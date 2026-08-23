# GUILD Project - Comprehensive Code Quality & Architecture Review

**Date:** August 19, 2026  
**Reviewer:** Senior Code Quality & Architecture Engineer  
**Scope:** Backend (`D:\Coding\GUILD\Backend\src\**`) + Frontend (`D:\Coding\GUILD\FrontEnd\src\**`)

---

## Executive Summary

| Metric | Score (1-10) | Status |
|--------|--------------|--------|
| **Architecture** | 7.5/10 | Good separation, some layering leaks |
| **Code Quality** | 7/10 | SOLID mostly followed, DRY violations exist |
| **Type Safety** | 3/10 | **CRITICAL** - No TypeScript, zero type coverage |
| **Testing** | 1/10 | **CRITICAL** - No tests whatsoever |
| **Performance** | 6.5/10 | Caching present, N+1 risks in leaderboards |
| **Maintainability** | 6/10 | Technical debt accumulating, duplicate logic |
| **Patterns** | 7/10 | Consistent within layers, cross-cutting concerns messy |
| **Error Handling** | 7.5/10 | Good centralized middleware, inconsistent frontend |

**Overall Score: 5.5/10** — *Functional but fragile. Critical gaps in type safety and testing make this unsuitable for production scaling without significant investment.*

---

## 1. ARCHITECTURE (7.5/10)

### ✅ Strengths
- **Clear layer separation**: Controllers → Services → Models (Backend)
- **Domain-driven boundaries**: Auth, Guild, Player, Media, FF, Admin domains
- **Middleware pipeline**: Auth, rate-limiting, bot prevention, error handling well-organized
- **Socket.io integration**: Real-time updates decoupled via service layer
- **FF API abstraction**: Dedicated client with caching, normalization, retries

### ⚠️ Issues

| Severity | File:Line | Issue | Recommendation |
|----------|-----------|-------|----------------|
| **HIGH** | `authController.js:804` | `submitUidRegion` is **800+ lines** — violates SRP, mixes FF API orchestration, mock fallback, profile building, User/PlayerProfile persistence, socket emits, asset resolution | Extract into: `FFProfileService`, `OnboardingService`, `ProfilePersistenceService`, `AssetResolutionService` |
| **HIGH** | `adminController.js:1-852` | **852-line god controller** — handles roster, actions, roles, transfers, leadership, ex-members, changelogs | Split into: `RosterController`, `MemberActionController`, `LeadershipController`, `AuditController` |
| **MEDIUM** | `ffController.js:144-438` | `getPlayerFull` = 295 lines with hardcoded season badge tables | Extract badge resolution to `RankBadgeResolver` service; move season tables to config |
| **MEDIUM** | `mediaController.js:1-390` | 390 lines mixing upload, moderation, reactions, comments | Split into `UploadController`, `ModerationController`, `InteractionController` |
| **LOW** | `authController.js:17-20` | `GAMES`, `ADMIN_ROLES` constants defined in controller | Move to `config/constants.js` or domain constants file |
| **LOW** | `guildController.js:8-9` | `GUILD_ADMIN_ROLES` duplicated in `adminController.js:13` | Single source of truth in `config/roles.js` |

### Architecture Diagram (Current)

```
┌─────────────────────────────────────────────────────────────┐
│                        Express App                           │
├─────────────────────────────────────────────────────────────┤
│  Middleware: helmet → cors → origin-check → json → cookie   │
├─────────────────────────────────────────────────────────────┤
│  Routes → Controllers → Models (Mongoose)                   │
│       ↘ Services (Socket, FF Client, ItemCatalog)           │
│       ↘ Middleware (Auth, RateLimit, Bot, Upload)           │
└─────────────────────────────────────────────────────────────┘
```

### Recommended Architecture

