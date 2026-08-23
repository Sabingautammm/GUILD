# Graph Report - GUILD  (2026-08-18)

## Corpus Check
- 159 files · ~379,210 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 1118 nodes · 1982 edges · 151 communities (134 shown, 17 thin omitted)
- Extraction: 94% EXTRACTED · 6% INFERRED · 0% AMBIGUOUS · INFERRED: 114 edges (avg confidence: 0.5)
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `371306a7`
- Run `git rev-parse HEAD` and compare to check if the graph is stale.
- Run `graphify update .` after code changes (no API cost).

## Community Hubs (Navigation)
- apiFetch
- dependencies
- adminController.js
- App.jsx
- dependencies
- Server.js
- InGame.py
- guildController.js
- GalleryPage.jsx
- ff-account.js
- ff-ingame.js
- useAuth
- Backend/package.json
- mediaRoutes.js
- server.js
- authController.js
- tauri.conf.json
- notificationRoutes.js
- ProfilePage.jsx
- leaderboardController.js
- ff-utils.js
- SeasonStatus.jsx
- playerController.js
- authRoutes.js
- test_ui_cdp.js
- AppDelegate
- memberController.js
- rankTiers.js
- Toast.jsx
- botPrevention.js
- SocialLogin.jsx
- plugins
- devDependencies
- getClanMainPageInfo
- completeOnboarding
- scripts
- useToast
- index.js
- ffController.js
- ff/client.js
- cors
- build.sh
- vercel.json
- authMiddleware.js
- Design System Master File
- dependencies
- FreeFire-Api
- org.junit.Test
- default.json
- adminApi.js
- FFLiveData.jsx
- MainActivity
- socket.js
- FrontEnd/package.json
- ChangeLog.js
- scripts
- devDependencies
- repository
- gradlew
- @capacitor/android
- ErrorBoundary
- jsonwebtoken
- mongoose
- multer
- FrontEnd/README.md
- capacitor.config.ts
- tailwindcss
- cookie-parser
- @tailwindcss/vite
- guild
- bcrypt

## God Nodes (most connected - your core abstractions)
1. `apiFetch()` - 86 edges
2. `useAuth()` - 40 edges
3. `react` - 33 edges
4. `useToast()` - 32 edges
5. `resolveMediaUrl()` - 25 edges
6. `playerName()` - 22 edges
7. `ApiError` - 18 edges
8. `getPlayerFull()` - 12 edges
9. `decodeProto()` - 12 edges
10. `withCache()` - 11 edges

## Surprising Connections (you probably didn't know these)
- `AppRoutes()` --calls--> `useAuth()`  [EXTRACTED]
  FrontEnd/src/App.jsx → FrontEnd/src/features/auth/context/AuthContext.jsx
- `AdminPage()` --calls--> `useAuth()`  [EXTRACTED]
  FrontEnd/src/pages/AdminPage.jsx → FrontEnd/src/features/auth/context/AuthContext.jsx
- `PassGrid()` --calls--> `resolveMediaUrl()`  [EXTRACTED]
  FrontEnd/src/features/dashboard/components/FFLiveData.jsx → FrontEnd/src/utils/mediaUrl.js
- `RoleChip()` --calls--> `playerName()`  [EXTRACTED]
  FrontEnd/src/pages/GuildPage.jsx → FrontEnd/src/utils/playerName.js
- `AvatarWithFallback()` --calls--> `resolveMediaUrl()`  [EXTRACTED]
  FrontEnd/src/pages/LeaderboardPage.jsx → FrontEnd/src/utils/mediaUrl.js

## Import Cycles
- None detected.

## Communities (151 total, 17 thin omitted)

### Community 0 - "apiFetch"
Cohesion: 0.06
Nodes (59): EnterUidRegionPage, GuildPage, OnboardingPage, SkeletonGuild(), AuthProvider(), changePassword(), checkGuildUid(), completeOnboarding() (+51 more)

### Community 1 - "dependencies"
Cohesion: 0.09
Nodes (21): dependencies, cors, dotenv, express, nodemon, protobufjs, protobufjs-cli, description (+13 more)

### Community 2 - "adminController.js"
Cohesion: 0.10
Nodes (34): addPlayerByGameUid(), ADMIN_ROLES, assignRole(), autoCancelExpiredActions(), bcrypt, ChangeLog, claimLeadership(), completeTransfer() (+26 more)

