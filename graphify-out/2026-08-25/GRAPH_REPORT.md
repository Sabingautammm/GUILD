# Graph Report - GUILD  (2026-08-25)

## Corpus Check
- 154 files · ~326,926 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 1255 nodes · 2157 edges · 153 communities (140 shown, 13 thin omitted)
- Extraction: 94% EXTRACTED · 6% INFERRED · 0% AMBIGUOUS · INFERRED: 135 edges (avg confidence: 0.5)
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `04c1522d`
- Run `git rev-parse HEAD` and compare to check if the graph is stale.
- Run `graphify update .` after code changes (no API cost).

## Community Hubs (Navigation)
- apiFetch
- dependencies
- adminRoutes.js
- App.jsx
- dependencies
- socket.js
- InGame.py
- guildController.js
- api/client.js
- ff-account.js
- ff-ingame.js
- resolveMediaUrl
- Backend/package.json
- mediaRoutes.js
- server.js
- authController.js
- 🟡 MEDIUM IMPACT ISSUES
- LeadershipController.js
- ProfilePage.jsx
- leaderboardController.js
- ff-utils.js
- SeasonStatus.jsx
- playerController.js
- authRoutes.js
- test_ui_cdp.js
- 🟠 HIGH IMPACT ISSUES
- memberController.js
- rankTiers.js
- ToastProvider.jsx
- botPrevention.js
- Backend Refactoring Orchestration Plan
- plugins
- GUILD Project — Comprehensive Performance Audit Report
- FFProfileService.js
- completeOnboarding
- 🟢 LOW IMPACT / NICE-TO-HAVE
- useToast
- index.js
- Server.js
- ff/client.js
- cors
- build.sh
- vercel.json
- MemberActionController.js
- Design System Master File
- dependencies
- FreeFire-Api
- 🔧 SPECIFIC CODE FIXES
- LeaderboardPage.jsx
- GUILD Project - Comprehensive Code Quality & Architecture Review
- FFLiveData.jsx
- 3. TYPE SAFETY — CRITICAL (3/10)
- versionController.js
- 🔴 CRITICAL ISSUES (Must Fix Immediately)
- adminController.js
- scripts
- devDependencies
- repository
- 10. PRIORITIZED ACTION PLAN
- 11. FILE-BY-FILE QUICK REFERENCE
- useAuth
- 1. ARCHITECTURE (7.5/10)
- 2. CODE QUALITY (7/10)
- 4. TESTING — CRITICAL (1/10)
- FrontEnd/README.md
- finalizeGoogleLogin
- 5. PERFORMANCE (6.5/10)
- ffTransformers.js
- ErrorBoundary
- 6. MAINTAINABILITY (6/10)
- 7. PATTERNS (7/10)
- 8. ERROR HANDLING (7.5/10)
- GuildPlayer.js
- cookie-parser
- express
- google-auth-library
- ioredis
- protobufjs
- AssetResolutionService.js
- adminApi.js
- express-rate-limit

## God Nodes (most connected - your core abstractions)
1. `apiFetch()` - 86 edges
2. `useAuth()` - 40 edges
3. `react` - 33 edges
4. `useToast()` - 32 edges
5. `resolveMediaUrl()` - 25 edges
6. `playerName()` - 22 edges
7. `🟡 MEDIUM IMPACT ISSUES` - 19 edges
8. `ApiError` - 18 edges
9. `🟠 HIGH IMPACT ISSUES` - 16 edges
10. `GUILD Project - Comprehensive Code Quality & Architecture Review` - 15 edges

## Surprising Connections (you probably didn't know these)
- `PassGrid()` --calls--> `resolveMediaUrl()`  [EXTRACTED]
  FrontEnd/src/features/dashboard/components/FFLiveData.jsx → FrontEnd/src/utils/mediaUrl.js
- `RoleChip()` --calls--> `playerName()`  [EXTRACTED]
  FrontEnd/src/pages/GuildPage.jsx → FrontEnd/src/utils/playerName.js
- `MediaPreviewCard()` --calls--> `resolveMediaUrl()`  [EXTRACTED]
  FrontEnd/src/pages/HomePage.jsx → FrontEnd/src/utils/mediaUrl.js
- `AvatarWithFallback()` --calls--> `resolveMediaUrl()`  [EXTRACTED]
  FrontEnd/src/pages/LeaderboardPage.jsx → FrontEnd/src/utils/mediaUrl.js