```
src/
├── config/           # Centralized configuration (constants, env validation)
├── domain/           # Domain-driven modules
│   ├── auth/         # AuthController, AuthService, AuthMiddleware
│   ├── guild/        # GuildController, GuildService, MembershipService
│   ├── player/       # PlayerController, PlayerService, ProfileService
│   ├── media/        # MediaController, UploadService, ModerationService
│   ├── ff/           # FFController, FFClient, ItemCatalog, RankResolver
│   ├── admin/        # AdminController, RoleService, ActionService, AuditService
│   └── notification/ # NotificationController, NotificationService
├── shared/
│   ├── middleware/   # Cross-cutting: errorHandler, rateLimiter, auth
│   ├── utils/        # Pure utilities: fileValidator, playerName, mediaUrl
│   ├── errors/       # Custom error classes (ApiError, ValidationError, etc.)
│   └── socket/       # SocketService, event types
└── infrastructure/   # DB connection, external clients
```

---

## 2. CODE QUALITY (7/10)

### ✅ Strengths
- Consistent async/await with `try/catch/next(error)` pattern
- Good JSDoc comments on complex functions (`ffClient`, `itemCatalog`)
- Meaningful variable names in business logic
- Proper use of `const`/`let`, no `var`
- Early returns for validation failures

### ❌ DRY Violations

| File | Lines | Duplicated Logic | Fix |
|------|-------|------------------|-----|
| `authController.js:260-320` + `ffController.js:258-319` | ~60 lines each | `pickBlock`, `cleanNickname`, `toIsoDate`, `normalizeGender`, `stripPrefix`, `normalizeRankshow`, `normalizeModeStats` | Extract to `services/ff/transformers.js` |
| `authController.js:582-626` + `playerController.js:39-76` | ~45 lines each | `mapSoloStats` / `aggregateBr` / `mapCs` | Extract to `services/player/statsMapper.js` |
| `EnterUidRegionPage.jsx` + `OnboardingPage.jsx` | ~200 lines | UID/Region form, REGIONS array, fetch logic, cross-check, avatar fallback | Extract to `OnboardingWizard` component + `useOnboarding` hook |
| `DesktopNavbar.jsx` + `MobileHeader.jsx` + `BottomNavbar.jsx` | ~80 lines each | `useUnreadCount` hook, notification bell, avatar rendering | Extract `useUnreadCount`, `NotificationBell`, `UserAvatar` components |

### Complexity Hotspots (Cyclomatic Complexity > 15)

| File | Function | Est. Complexity | Refactoring Target |
|------|----------|-----------------|-------------------|
| `authController.js` | `submitUidRegion` | ~45 | Split into 5+ functions |
| `adminController.js` | `votePendingAction` | ~25 | Extract consensus logic to service |
| `ffController.js` | `getPlayerFull` | ~30 | Split by data domain |
| `mediaController.js` | `uploadMedia` | ~20 | Extract notification logic |

### Naming Inconsistencies

| Pattern | Examples | Standard |
|---------|----------|----------|
| **CamelCase vs snake_case** | `gameUid` vs `guildUid` vs `clanId` | Pick one (recommend camelCase for JS) |
| **Abbreviations** | `bi`, `pi`, `cs`, `br` in `authController` | Use full names (`basicInfo`, `profileInfo`, `clashSquad`, `battleRoyale`) |
| **Controller naming** | `ffController` vs `authController` vs `guildController` | Consistent suffix: `Controller` |

---

## 3. TYPE SAFETY — CRITICAL (3/10)

### Current State
- **Backend**: Plain JavaScript (Node.js/Express) — **Zero type coverage**
- **Frontend**: React with JSX — **Zero TypeScript**, no PropTypes, no JSDoc types
- **API Contracts**: No OpenAPI/Swagger, no schema validation

### Impact
| Risk | Likelihood | Severity |
|------|------------|----------|
| Runtime `undefined` property access | Very High | High |
| API contract drift (frontend/backend) | High | High |
| Refactoring fear / regression risk | Very High | Medium |
| Onboarding new developers | High | Medium |

### Immediate Actions Required

```bash
# 1. Add TypeScript to backend
cd Backend && npm init -y
npm install -D typescript @types/node @types/express @types/mongoose @types/jsonwebtoken @types/bcrypt @types/cookie-parser @types/cors @types/multer @types/socket.io
npx tsc --init --target ES2022 --module NodeNext --moduleResolution NodeNext --strict --esModuleInterop --outDir dist --rootDir src

# 2. Add TypeScript to frontend
cd FrontEnd && npm install -D typescript @types/react @types/react-dom @types/react-router-dom
# Update vite.config.ts for TS support
```