### Community 3 - "App.jsx"
Cohesion: 0.08
Nodes (22): App(), AppRoutes(), LeaderboardPage, MemberDetailsPage, MembersPage, ReelPage, Navbar(), ProtectedRoutes() (+14 more)

### Community 4 - "dependencies"
Cohesion: 0.12
Nodes (17): @capacitor/core, @capacitor/ios, framer-motion, dependencies, @capacitor/core, @capacitor/ios, framer-motion, react (+9 more)

### Community 5 - "Server.js"
Cohesion: 0.09
Nodes (18): mongoose, errorHandler(), notFound(), allowedOrigins, app, connectDB, cookieParser, cors (+10 more)

### Community 6 - "InGame.py"
Cohesion: 0.25
Nodes (6): get_player_personal_show(), get_player_stats(), Perform a fuzzy account search by keyword. Args: server_url (str): Base URL of…, Get player statistics for BR or CS mode Args: mode (str): "br" or "cs" uid…, Get player personal show data Args: authorization (str): Bearer token for…, search_account_by_keyword()

### Community 7 - "guildController.js"
Cohesion: 0.10
Nodes (23): applyToGuild(), ChangeLog, disbandGuild(), getGuildProfile(), getPrivateGuildView(), Guild, GUILD_ADMIN_ROLES, GuildPlayer (+15 more)

### Community 8 - "GalleryPage.jsx"
Cohesion: 0.12
Nodes (26): GalleryPage, MediaCard(), SkeletonMediaGrid(), MediaTab(), PlayerIdCard(), RankingCard(), GalleryPage(), IMAGE_EXTENSIONS (+18 more)

### Community 9 - "ff-account.js"
Cohesion: 0.11
Nodes (19): { encodeProto, decodeProto, postExpectContinue, postForm, safeJson }, {
  GARENA_TOKEN_URL,
  MAJOR_LOGIN_URL,
  CLIENT_SECRET,
  CLIENT_ID,
  RELEASEVERSION,
  DEBUG,
}, getGarenaToken(), { MajorLogin }, searchClanByName(), ACCOUNT_KEYS, ACCOUNTS, CLIENT_ID (+11 more)

### Community 10 - "ff-ingame.js"
Cohesion: 0.11
Nodes (25): addRates(), authHeaders(), CLAN_ACTIVITY_TYPE, { encodeProto, decodeProto, postExpectContinue }, getPlayerGallery(), getPlayerPersonalShow(), getPlayerRank(), getPlayerStats() (+17 more)

### Community 11 - "useAuth"
Cohesion: 0.27
Nodes (12): BottomNavbar(), navItems, DesktopNavbar(), navItems, useUnreadCount(), MobileHeader(), Avatar(), AuthContext (+4 more)

### Community 12 - "Backend/package.json"
Cohesion: 0.15
Nodes (12): author, bugs, url, description, engines, node, homepage, license (+4 more)

### Community 13 - "mediaRoutes.js"
Cohesion: 0.06
Nodes (41): LIMITS, MIME_TYPES, path, addComment(), getGallery(), getLimit(), getMyMedia(), getPendingForAdmin() (+33 more)

### Community 14 - "server.js"
Cohesion: 0.10
Nodes (17): { ACCOUNTS, RATE_LIMIT_MAX, RATE_LIMIT_WINDOW_MS }, { ApiError }, app, authenticate(), cors, crypto, doLogin(), express (+9 more)

### Community 15 - "authController.js"
Cohesion: 0.08
Nodes (28): ADMIN_ROLES, bcrypt, buildProfileDataFromFF(), ChangeLog, DUMMY_BCRYPT_HASH, { emitPlayerStatsUpdate, emitPlayerProfileUpdate }, ffClient, GAMES (+20 more)

### Community 16 - "tauri.conf.json"
Cohesion: 0.07
Nodes (28): app, security, windows, build, beforeBuildCommand, beforeDevCommand, devUrl, frontendDist (+20 more)

### Community 17 - "notificationRoutes.js"
Cohesion: 0.19
Nodes (10): getNotifications(), getUnreadCount(), markRead(), Notification, mongoose, notificationSchema, express, { getNotifications, getUnreadCount, markRead } (+2 more)

### Community 18 - "ProfilePage.jsx"
Cohesion: 0.18
Nodes (11): ProfilePage, PasswordInput(), usePlayerProfile(), sanitizeStats(), usePlayerStatsSocket(), HomePage(), AVATAR_EXTENSIONS, AVATAR_MIMES (+3 more)