- `removeGuildPlayer()` --calls--> `apiFetch()`  [EXTRACTED]
  FrontEnd/src/services/api/adminApi.js → FrontEnd/src/services/api/client.js

## Import Cycles
- None detected.

## Communities (153 total, 13 thin omitted)

### Community 0 - "apiFetch"
Cohesion: 0.06
Nodes (56): EnterUidRegionPage, GuildPage, OnboardingPage, SkeletonGuild(), AuthProvider(), changePassword(), checkGuildUid(), completeOnboarding() (+48 more)

### Community 1 - "dependencies"
Cohesion: 0.09
Nodes (21): dependencies, cors, dotenv, express, nodemon, protobufjs, protobufjs-cli, description (+13 more)

### Community 2 - "adminRoutes.js"
Cohesion: 0.13
Nodes (19): addPlayerByGameUid(), ADMIN_ROLES, getExMembers(), getGuildPlayers(), getRoster(), GuildPlayer, hardDeleteExMember(), Membership (+11 more)

### Community 3 - "App.jsx"
Cohesion: 0.10
Nodes (14): AdminPage, App(), GalleryPage, MemberDetailsPage, MembersPage, ReelPage, ProtectedRoutes(), FullPageSkeleton() (+6 more)

### Community 4 - "dependencies"
Cohesion: 0.06
Nodes (34): framer-motion, dependencies, framer-motion, react, react-dom, react-icons, react-router-dom, socket.io-client (+26 more)

### Community 5 - "socket.js"
Cohesion: 0.17
Nodes (9): bcrypt, mongoose, userSchema, cookie, initializeSocket(), jwt, { Server }, User (+1 more)

### Community 6 - "InGame.py"
Cohesion: 0.25
Nodes (6): get_player_personal_show(), get_player_stats(), Perform a fuzzy account search by keyword. Args: server_url (str): Base URL of…, Get player statistics for BR or CS mode Args: mode (str): "br" or "cs" uid…, Get player personal show data Args: authorization (str): Bearer token for…, search_account_by_keyword()

### Community 7 - "guildController.js"
Cohesion: 0.13
Nodes (20): applyToGuild(), ChangeLog, disbandGuild(), getGuildProfile(), getPrivateGuildView(), Guild, GUILD_ADMIN_ROLES, GuildPlayer (+12 more)

### Community 8 - "api/client.js"
Cohesion: 0.15
Nodes (21): MediaCard(), SkeletonMediaGrid(), MediaTab(), GalleryPage(), IMAGE_EXTENSIONS, IMAGE_MIMES, validateMediaFile(), VIDEO_EXTENSIONS (+13 more)

### Community 9 - "ff-account.js"
Cohesion: 0.10
Nodes (21): { encodeProto, decodeProto, postExpectContinue, postForm, safeJson }, {
  GARENA_TOKEN_URL,
  MAJOR_LOGIN_URL,
  CLIENT_SECRET,
  CLIENT_ID,
  RELEASEVERSION,
  DEBUG,
}, getGarenaToken(), { MajorLogin }, searchAccountByKeyword(), { ACCOUNTS }, { getGarenaToken, getMajorLogin }, { getPlayerPersonalShow, getPlayerStats, searchAccountByKeyword } (+13 more)

### Community 10 - "ff-ingame.js"
Cohesion: 0.13
Nodes (28): addRates(), authHeaders(), cacheGet(), cacheSet(), CLAN_ACTIVITY_TYPE, { encodeProto, decodeProto, postExpectContinue }, enrichPlayers(), getClanMainPageInfo() (+20 more)

### Community 11 - "resolveMediaUrl"
Cohesion: 0.22
Nodes (14): BottomNavbar(), navItems, DesktopNavbar(), navItems, useUnreadCount(), MobileHeader(), Navbar(), Avatar() (+6 more)

### Community 12 - "Backend/package.json"
Cohesion: 0.15
Nodes (12): author, bugs, url, description, engines, node, homepage, license (+4 more)

### Community 13 - "mediaRoutes.js"
Cohesion: 0.06
Nodes (45): LIMITS, MIME_TYPES, path, addComment(), getGallery(), getLimit(), getMyMedia(), getPendingForAdmin() (+37 more)

### Community 14 - "server.js"
Cohesion: 0.09
Nodes (20): { ACCOUNTS, RATE_LIMIT_MAX, RATE_LIMIT_WINDOW_MS }, API_KEYS, { ApiError }, app, authenticate(), cors, CORS_ORIGINS, crypto (+12 more)