### Type Definition Priorities

| Priority | Target | Example |
|----------|--------|---------|
| **P0** | API request/response shapes | `AuthLoginRequest`, `GuildCreateResponse`, `PlayerProfileDTO` |
| **P0** | Mongoose document interfaces | `IUser`, `IGuild`, `IMembership`, `IPlayerProfile` |
| **P1** | Service method signatures | `FFClient.getPlayerProfile(server: string, uid: string): Promise<FFProfileResponse>` |
| **P1** | React component props | `interface ProfilePageProps {}`, `interface AvatarUploadZoneProps {}` |
| **P2** | Utility function types | `resolveMediaUrl(url: string \| null): string` |

### Example: Mongoose Model with TypeScript

```typescript
// Backend/src/models/User.ts
import mongoose, { Document, Schema } from 'mongoose';
import bcrypt from 'bcrypt';

export interface IUser extends Document {
  googleId: string | null;
  email: string;
  name: string;
  avatar: string;
  passwordHash: string | null;
  sessionVersion: number;
  lastLoginAt: Date;
  game: 'PUBG' | 'Free Fire' | 'Mobile Legends' | null;
  gameUid: string | null;
  inGameName: string | null;
  region: RegionCode | null;
  onboardingCompleted: boolean;
  profileCompleted: boolean;
  matchPassword(enteredPassword: string): Promise<boolean>;
}

const userSchema = new Schema<IUser>({
  googleId: { type: String, default: null, index: true },
  email: { type: String, required: true, unique: true, lowercase: true, trim: true },
  // ...
}, { timestamps: true });

userSchema.methods.matchPassword = async function (this: IUser, enteredPassword: string): Promise<boolean> {
  if (!this.passwordHash) return false;
  return bcrypt.compare(enteredPassword, this.passwordHash);
};

export const User = mongoose.model<IUser>('User', userSchema);
```

---

## 4. TESTING — CRITICAL (1/10)

### Current State
- **Backend**: **0 test files**, **0% coverage**
- **Frontend**: **0 test files**, **0% coverage**
- **E2E**: No Cypress/Playwright tests
- **Integration**: No test database setup

### Risk Assessment
| Component | Risk | Consequence |
|-----------|------|-------------|
| `authController.js` (1300+ lines) | Critical | Auth bypass, session hijack, onboarding corruption |
| `adminController.js` (850+ lines) | Critical | Role escalation, guild takeover, data deletion |
| `ffClient.js` (200 lines) | High | Silent data corruption, mock fallback bugs |
| `mediaController.js` (390 lines) | High | Upload bypass, XSS via files, approval flow bugs |
| Socket.io handlers | Medium | Real-time desync, memory leaks |

### Testing Strategy (Priority Order)

```bash
# 1. Unit tests (Vitest/Jest)
Backend/
├── tests/
│   ├── unit/
│   │   ├── services/
│   │   │   ├── ffClient.test.ts          # Mock fetch, test cache/TTL/retry
│   │   │   ├── itemCatalog.test.ts       # Test regex parsing, disk cache
│   │   │   └── statsMapper.test.ts       # Test BR/CS aggregation logic
│   │   ├── utils/
│   │   │   └── fileValidator.test.ts     # Test magic byte detection
│   │   └── middleware/
│   │       ├── authMiddleware.test.ts    # Test JWT verify, sessionVersion
│   │       └── botPrevention.test.ts     # Test honeypot, fingerprint
│   └── integration/
│       ├── authController.test.ts        # Supertest + test DB
│       ├── guildController.test.ts
│       └── adminController.test.ts

FrontEnd/
├── tests/
│   ├── unit/
│   │   ├── hooks/
│   │   │   ├── usePlayerProfile.test.tsx
│   │   │   └── useAuth.test.tsx
│   │   ├── utils/
│   │   │   └── playerName.test.ts
│   │   └── components/
│   │       └── AvatarUploadZone.test.tsx
│   └── integration/
│       ├── OnboardingWizard.test.tsx     # MSW for API mocking
│       └── ProfilePage.test.tsx

# 2. E2E tests (Playwright)
e2e/
├── auth.spec.ts           # Google login → onboarding → dashboard
├── guild-management.spec.ts # Create guild → invite → promote → transfer
├── media.spec.ts          # Upload → approve → react → comment
└── leaderboards.spec.ts   # Stats refresh → ranking updates
```