### Community 19 - "leaderboardController.js"
Cohesion: 0.19
Nodes (14): clampPercent(), computeTotals(), getGuildLeaderboard(), getPlayerLeaderboard(), Guild, Membership, num(), PlayerProfile (+6 more)

### Community 20 - "ff-utils.js"
Cohesion: 0.17
Nodes (13): getMajorLogin(), aesCbcDecrypt(), aesCbcEncrypt(), ApiError, crypto, decodeProto(), encodeProto(), https (+5 more)

### Community 22 - "playerController.js"
Cohesion: 0.19
Nodes (18): aggregateBr(), cleanNickname(), { emitPlayerStatsUpdate, emitPlayerProfileUpdate }, ensureStats(), ffClient, finiteOr(), getMyProfile(), Guild (+10 more)

### Community 23 - "authRoutes.js"
Cohesion: 0.12
Nodes (18): changePassword(), checkGuildUid(), createGuild(), deleteAccount(), generateToken(), getMe(), googleAuth(), logout() (+10 more)

### Community 24 - "test_ui_cdp.js"
Cohesion: 0.20
Nodes (13): edge, EDGE_CANDIDATES, edgeProc, evaluate(), { execFileSync, spawn }, fs, getJson(), main() (+5 more)

### Community 25 - "AppDelegate"
Cohesion: 0.13
Nodes (13): Any, Bool, Capacitor, AppDelegate, NSUserActivity, UIApplication, UIApplicationDelegate, UIKit (+5 more)

### Community 26 - "memberController.js"
Cohesion: 0.22
Nodes (10): DEFAULT_MEMBERS, getMemberById(), getMembers(), GuildMember, mongoose, guildMemberSchema, mongoose, express (+2 more)

### Community 27 - "rankTiers.js"
Cohesion: 0.31
Nodes (9): BR_BY_ID, BR_TIERS, CS_BY_ID, CS_STAR_TIERS, CS_TIERS, mapBr(), mapCs(), progress() (+1 more)

### Community 28 - "Toast.jsx"
Cohesion: 0.31
Nodes (6): isMobile(), Toast(), ToastContainer(), MAX_VISIBLE_TOASTS, TOAST_COLORS, TOAST_DURATIONS

### Community 29 - "botPrevention.js"
Cohesion: 0.27
Nodes (10): analyzeBehavior(), botPrevention(), checkHoneypot(), crypto, fingerprintStore, generateFingerprint(), HONEYPOT_FIELDS, isSuspiciousFingerprint() (+2 more)

### Community 30 - "SocialLogin.jsx"
Cohesion: 0.36
Nodes (6): LoginForm(), isMobileDevice(), loadGsiScript(), SocialLogin(), googleLogin(), AuthPage()

### Community 31 - "plugins"
Cohesion: 0.22
Nodes (8): plugins, rules, react/only-export-components, react/rules-of-hooks, $schema, oxc, typescript, warn

### Community 32 - "devDependencies"
Cohesion: 0.13
Nodes (15): @capacitor/cli, devDependencies, @capacitor/cli, oxlint, @tauri-apps/cli, typescript, vite, vite-plugin-pwa (+7 more)

### Community 33 - "getClanMainPageInfo"
Cohesion: 0.31
Nodes (10): cacheGet(), cacheSet(), enrichPlayers(), getClanMainPageInfo(), getClanOfficers(), getGuildMembers(), getGuildMemberUids(), getPlayerProfileCached() (+2 more)

### Community 34 - "completeOnboarding"
Cohesion: 0.18
Nodes (10): cleanNickname(), completeOnboarding(), detectGuildStatus(), submitGameIdentity(), submitUidRegion(), guildSchema, mongoose, mongoose (+2 more)

### Community 35 - "scripts"
Cohesion: 0.22
Nodes (9): scripts, android:apk, build, cap:sync, dev, lint, preview, start (+1 more)

### Community 36 - "useToast"
Cohesion: 0.22
Nodes (10): NotificationsPage, ToastDemoPage, ToastContext, ToastProvider(), useToast(), NotificationsPage(), ToastDemoPage(), getNotifications() (+2 more)

### Community 37 - "index.js"
Cohesion: 0.40
Nodes (4): app, express, path, NOTE: the page HTML is a template literal; String.raw keeps \n escapes intact

### Community 38 - "ffController.js"
Cohesion: 0.12
Nodes (31): ffClient, getGuildInfo(), getGuildMembers(), getHealth(), getPlayerFull(), getPlayerGuild(), getPlayerProfile(), getPlayerRank() (+23 more)