### Community 15 - "authController.js"
Cohesion: 0.08
Nodes (29): ADMIN_ROLES, bcrypt, buildProfileDataFromFF(), ChangeLog, cleanNickname(), crypto, DUMMY_BCRYPT_HASH, { emitPlayerStatsUpdate, emitPlayerProfileUpdate } (+21 more)

### Community 16 - "🟡 MEDIUM IMPACT ISSUES"
Cohesion: 0.11
Nodes (19): BACKEND-009: Pagination Missing on `/api/guild/:guildUid` (Roster), BACKEND-010: `searchGuilds` Uses `$regex` Without Text Index, BACKEND-011: Socket.io No Redis Adapter (Single Instance Only), BACKEND-012: No Database Query Logging / Slow Query Detection, BACKEND-013: `optionalAuth` Middleware Runs 2 DB Queries for Guests, BACKEND-014: `getMemberById` Has Complex Fallback Logic (Multiple Queries), DB-003: `PlayerProfile.stats` Embedded Document Grows Unbounded, DB-004: No TTL Index on `Notification` (Unbounded Growth) (+11 more)

### Community 17 - "LeadershipController.js"
Cohesion: 0.14
Nodes (14): bcrypt, ChangeLog, claimLeadership(), completeTransfer(), crypto, { emitPlayerProfileUpdate }, Guild, initiateTransfer() (+6 more)

### Community 18 - "ProfilePage.jsx"
Cohesion: 0.16
Nodes (10): ProfilePage, PasswordInput(), usePlayerProfile(), getMyProfile(), AVATAR_EXTENSIONS, AVATAR_MIMES, ProfilePage(), STAT_MODES (+2 more)

### Community 19 - "leaderboardController.js"
Cohesion: 0.18
Nodes (17): clampPercent(), computeTotals(), getGuildLeaderboard(), getLimit(), getOffset(), getPlayerLeaderboard(), Guild, Membership (+9 more)

### Community 20 - "ff-utils.js"
Cohesion: 0.15
Nodes (15): getMajorLogin(), searchClanByName(), main(), aesCbcDecrypt(), aesCbcEncrypt(), ApiError, crypto, decodeProto() (+7 more)

### Community 22 - "playerController.js"
Cohesion: 0.08
Nodes (35): getNotifications(), getUnreadCount(), markRead(), Notification, aggregateBr(), cleanNickname(), { emitPlayerStatsUpdate, emitPlayerProfileUpdate }, ensureStats() (+27 more)

### Community 23 - "authRoutes.js"
Cohesion: 0.11
Nodes (19): changePassword(), checkGuildUid(), clearAuthCookies(), deleteAccount(), logout(), verifyLeaderPassword(), authLimiter, ffLimiter (+11 more)

### Community 24 - "test_ui_cdp.js"
Cohesion: 0.20
Nodes (13): edge, EDGE_CANDIDATES, edgeProc, evaluate(), { execFileSync, spawn }, fs, getJson(), main() (+5 more)

### Community 25 - "🟠 HIGH IMPACT ISSUES"
Cohesion: 0.12
Nodes (16): BACKEND-004: `refreshLiveProfile` Makes 4 Sequential FF API Calls (No Parallel Batch), BACKEND-005: `getPlayerFull` (FF Proxy) Makes 6+ Upstream Calls Serially in Parts, BACKEND-006: Auth Middleware Runs `Membership.findOne` on EVERY Protected Request, BACKEND-007: No Request/Response Compression (gzip/brotli), BACKEND-008: Rate Limiter Uses In-Memory Store (Not Distributed), CACHE-001: FF Item Catalog Loads 12.6 MB JSON at Boot (Blocks Startup), CACHE-002: No Redis/Valkey for Distributed Caching, FRONTEND-001: Main Bundle **472 KB** (gzipped ~140 KB) — Exceeds 170 KB Budget (+8 more)

### Community 26 - "memberController.js"
Cohesion: 0.18
Nodes (10): DEFAULT_MEMBERS, getMemberById(), getMembers(), GuildMember, mongoose, guildMemberSchema, mongoose, express (+2 more)

### Community 27 - "rankTiers.js"
Cohesion: 0.19
Nodes (12): getPlayerPersonalShow(), getPlayerRank(), splitPasses(), BR_BY_ID, BR_TIERS, CS_BY_ID, CS_STAR_TIERS, CS_TIERS (+4 more)