### Minimum Viable Test Coverage Targets
| Layer | Target | Rationale |
|-------|--------|-----------|
| Business logic (services, utils) | **90%+** | Pure functions, easy to test, high impact |
| Controllers | **70%+** | Integration tests with test DB |
| Middleware | **80%+** | Security-critical |
| Frontend hooks/components | **60%+** | React Testing Library |
| E2E critical paths | **5 scenarios** | Auth, onboarding, guild CRUD, media, admin |

---

## 5. PERFORMANCE (6.5/10)

### ✅ Strengths
- **FF API Client**: In-memory TTL cache (profile 60s, stats 60s, guild 5min), in-flight dedupe, 8s timeout + 1 retry
- **Item Catalog**: Disk cache (survives restarts), regex scan avoids full JSON parse (12.6MB)
- **Database**: Connection pooling (maxPoolSize: 20), proper indexes on query fields
- **Frontend**: Route-level code splitting (`React.lazy`), skeleton loaders, `useCallback`/`useMemo` where needed
- **Static assets**: 24h cache headers for uploads, `trust proxy` for correct IP behind load balancer

### ⚠️ Issues

| Severity | Location | Issue | Impact | Fix |
|----------|----------|-------|--------|-----|
| **HIGH** | `leaderboardController.js:101-103` | `PlayerProfile.find()` loads **ALL profiles** into memory for scoring | O(N) memory, blocks event loop, fails at ~10k profiles | Add `leaderboardScore` materialized field + scheduled aggregation job; query with `.sort({leaderboardScore: -1}).limit(100)` |
| **HIGH** | `playerController.js:223` | `refreshLiveProfile` called on **every** `/players/me` request | 4 parallel FF API calls per profile view; 8s timeout each | Cache live rank for 30s per user; background refresh via cron |
| **MEDIUM** | `mediaController.js:47-51` | `getGallery` populates `comments.userId` without limit | N+1 if media has many comments; unbounded array | Add `commentsLimit` query param; paginate comments separately |
| **MEDIUM** | `adminController.js:30-32` | `getRoster` populates `userId` for all members | Unnecessary data transfer for large guilds | Add `select` projection; paginate |
| **MEDIUM** | `FrontEnd/hooks/usePlayerStatsSocket.js` | New socket connection per `playerId` | Multiple connections if user views multiple profiles | Singleton socket per session; multiplex subscriptions |
| **LOW** | `FrontEnd/services/api/client.js:54` | `CLIENT_FINGERPRINT` generated on **every module load** | Canvas fingerprinting on every page visit | Generate once per session; store in `sessionStorage` |
| **LOW** | `authController.js:761` | `resolveProfileAssets` called on every onboarding completion | Network call to item catalog (if cache miss) | Already cached by `itemCatalog`; verify warm-up works |

### Database Index Audit

| Collection | Current Indexes | Missing Indexes |
|------------|-----------------|-----------------|
| `users` | `googleId`, `email`, compound `(game, gameUid)` partial | `(onboardingCompleted, game)` for free player queries |
| `guilds` | `disbandedAt+score`, `leaderId`, `transferToken` sparse | `(visibility, disbandedAt)` for public search |
| `memberships` | `(userId, guildUid)`, `(guildUid, status)`, `(guildUid, status, role)` | `(userId, status)` for `getMyProfile` sync |
| `playerprofiles` | `playerRank`, `stats.brRank.rankPoints`, `stats.csRank.rankPoints` | `(guildUid, role)` for guild leaderboards |
| `media` | `(guildUid, approvalStatus, visibility)`, `(uploaderId, createdAt)`, `(guildUid, approvalStatus, createdAt)` | `(category, approvalStatus)` for global feed |

---

## 6. MAINTAINABILITY (6/10)

### Technical Debt Inventory