### Community 39 - "ff/client.js"
Cohesion: 0.22
Nodes (19): ApiLikeError, BASE_URL, CACHE, cacheGet(), cacheSet(), ffApiAvailable(), ffGet(), ffGetRaw() (+11 more)

### Community 114 - "authMiddleware.js"
Cohesion: 0.14
Nodes (13): jwt, Membership, optionalAuth(), protect(), requireRole(), User, bcrypt, mongoose (+5 more)

### Community 115 - "Design System Master File"
Cohesion: 0.11
Nodes (17): Additional Forbidden Patterns, Anti-Patterns (Do NOT Use), Buttons, Cards, Color Palette, Component Specs, Design System Master File, Global Rules (+9 more)

### Community 116 - "dependencies"
Cohesion: 0.13
Nodes (15): dependencies, dotenv, express, express-rate-limit, google-auth-library, helmet, protobufjs, socket.io (+7 more)

### Community 117 - "FreeFire-Api"
Cohesion: 0.13
Nodes (14): API Responses, Author, Contributing, Deployment, Features, FreeFire-Api, Get Player Personal Show, Get Player Stats (+6 more)

### Community 118 - "org.junit.Test"
Cohesion: 0.36
Nodes (4): ExampleInstrumentedTest, ExampleUnitTest, org.junit.runner.RunWith, org.junit.Test

### Community 119 - "default.json"
Cohesion: 0.25
Nodes (7): description, identifier, permissions, $schema, windows, core:default, main

### Community 120 - "adminApi.js"
Cohesion: 0.12
Nodes (30): AdminPage, ActivityTab(), truncate(), GAMES, GuildPlayersTab(), STATUS_FILTERS, MembersTab(), PendingTab() (+22 more)

### Community 121 - "FFLiveData.jsx"
Cohesion: 0.24
Nodes (10): CombatBlock(), FFLiveData(), fmtAge(), fmtDuration(), fmtEpoch(), n(), PassGrid(), TierCard() (+2 more)

### Community 122 - "MainActivity"
Cohesion: 0.40
Nodes (4): Bundle, com.getcapacitor.BridgeActivity, MainActivity, Override

### Community 123 - "socket.js"
Cohesion: 0.29
Nodes (5): initializeSocket(), jwt, { Server }, User, userSockets

### Community 124 - "FrontEnd/package.json"
Cohesion: 0.40
Nodes (4): name, private, type, version

### Community 126 - "scripts"
Cohesion: 0.50
Nodes (4): scripts, dev, start, test

### Community 127 - "devDependencies"
Cohesion: 0.67
Nodes (3): devDependencies, nodemon, nodemon

### Community 128 - "repository"
Cohesion: 0.67
Nodes (3): repository, type, url

### Community 129 - "gradlew"
Cohesion: 0.83
Nodes (3): gradlew script, die(), warn()

## Knowledge Gaps
- **352 isolated node(s):** `name`, `version`, `description`, `homepage`, `url` (+347 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **17 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `apiFetch()` connect `apiFetch` to `App.jsx`, `useToast`, `GalleryPage.jsx`, `useAuth`, `ProfilePage.jsx`, `adminApi.js`, `FFLiveData.jsx`, `SocialLogin.jsx`?**
  _High betweenness centrality (0.016) - this node is a cross-community bridge._
- **Why does `react` connect `useAuth` to `apiFetch`, `App.jsx`, `useToast`, `GalleryPage.jsx`, `ProfilePage.jsx`, `adminApi.js`, `FFLiveData.jsx`, `Toast.jsx`, `SocialLogin.jsx`, `plugins`?**
  _High betweenness centrality (0.011) - this node is a cross-community bridge._
- **Why does `getMemberById()` connect `memberController.js` to `mediaRoutes.js`?**
  _High betweenness centrality (0.007) - this node is a cross-community bridge._
- **What connects `name`, `version`, `description` to the rest of the system?**
  _352 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `apiFetch` be split into smaller, more focused modules?**
  _Cohesion score 0.05578947368421053 - nodes in this community are weakly interconnected._
- **Should `dependencies` be split into smaller, more focused modules?**
  _Cohesion score 0.09090909090909091 - nodes in this community are weakly interconnected._
- **Should `adminController.js` be split into smaller, more focused modules?**
  _Cohesion score 0.09682539682539683 - nodes in this community are weakly interconnected._