### Community 28 - "ToastProvider.jsx"
Cohesion: 0.26
Nodes (8): isMobile(), Toast(), ToastContainer(), ToastContext, ToastProvider(), MAX_VISIBLE_TOASTS, TOAST_COLORS, TOAST_DURATIONS

### Community 29 - "botPrevention.js"
Cohesion: 0.23
Nodes (13): analyzeBehavior(), botPrevention(), checkHoneypot(), crypto, generateFingerprint(), HONEYPOT_FIELDS, isSuspiciousFingerprint(), isSuspiciousFingerprintMemory() (+5 more)

### Community 30 - "Backend Refactoring Orchestration Plan"
Cohesion: 0.07
Nodes (28): Acceptance Criteria, Acceptance Criteria, Acceptance Criteria, Backend Refactoring Orchestration Plan, Current State, Current State (Duplicated Logic), Current State (Monolithic), ✅ Definition of Done (+20 more)

### Community 31 - "plugins"
Cohesion: 0.22
Nodes (8): plugins, rules, react/only-export-components, react/rules-of-hooks, $schema, oxc, typescript, warn

### Community 32 - "GUILD Project — Comprehensive Performance Audit Report"
Cohesion: 0.17
Nodes (11): 📦 BUNDLE SIZE ANALYSIS (Current), 🗄️ DATABASE INDEX AUDIT, 📈 ESTIMATED IMPACT AFTER FIXES, 📊 Executive Summary, GUILD Project — Comprehensive Performance Audit Report, 📋 OPTIMIZATION ROADMAP (Prioritized), 🎯 PERFORMANCE BUDGETS (Recommended), Phase 1: Critical Fixes (Week 1–2) (+3 more)

### Community 33 - "FFProfileService.js"
Cohesion: 0.18
Nodes (13): submitUidRegion(), { buildProfileDataFromFF }, fetchFreeFireProfile(), ffClient, generateMockProfileData(), mapSoloStats(), VALID_REGIONS, { cleanNickname } (+5 more)

### Community 34 - "completeOnboarding"
Cohesion: 0.33
Nodes (5): completeOnboarding(), detectGuildStatus(), submitGameIdentity(), guildSchema, mongoose

### Community 35 - "🟢 LOW IMPACT / NICE-TO-HAVE"
Cohesion: 0.20
Nodes (10): BACKEND-015: `warmCatalog()` Runs Synchronously at Boot (Blocks Startup), BACKEND-016: No Health Check for MongoDB Connection Pool, BACKEND-017: `express.json({ limit: '100kb' })` Too Restrictive for Base64 Images, FRONTEND-008: No Bundle Analyzer in CI, FRONTEND-009: `registerSW.js` Not Inlined (Extra Request), FRONTEND-010: Missing `preconnect` / `dns-prefetch` for API Origin, 🟢 LOW IMPACT / NICE-TO-HAVE, MOBILE-006: Keystore Passwords in `gradle.properties` (Security + CI Issue) (+2 more)

### Community 36 - "useToast"
Cohesion: 0.31
Nodes (7): NotificationsPage, ToastDemoPage, useToast(), NotificationsPage(), ToastDemoPage(), getNotifications(), markAllRead()

### Community 37 - "index.js"
Cohesion: 0.40
Nodes (4): app, express, path, NOTE: the page HTML is a template literal; String.raw keeps \n escapes intact

### Community 38 - "Server.js"
Cohesion: 0.06
Nodes (45): mongoose, ffClient, getGuildInfo(), getGuildMembers(), getHealth(), getPlayerFull(), getPlayerGuild(), getPlayerProfile() (+37 more)

### Community 39 - "ff/client.js"
Cohesion: 0.21
Nodes (19): ApiLikeError, BASE_URL, CACHE, cacheGet(), cacheSet(), ffApiAvailable(), ffGet(), ffGetRaw() (+11 more)

### Community 114 - "MemberActionController.js"
Cohesion: 0.13
Nodes (17): ADMIN_ROLES, ASSIGNABLE_ROLES, assignRole(), ChangeLog, { emitPlayerProfileUpdate }, getPendingActions(), Membership, Notification (+9 more)

### Community 115 - "Design System Master File"
Cohesion: 0.11
Nodes (17): Additional Forbidden Patterns, Anti-Patterns (Do NOT Use), Buttons, Cards, Color Palette, Component Specs, Design System Master File, Global Rules (+9 more)

### Community 116 - "dependencies"
Cohesion: 0.13
Nodes (15): dependencies, bcrypt, dotenv, helmet, jsonwebtoken, mongoose, multer, socket.io (+7 more)