| Debt Item | Location | Effort | Risk |
|-----------|----------|--------|------|
| **Mock FF data fallback** | `authController.js:483-553` | Medium | Mock data persists to PlayerProfile; hard to distinguish real vs mock |
| **Hardcoded season badge tables** | `ffController.js:250-295` | Low | FF API changes break badge rendering; no tests |
| **Duplicate onboarding pages** | `EnterUidRegionPage.jsx` + `OnboardingPage.jsx` | Medium | Bug fixes applied to one but not the other |
| **No API versioning** | `Server.js:109-118` | Low | Breaking changes require coordinated deploy |
| **No request validation library** | Controllers use manual `if (!x) return 400` | Medium | Inconsistent validation, missed edge cases |
| **In-memory bot prevention** | `botPrevention.js:4` | High | **Does not work in clustered/production** (Map not shared) |
| **No structured logging** | `console.log/warn/error` throughout | Low | Hard to correlate requests, no log aggregation |
| **No health check dependencies** | `/api/health` returns static ok | Low | Doesn't verify DB, FF API, Socket connectivity |
| **Magic numbers** | `MEMBER_CAP=55`, `OFFICER_MAX=4`, `TOKEN_TTL=60min` | Low | Scattered in controllers; change requires grep |

### Coupling Analysis

```
High Coupling (Refactor):
├── authController ↔ FF Client ↔ ItemCatalog (tight, circular via require)
├── authController ↔ PlayerProfile model (direct save in controller)
├── adminController ↔ 8 models (god controller)
└── FrontEnd: OnboardingPage ↔ authApi ↔ ffApi (3 API layers for same data)

Low Coupling (Good):
├── Middleware pipeline (independent, composable)
├── Socket service (decoupled via events)
└── Utility functions (pure, no side effects)
```

### Documentation Gaps
| Missing | Where Needed |
|---------|--------------|
| API specification (OpenAPI) | All routes |
| Architecture decision records (ADRs) | Root `/docs/adr/` |
| Database schema documentation | `/docs/schema.md` |
| Deployment/runbook | `/docs/operations.md` |
| Contribution guide | `CONTRIBUTING.md` |

---

## 7. PATTERNS (7/10)

### ✅ Good Patterns Used
- **Middleware pipeline** for cross-cutting concerns (auth, rate-limit, bot, error)
- **Service layer** for external APIs (FF Client, Item Catalog, Socket)
- **Repository-ish pattern** via Mongoose models (though controllers call models directly)
- **Event-driven updates** via Socket.io (`emitPlayerStatsUpdate`, `emitPlayerProfileUpdate`)
- **Optimistic UI** with toast promises (`toast.promise()`)
- **Skeleton screens** for perceived performance
- **Error boundaries** in React (`App.jsx:59-96`)

### ❌ Anti-Patterns

| Anti-Pattern | Location | Refactor |
|--------------|----------|----------|
| **God Controller** | `authController.js`, `adminController.js`, `ffController.js` | Extract domain services |
| **Controller doing persistence** | `authController.js:743` `await req.user.save()` | Move to service |
| **Circular require()** | `authController.js:11` requires `socket.js`, `socket.js:4` requires `User` model | Dependency injection or event bus |
| **Magic strings for events** | `socket.js:66` `'subscribe:player-stats'` | Define in `shared/events.ts` |
| **Inline regex in hot path** | `ffController.js:298` `replace(/^UI_BP_Emoji_/, '')` | Pre-compile regex constants |
| **Mutating request body** | `client.js:92` `addBotProtectionFields(body)` | Return new object (already does) |
| **Boolean trap** | `mediaController.js:86` `private: isPrivate === true \| visibility === 'private'` | Explicit enum `'public' \| 'private'` |
| **Duplicate constants** | `GUILD_ADMIN_ROLES` in 2 controllers | Shared config |

### Design Pattern Opportunities

| Pattern | Where to Apply | Benefit |
|---------|----------------|---------|
| **Strategy** | FF API response normalization (`ffController.js:260-320`) | Swap normalizers per FF API version |
| **Factory** | `Media` creation (avatar vs guild vs personal) | Encapsulate approval logic |
| **State Machine** | `Membership.status` transitions | Prevent invalid `pending → removed` |
| **Decorator** | Rate limiters (auth vs write vs FF) | Compose limits per route |
| **Observer** | `ChangeLog` creation | Decouple audit from business logic |
| **Command** | `PendingAction` (kick, approve, reject) | Undo/redo, audit trail, queue |

---

## 8. ERROR HANDLING (7.5/10)

### ✅ Strengths
- **Centralized error middleware** (`errorMiddleware.js`) handles:
  - MongoDB duplicate key (11000) → 409
  - Multer file size → 413
  - JSON parse failure → 400
  - Mongoose validation → 400 with first error message
  - CastError (bad ObjectId) → 400
  - Custom `ApiLikeError` from FF client → passes upstream status/code
  - Unknown errors → 500 with generic message (no stack in prod)
- **Async wrapper pattern**: All controllers use `try/catch/next(error)`
- **Frontend**: `ApiError` class with status, fieldErrors; `defaultMessageForStatus` for UX

### ⚠️ Issues

| Severity | Location | Issue |
|----------|----------|-------|
| **MEDIUM** | `errorMiddleware.js:58-66` | `isKnownError` logic fragile: `err.expose` set only in some branches; `ValidationError` name checked again |
| **MEDIUM** | `authController.js:1294-1295` | `deleteAccount` uses `req.user.password` but schema has `passwordHash` — **will always fail** |
| **LOW** | `mediaController.js:315-318` | `toggleReaction` returns `reacted: index < 0` but doesn't distinguish add vs remove for UI |
| **LOW** | `FrontEnd/services/api/client.js:112-120` | Non-JSON response silently ignored; could be HTML error page from proxy |
| **LOW** | `socket.js:52-54` | Socket auth errors just `next(new Error('Invalid token'))` — no specific codes for UI |

### Error Handling Improvements

```javascript
// 1. Standardize error response shape (backend)
{
  "error": {
    "code": "VALIDATION_FAILED",
    "message": "UID must be numeric.",
    "field": "uid",
    "details": {}
  }
}

// 2. Frontend ApiError enhancement
export class ApiError extends Error {
  constructor(message, status, code, fieldErrors, rawResponse) {
    super(message);
    this.name = "ApiError";
    this.status = status;
    this.code = code;           // e.g., "FF_RATE_LIMITED", "DUPLICATE_GUILD_UID"
    this.fieldErrors = fieldErrors; // { field: "message" }
    this.rawResponse = rawResponse; // for debugging
  }
}

// 3. Structured logging (backend)
const logger = {
  info: (msg, meta) => console.log(JSON.stringify({ level: 'info', msg, ...meta, timestamp: new Date().toISOString() })),
  warn: (msg, meta) => console.warn(JSON.stringify({ level: 'warn', msg, ...meta, timestamp: new Date().toISOString() })),
  error: (msg, meta) => console.error(JSON.stringify({ level: 'error', msg, ...meta, timestamp: new Date().toISOString() })),
};

// 4. Correlation IDs for request tracing
app.use((req, res, next) => {
  req.correlationId = req.headers['x-correlation-id'] || crypto.randomUUID();
  res.set('X-Correlation-ID', req.correlationId);
  next();
});
```

---

## 9. SECURITY REVIEW

### ✅ Good Practices
- Helmet.js with CORP disabled only for uploads (intentional)
- CORS with explicit allowed origins + middleware hard-deny
- JWT with `HS256` algorithm lock, `sessionVersion` for invalidation
- HttpOnly cookies with `SameSite=None; Secure` (production) / `Lax` (WebView)
- Rate limiting on auth (30/15min), writes (80/15min), FF proxy (120/15min)
- File upload validation via magic bytes (not MIME type)
- Bot prevention: honeypot, fingerprinting, behavioral analysis, hCaptcha ready
- bcrypt for password hashing (cost 10)
- Leader password separate from Google OAuth

### ⚠️ Security Gaps