### Community 117 - "FreeFire-Api"
Cohesion: 0.13
Nodes (14): API Responses, Author, Contributing, Deployment, Features, FreeFire-Api, Get Player Personal Show, Get Player Stats (+6 more)

### Community 118 - "🔧 SPECIFIC CODE FIXES"
Cohesion: 0.20
Nodes (10): Fix 1: N+1 in `getMyProfile` (Backend/src/controllers/playerController.js), Fix 2: Materialized Leaderboard Score (Backend/src/models/PlayerProfile.js + Controller), Fix 3: Vite Config for Bundle Splitting (FrontEnd/vite.config.js), Fix 4: Android Release Build Optimization (FrontEnd/android/app/build.gradle), Fix 5: Tauri Release Profile (FrontEnd/src-tauri/Cargo.toml), Fix 6: Redis Integration for Caching & Rate Limiting (New File: Backend/src/config/redis.js), Fix 7: FF Item Catalog Optimization (Backend/src/services/ff/itemCatalog.js), Fix 8: Frontend Request Deduplication (FrontEnd/src/services/api/client.js) (+2 more)

### Community 119 - "LeaderboardPage.jsx"
Cohesion: 0.21
Nodes (8): LeaderboardPage, SkeletonLeaderboard(), AvatarWithFallback(), fmt(), LeaderboardPage(), rankStyleFor(), STAT_MODES, getPlayerLeaderboard()

### Community 120 - "GUILD Project - Comprehensive Code Quality & Architecture Review"
Cohesion: 0.25
Nodes (7): 12. METRICS BASELINE (Post-Refactor Targets), 9. SECURITY REVIEW, Appendix: Recommended Tooling, Executive Summary, ✅ Good Practices, GUILD Project - Comprehensive Code Quality & Architecture Review, ⚠️ Security Gaps

### Community 121 - "FFLiveData.jsx"
Cohesion: 0.24
Nodes (10): CombatBlock(), FFLiveData(), fmtAge(), fmtDuration(), fmtEpoch(), n(), PassGrid(), TierCard() (+2 more)

### Community 122 - "3. TYPE SAFETY — CRITICAL (3/10)"
Cohesion: 0.33
Nodes (6): 3. TYPE SAFETY — CRITICAL (3/10), Current State, Example: Mongoose Model with TypeScript, Immediate Actions Required, Impact, Type Definition Priorities

### Community 123 - "versionController.js"
Cohesion: 0.14
Nodes (9): mongoose, Version, getLatestVersion(), Version, mongoose, versionSchema, express, { getLatestVersion } (+1 more)

### Community 124 - "🔴 CRITICAL ISSUES (Must Fix Immediately)"
Cohesion: 0.33
Nodes (6): BACKEND-001: N+1 Query in `getMyProfile` — Player Profile Endpoint, BACKEND-002: `getPlayerLeaderboard` Loads ALL Profiles Into Memory, BACKEND-003: No Connection Pool Monitoring / Exhaustion Handling, 🔴 CRITICAL ISSUES (Must Fix Immediately), DB-001: Missing Compound Indexes for High-Frequency Queries, DB-002: `GuildMember` Model Uses `find()` Without Filter (Full Collection Scan)

### Community 125 - "adminController.js"
Cohesion: 0.18
Nodes (8): AuditController, LeadershipController, MemberActionController, RosterController, ChangeLog, getChangeLogs(), changeLogSchema, mongoose

### Community 126 - "scripts"
Cohesion: 0.50
Nodes (4): scripts, dev, start, test

### Community 127 - "devDependencies"
Cohesion: 0.67
Nodes (3): devDependencies, nodemon, nodemon

### Community 128 - "repository"
Cohesion: 0.67
Nodes (3): repository, type, url

### Community 129 - "10. PRIORITIZED ACTION PLAN"
Cohesion: 0.40
Nodes (5): 10. PRIORITIZED ACTION PLAN, 🔴 CRITICAL (Do First — Blocks Production), 🟠 HIGH (Next Sprint), 🟢 LOW (Polish), 🟡 MEDIUM (Technical Debt)

### Community 130 - "11. FILE-BY-FILE QUICK REFERENCE"
Cohesion: 0.40
Nodes (5): 11. FILE-BY-FILE QUICK REFERENCE, Backend — Good Patterns to Preserve, Backend — Must Refactor, Frontend — Good Patterns to Preserve, Frontend — Must Refactor