| Severity | Issue | Location | Fix |
|----------|-------|----------|-----|
| **HIGH** | **In-memory bot prevention store** — `Map` not shared across workers/processes | `botPrevention.js:4` | Use Redis (ioredis) with TTL |
| **HIGH** | **No CSP header** — Helmet defaults may be too permissive | `Server.js:44-53` | Configure `contentSecurityPolicy` with nonces for inline scripts |
| **MEDIUM** | **JWT secret validation only at startup** — no rotation support | `Server.js:20-23` | Support `JWT_SECRET_OLD` for rotation; key ID in token |
| **MEDIUM** | **No password strength policy** — min 6 chars only | `authController.js:1113, 1251` | Enforce 12+ chars, entropy check (zxcvbn) |
| **MEDIUM** | **File upload path traversal risk** — `crypto.randomBytes` filename safe but `UPLOAD_DIR` from env | `uploadMiddleware.js:75` | Validate `UPLOAD_DIR` is absolute, outside web root |
| **LOW** | **Cookie domain hardcoded to `.vercel.app`** | `authController.js:53` | Make configurable via `COOKIE_DOMAIN` env |
| **LOW** | **No security headers for HSTS, X-Frame-Options** | `Server.js` | Helmet defaults OK but verify `hsts: { maxAge: 31536000 }` |
| **LOW** | **Socket.io no per-message rate limit** | `socket.js` | Add token bucket per socket for `subscribe:player-stats` |

---

## 10. PRIORITIZED ACTION PLAN

### 🔴 CRITICAL (Do First — Blocks Production)

| # | Task | Effort | Owner |
|---|------|--------|-------|
| 1 | **Add TypeScript to both codebases** | 3-5 days | Team |
| 2 | **Write unit tests for business logic** (services, utils, mappers) | 5-7 days | Backend |
| 3 | **Fix `deleteAccount` password bug** | 30 min | Backend |
| 4 | **Replace in-memory bot store with Redis** | 1-2 days | Backend |
| 5 | **Add integration test harness** (test DB, supertest, MSW) | 2-3 days | Team |

### 🟠 HIGH (Next Sprint)

| # | Task | Effort | Owner |
|---|------|--------|-------|
| 6 | **Refactor `authController.submitUidRegion`** into services | 3-4 days | Backend |
| 7 | **Refactor `adminController`** into 4 controllers | 3-4 days | Backend |
| 8 | **Add materialized `leaderboardScore` + cron job** | 2 days | Backend |
| 9 | **Unify onboarding pages** (`EnterUidRegion` + `Onboarding`) | 2-3 days | Frontend |
| 10 | **Extract shared FF transformers** (`pickBlock`, `normalizeModeStats`, etc.) | 1 day | Backend |
| 11 | **Add OpenAPI spec generation** (swagger-jsdoc) | 1-2 days | Backend |
| 12 | **Add structured logging + correlation IDs** | 1 day | Backend |

### 🟡 MEDIUM (Technical Debt)

| # | Task | Effort | Owner |
|---|------|--------|-------|
| 13 | **Extract `RankBadgeResolver` service** from `ffController` | 1 day | Backend |
| 14 | **Add request validation library** (zod/joi) | 1 day | Backend |
| 15 | **Singleton Socket.io connection** on frontend | 1 day | Frontend |
| 16 | **Add health check dependencies** (DB, FF API, Redis) | 4 hours | Backend |
| 17 | **Move magic numbers to config** | 2 hours | Backend |
| 18 | **Add CSP headers with nonces** | 4 hours | Backend |
| 19 | **Pagination for comments, roster, media** | 2 days | Backend |
| 20 | **Database index audit + missing indexes** | 4 hours | Backend |

### 🟢 LOW (Polish)

| # | Task | Effort | Owner |
|---|------|--------|-------|
| 21 | **ADR documentation** for key decisions | Ongoing | Team |
| 22 | **Contribution guide + code style** (ESLint, Prettier) | 1 day | Team |
| 23 | **Storybook for UI components** | 2 days | Frontend |
| 24 | **E2E test suite** (Playwright) | 3-5 days | Team |
| 25 | **Bundle analysis + optimization** | 2 days | Frontend |

---

## 11. FILE-BY-FILE QUICK REFERENCE

### Backend — Must Refactor

| File | Lines | Primary Issue |
|------|-------|---------------|
| `authController.js` | 1309 | God controller, 800-line function, mixed concerns |
| `adminController.js` | 852 | God controller, 8+ responsibilities |
| `ffController.js` | 449 | `getPlayerFull` 295 lines, hardcoded season tables |
| `mediaController.js` | 390 | Mixed upload/moderation/interaction |
| `botPrevention.js` | 268 | In-memory store (production unsafe) |