### Community 131 - "useAuth"
Cohesion: 0.16
Nodes (17): AppRoutes(), isMobileDevice(), loadGsiScript(), SocialLogin(), AuthContext, useAuth(), useLogin(), googleLogin() (+9 more)

### Community 132 - "1. ARCHITECTURE (7.5/10)"
Cohesion: 0.40
Nodes (5): 1. ARCHITECTURE (7.5/10), Architecture Diagram (Current), ⚠️ Issues, Recommended Architecture, ✅ Strengths

### Community 133 - "2. CODE QUALITY (7/10)"
Cohesion: 0.40
Nodes (5): 2. CODE QUALITY (7/10), Complexity Hotspots (Cyclomatic Complexity > 15), ❌ DRY Violations, Naming Inconsistencies, ✅ Strengths

### Community 134 - "4. TESTING — CRITICAL (1/10)"
Cohesion: 0.40
Nodes (5): 4. TESTING — CRITICAL (1/10), Current State, Minimum Viable Test Coverage Targets, Risk Assessment, Testing Strategy (Priority Order)

### Community 136 - "finalizeGoogleLogin"
Cohesion: 0.20
Nodes (10): createGuild(), finalizeGoogleLogin(), generateAccessToken(), generateRefreshToken(), getMe(), googleAuth(), googleCallback(), hashRefreshToken() (+2 more)

### Community 137 - "5. PERFORMANCE (6.5/10)"
Cohesion: 0.50
Nodes (4): 5. PERFORMANCE (6.5/10), Database Index Audit, ⚠️ Issues, ✅ Strengths

### Community 138 - "ffTransformers.js"
Cohesion: 0.36
Nodes (8): buildProfileDataFromFF(), cleanNickname(), normalizeGender(), normalizeModeStats(), normalizeRankshow(), pickBlock(), stripPrefix(), toIsoDate()

### Community 140 - "6. MAINTAINABILITY (6/10)"
Cohesion: 0.50
Nodes (4): 6. MAINTAINABILITY (6/10), Coupling Analysis, Documentation Gaps, Technical Debt Inventory

### Community 141 - "7. PATTERNS (7/10)"
Cohesion: 0.50
Nodes (4): 7. PATTERNS (7/10), ❌ Anti-Patterns, Design Pattern Opportunities, ✅ Good Patterns Used

### Community 142 - "8. ERROR HANDLING (7.5/10)"
Cohesion: 0.50
Nodes (4): 8. ERROR HANDLING (7.5/10), Error Handling Improvements, ⚠️ Issues, ✅ Strengths

### Community 150 - "AssetResolutionService.js"
Cohesion: 0.40
Nodes (4): buildProfilePreviewObject(), { cleanNickname }, itemCatalog, resolveProfileAssets()

### Community 151 - "adminApi.js"
Cohesion: 0.13
Nodes (27): ActivityTab(), truncate(), GAMES, GuildPlayersTab(), STATUS_FILTERS, MembersTab(), PendingTab(), TYPE_LABEL (+19 more)

## Knowledge Gaps
- **498 isolated node(s):** `name`, `version`, `description`, `homepage`, `url` (+493 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **13 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `apiFetch()` connect `apiFetch` to `useAuth`, `useToast`, `api/client.js`, `resolveMediaUrl`, `ProfilePage.jsx`, `LeaderboardPage.jsx`, `adminApi.js`, `FFLiveData.jsx`?**
  _High betweenness centrality (0.018) - this node is a cross-community bridge._
- **Why does `getMemberById()` connect `memberController.js` to `mediaRoutes.js`?**
  _High betweenness centrality (0.010) - this node is a cross-community bridge._
- **Why does `react` connect `useAuth` to `apiFetch`, `App.jsx`, `useToast`, `api/client.js`, `resolveMediaUrl`, `ProfilePage.jsx`, `LeaderboardPage.jsx`, `adminApi.js`, `FFLiveData.jsx`, `ToastProvider.jsx`, `plugins`?**
  _High betweenness centrality (0.008) - this node is a cross-community bridge._
- **What connects `name`, `version`, `description` to the rest of the system?**
  _498 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `apiFetch` be split into smaller, more focused modules?**
  _Cohesion score 0.05839727195225917 - nodes in this community are weakly interconnected._
- **Should `dependencies` be split into smaller, more focused modules?**
  _Cohesion score 0.09090909090909091 - nodes in this community are weakly interconnected._
- **Should `adminRoutes.js` be split into smaller, more focused modules?**
  _Cohesion score 0.12857142857142856 - nodes in this community are weakly interconnected._