### Backend — Good Patterns to Preserve

| File | Why |
|------|-----|
| `errorMiddleware.js` | Comprehensive error normalization |
| `ff/client.js` | Caching, dedupe, retry, typed errors |
| `services/ff/itemCatalog.js` | Disk cache, regex scan, warm-up |
| `utils/fileValidator.js` | Pure magic-byte detection |
| `middleware/authMiddleware.js` | Clean JWT + sessionVersion + optional auth |

### Frontend — Must Refactor

| File | Lines | Primary Issue |
|------|-------|---------------|
| `ProfilePage.jsx` | 782 | Massive component, mixed concerns |
| `OnboardingPage.jsx` | 431 | Duplicate of `EnterUidRegionPage` |
| `EnterUidRegionPage.jsx` | 524 | Duplicate of `OnboardingPage` |
| `DesktopNavbar.jsx` | 215 | Inline `useUnreadCount`, duplicated in Mobile/Bottom |

### Frontend — Good Patterns to Preserve

| File | Why |
|------|-----|
| `services/api/client.js` | `ApiError`, bot protection fields, timeout handling |
| `hooks/usePlayerProfile.js` | Clean cancellation, reload key pattern |
| `hooks/usePlayerStatsSocket.js` | Sanitization guard against stale socket data |
| `components/toast/ToastProvider.jsx` | Promise-based toast API |
| `components/ui/Skeleton.jsx` | Comprehensive skeleton variants |

---

## 12. METRICS BASELINE (Post-Refactor Targets)

| Metric | Current | Target (3 months) |
|--------|---------|-------------------|
| TypeScript coverage | 0% | 95%+ |
| Unit test coverage (backend) | 0% | 80%+ |
| Unit test coverage (frontend) | 0% | 60%+ |
| Integration test coverage | 0% | 70%+ |
| E2E critical paths | 0 | 5 |
| Cyclomatic complexity (max) | ~45 | <15 |
| God controllers (>300 lines) | 4 | 0 |
| Duplicate code blocks (>30 lines) | 6 | 0 |
| In-memory state in production | 1 (bot store) | 0 |
| API response time (p95) | Unknown | <200ms |
| Bundle size (gzipped) | Unknown | <200KB |

---

## Appendix: Recommended Tooling

```json
// Backend package.json additions
{
  "devDependencies": {
    "typescript": "^5.3",
    "@types/node": "^20.10",
    "@types/express": "^4.17",
    "@types/mongoose": "^5.11",
    "@types/jsonwebtoken": "^9.0",
    "@types/bcrypt": "^5.0",
    "@types/cookie-parser": "^1.4",
    "@types/cors": "^2.8",
    "@types/multer": "^1.4",
    "@types/socket.io": "^3.0",
    "vitest": "^1.0",
    "supertest": "^6.3",
    "mongodb-memory-server": "^9.1",
    "eslint": "^8.55",
    "@typescript-eslint/eslint-plugin": "^6.15",
    "swagger-jsdoc": "^6.2",
    "swagger-ui-express": "^5.0",
    "zod": "^3.22",
    "ioredis": "^5.3",
    "pino": "^8.17",
    "pino-pretty": "^10.3"
  }
}
```

```json
// Frontend package.json additions
{
  "devDependencies": {
    "typescript": "^5.3",
    "@types/react": "^18.2",
    "@types/react-dom": "^18.2",
    "@types/react-router-dom": "^5.3",
    "vitest": "^1.0",
    "@testing-library/react": "^14.1",
    "@testing-library/jest-dom": "^6.1",
    "msw": "^2.0",
    "playwright": "^1.40",
    "eslint": "^8.55",
    "@typescript-eslint/eslint-plugin": "^6.15",
    "vite-plugin-checker": "^0.6"
  }
}
```

---

**Review Complete.** This codebase demonstrates solid domain knowledge and functional features but requires significant investment in type safety, testing, and architectural refactoring before it can be considered production-ready for scale. The highest-impact changes are **TypeScript adoption** and **test infrastructure** — these enable all subsequent refactoring with confidence.