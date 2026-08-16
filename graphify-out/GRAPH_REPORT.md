# Graph Report - GUILD  (2026-08-16)

## Corpus Check
- cluster-only mode — file stats not available

## Summary
- 929 nodes · 1709 edges · 122 communities (119 shown, 3 thin omitted)
- Extraction: 94% EXTRACTED · 6% INFERRED · 0% AMBIGUOUS · INFERRED: 98 edges (avg confidence: 0.52)
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `d8a4b22d`
- Run `git rev-parse HEAD` and compare to check if the graph is stale.
- Run `graphify update .` after code changes (no API cost).

## Community Hubs (Navigation)
- Community 0
- Community 1
- Community 2
- Community 3
- Community 4
- Community 5
- Community 6
- Community 7
- Community 8
- Community 9
- Community 10
- Community 11
- Community 12
- Community 13
- Community 14
- Community 15
- Community 16
- Community 17
- Community 18
- Community 19
- Community 20
- Community 21
- Community 22
- Community 23
- Community 24
- Community 25
- Community 26
- Community 27
- Community 28
- Community 29
- Community 30
- Community 31
- Community 32
- Community 33
- Community 34
- Community 35
- Community 36
- Community 37
- Community 38
- Community 39
- Community 40
- Community 41
- Community 42
- Community 43
- Community 44
- Community 45
- Community 46
- Community 48
- Community 50
- Community 59

## God Nodes (most connected - your core abstractions)
1. `apiFetch()` - 81 edges
2. `useAuth()` - 40 edges
3. `useToast()` - 32 edges
4. `react` - 32 edges
5. `playerName()` - 22 edges
6. `resolveMediaUrl()` - 21 edges
7. `ApiError` - 18 edges
8. `decodeProto()` - 12 edges
9. `encode_protobuf()` - 11 edges
10. `postProto()` - 11 edges

## Surprising Connections (you probably didn't know these)
- `AdminPage()` --calls--> `useAuth()`  [EXTRACTED]
  FrontEnd/src/pages/AdminPage.jsx → FrontEnd/src/features/auth/context/AuthContext.jsx
- `AvatarWithFallback()` --calls--> `resolveMediaUrl()`  [EXTRACTED]
  FrontEnd/src/pages/LeaderboardPage.jsx → FrontEnd/src/utils/mediaUrl.js
- `updateMyProfile()` --calls--> `apiFetch()`  [EXTRACTED]
  FrontEnd/src/features/dashboard/services/playerApi.js → FrontEnd/src/services/api/client.js
- `removeGuildPlayer()` --calls--> `apiFetch()`  [EXTRACTED]
  FrontEnd/src/services/api/adminApi.js → FrontEnd/src/services/api/client.js
- `markRead()` --calls--> `apiFetch()`  [EXTRACTED]
  FrontEnd/src/services/api/notificationApi.js → FrontEnd/src/services/api/client.js

## Import Cycles
- None detected.

## Communities (122 total, 3 thin omitted)

### Community 0 - "Community 0"
Cohesion: 0.07
Nodes (40): LIMITS, MIME_TYPES, path, addComment(), getGallery(), getLimit(), getMyMedia(), getPendingForAdmin() (+32 more)

### Community 1 - "Community 1"
Cohesion: 0.09
Nodes (36): addPlayerByGameUid(), ADMIN_ROLES, assignRole(), autoCancelExpiredActions(), bcrypt, ChangeLog, claimLeadership(), completeTransfer() (+28 more)

### Community 2 - "Community 2"
Cohesion: 0.06
Nodes (34): framer-motion, dependencies, framer-motion, react, react-dom, react-icons, react-router-dom, socket.io-client (+26 more)

### Community 3 - "Community 3"
Cohesion: 0.15
Nodes (25): Exception, get_garena_token(), get_major_login(), Perform major login with the provided credentials Args: logintoken (str): The…, Get Garena token using uid and password Args: uid (str): User ID password…, get_player_personal_show(), get_player_stats(), Perform a fuzzy account search by keyword. Args: server_url (str): Base URL of… (+17 more)

### Community 4 - "Community 4"
Cohesion: 0.09
Nodes (25): applyToGuild(), ChangeLog, disbandGuild(), getGuildProfile(), getPrivateGuildView(), Guild, GUILD_ADMIN_ROLES, GuildPlayer (+17 more)

### Community 5 - "Community 5"
Cohesion: 0.13
Nodes (28): addRates(), authHeaders(), cacheGet(), cacheSet(), CLAN_ACTIVITY_TYPE, { encodeProto, decodeProto, postExpectContinue }, enrichPlayers(), getClanMainPageInfo() (+20 more)

### Community 6 - "Community 6"
Cohesion: 0.13
Nodes (25): AuthProvider(), changePassword(), checkGuildUid(), createGuild(), deleteAccount(), getCurrentUser(), leaderLogin(), logout() (+17 more)

### Community 7 - "Community 7"
Cohesion: 0.10
Nodes (21): { encodeProto, decodeProto, postExpectContinue, postForm, safeJson }, {
  GARENA_TOKEN_URL,
  MAJOR_LOGIN_URL,
  CLIENT_SECRET,
  CLIENT_ID,
  RELEASEVERSION,
  DEBUG,
}, getGarenaToken(), { MajorLogin }, searchAccountByKeyword(), { ACCOUNTS }, { getGarenaToken, getMajorLogin }, { getPlayerPersonalShow, getPlayerStats, searchAccountByKeyword } (+13 more)

### Community 8 - "Community 8"
Cohesion: 0.10
Nodes (15): App(), AppRoutes(), GuildPage, MemberDetailsPage, Navbar(), ProtectedRoutes(), FullPageSkeleton(), Skeleton() (+7 more)

### Community 9 - "Community 9"
Cohesion: 0.09
Nodes (18): { ACCOUNTS, RATE_LIMIT_MAX, RATE_LIMIT_WINDOW_MS }, { ApiError }, app, authenticate(), cors, crypto, doLogin(), express (+10 more)

### Community 10 - "Community 10"
Cohesion: 0.09
Nodes (23): dependencies, bcrypt, cookie-parser, cors, express, express-rate-limit, google-auth-library, helmet (+15 more)

### Community 11 - "Community 11"
Cohesion: 0.14
Nodes (13): EnterUidRegionPage, OnboardingPage, ToastDemoPage, ToastContext, ToastProvider(), useToast(), completeOnboarding(), submitUidRegion() (+5 more)

### Community 12 - "Community 12"
Cohesion: 0.16
Nodes (18): GalleryPage, ReelPage, MediaCard(), GalleryPage(), IMAGE_EXTENSIONS, IMAGE_MIMES, validateMediaFile(), VIDEO_EXTENSIONS (+10 more)

### Community 13 - "Community 13"
Cohesion: 0.10
Nodes (17): mongoose, errorHandler(), notFound(), allowedOrigins, app, connectDB, cookieParser, cors (+9 more)

### Community 14 - "Community 14"
Cohesion: 0.11
Nodes (21): ADMIN_ROLES, bcrypt, ChangeLog, createGuild(), DUMMY_BCRYPT_HASH, { emitPlayerStatsUpdate, emitPlayerProfileUpdate }, GAMES, generateToken() (+13 more)

### Community 15 - "Community 15"
Cohesion: 0.14
Nodes (18): completeOnboarding(), detectGuildStatus(), submitGameIdentity(), submitUidRegion(), { emitPlayerStatsUpdate, emitPlayerProfileUpdate }, getMyProfile(), Guild, Membership (+10 more)

### Community 16 - "Community 16"
Cohesion: 0.18
Nodes (16): AdminPage, SkeletonMediaGrid(), ActivityTab(), truncate(), MediaTab(), PendingTab(), TYPE_LABEL, AdminPage() (+8 more)

### Community 17 - "Community 17"
Cohesion: 0.18
Nodes (11): LeaderboardPage, MembersPage, SkeletonList(), AvatarWithFallback(), fmt(), LeaderboardPage(), rankStyleFor(), STAT_MODES (+3 more)

### Community 18 - "Community 18"
Cohesion: 0.16
Nodes (10): ProfilePage, PasswordInput(), usePlayerProfile(), getMyProfile(), updateMyProfile(), AVATAR_EXTENSIONS, AVATAR_MIMES, ProfilePage() (+2 more)

### Community 19 - "Community 19"
Cohesion: 0.27
Nodes (13): MembersTab(), TransferTab(), MOCK_PLAYER, ROLE_LABEL, claimLeadership(), completeTransfer(), deleteExMember(), getExMembers() (+5 more)

### Community 20 - "Community 20"
Cohesion: 0.12
Nodes (15): author, bugs, url, description, engines, node, homepage, license (+7 more)

### Community 21 - "Community 21"
Cohesion: 0.19
Nodes (14): clampPercent(), computeTotals(), getGuildLeaderboard(), getPlayerLeaderboard(), Guild, Membership, num(), PlayerProfile (+6 more)

### Community 22 - "Community 22"
Cohesion: 0.17
Nodes (14): getMajorLogin(), searchClanByName(), main(), aesCbcDecrypt(), aesCbcEncrypt(), crypto, decodeProto(), encodeProto() (+6 more)

### Community 23 - "Community 23"
Cohesion: 0.15
Nodes (12): jwt, Membership, optionalAuth(), protect(), requireRole(), User, membershipSchema, mongoose (+4 more)

### Community 24 - "Community 24"
Cohesion: 0.13
Nodes (12): crypto, MAIN_IV, MAIN_KEY, mine, mineRaw, myEnc, myProto, path (+4 more)

### Community 25 - "Community 25"
Cohesion: 0.19
Nodes (10): NotificationsPage, NotificationsPage(), addBotProtectionFields(), ApiError, CLIENT_FINGERPRINT, defaultMessageForStatus(), PAGE_LOAD_TIME, getNotifications() (+2 more)

### Community 26 - "Community 26"
Cohesion: 0.30
Nodes (9): DesktopNavbar(), navItems, useUnreadCount(), MobileHeader(), Avatar(), PlayerIdCard(), getUnreadCount(), API_ORIGIN (+1 more)

### Community 27 - "Community 27"
Cohesion: 0.14
Nodes (13): changePassword(), checkGuildUid(), deleteAccount(), logout(), verifyLeaderPassword(), authBotPrevention, { authLimiter }, { botPrevention } (+5 more)

### Community 28 - "Community 28"
Cohesion: 0.20
Nodes (13): edge, EDGE_CANDIDATES, edgeProc, evaluate(), { execFileSync, spawn }, fs, getJson(), main() (+5 more)

### Community 29 - "Community 29"
Cohesion: 0.18
Nodes (10): DEFAULT_MEMBERS, getMemberById(), getMembers(), GuildMember, mongoose, guildMemberSchema, mongoose, express (+2 more)

### Community 30 - "Community 30"
Cohesion: 0.19
Nodes (10): getNotifications(), getUnreadCount(), markRead(), Notification, mongoose, notificationSchema, express, { getNotifications, getUnreadCount, markRead } (+2 more)

### Community 31 - "Community 31"
Cohesion: 0.19
Nodes (12): getPlayerPersonalShow(), getPlayerRank(), splitPasses(), BR_BY_ID, BR_TIERS, CS_BY_ID, CS_STAR_TIERS, CS_TIERS (+4 more)

### Community 32 - "Community 32"
Cohesion: 0.13
Nodes (15): dotenv, protobufjs, dotenv, protobufjs, dependencies, cors, dotenv, express (+7 more)

### Community 33 - "Community 33"
Cohesion: 0.27
Nodes (10): analyzeBehavior(), botPrevention(), checkHoneypot(), crypto, fingerprintStore, generateFingerprint(), HONEYPOT_FIELDS, isSuspiciousFingerprint() (+2 more)

### Community 34 - "Community 34"
Cohesion: 0.17
Nodes (7): crypto, https, MAIN_IV, MAIN_KEY, { MajorLogin }, { pad, toCamel }, zlib

### Community 35 - "Community 35"
Cohesion: 0.32
Nodes (8): BottomNavbar(), navItems, AuthContext, useAuth(), useLogin(), usePlayerStatsSocket(), HomePage(), react

### Community 36 - "Community 36"
Cohesion: 0.18
Nodes (8): bcrypt, mongoose, userSchema, initializeSocket(), jwt, { Server }, User, userSockets

### Community 37 - "Community 37"
Cohesion: 0.24
Nodes (4): ModeStatsCard(), RankingCard(), SeasonStatsSection(), MediaPreviewCard()

### Community 38 - "Community 38"
Cohesion: 0.31
Nodes (6): isMobile(), Toast(), ToastContainer(), MAX_VISIBLE_TOASTS, TOAST_COLORS, TOAST_DURATIONS

### Community 39 - "Community 39"
Cohesion: 0.22
Nodes (8): description, main, name, scripts, build:proto, dev, start, version

### Community 40 - "Community 40"
Cohesion: 0.22
Nodes (8): plugins, rules, react/only-export-components, react/rules-of-hooks, $schema, oxc, typescript, warn

### Community 41 - "Community 41"
Cohesion: 0.36
Nodes (6): LoginForm(), isMobileDevice(), loadGsiScript(), SocialLogin(), googleLogin(), AuthPage()

### Community 42 - "Community 42"
Cohesion: 0.56
Nodes (7): GuildPage(), applyToGuild(), disbandGuild(), getGuildProfile(), getPrivateGuildView(), leaveGuild(), updateGuild()

### Community 43 - "Community 43"
Cohesion: 0.36
Nodes (6): GAMES, GuildPlayersTab(), STATUS_FILTERS, addPlayerByGameUid(), getGuildPlayers(), searchGuildPlayer()

### Community 45 - "Community 45"
Cohesion: 0.40
Nodes (4): app, express, path, NOTE: the page HTML is a template literal; String.raw keeps \n escapes intact

### Community 46 - "Community 46"
Cohesion: 0.50
Nodes (4): scripts, dev, start, test

### Community 48 - "Community 48"
Cohesion: 0.67
Nodes (3): devDependencies, nodemon, nodemon

## Knowledge Gaps
- **300 isolated node(s):** `path`, `Media`, `mongoose`, `Notification`, `{ persistValidatedFile }` (+295 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **3 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `apiFetch()` connect `Community 6` to `Community 8`, `Community 41`, `Community 42`, `Community 11`, `Community 43`, `Community 12`, `Community 16`, `Community 17`, `Community 18`, `Community 19`, `Community 25`, `Community 26`?**
  _High betweenness centrality (0.021) - this node is a cross-community bridge._
- **Why does `react` connect `Community 35` to `Community 37`, `Community 38`, `Community 40`, `Community 8`, `Community 41`, `Community 11`, `Community 12`, `Community 43`, `Community 42`, `Community 16`, `Community 17`, `Community 18`, `Community 19`, `Community 25`, `Community 26`?**
  _High betweenness centrality (0.013) - this node is a cross-community bridge._
- **Why does `getMemberById()` connect `Community 29` to `Community 23`?**
  _High betweenness centrality (0.007) - this node is a cross-community bridge._
- **What connects `path`, `Media`, `mongoose` to the rest of the system?**
  _300 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Community 0` be split into smaller, more focused modules?**
  _Cohesion score 0.06845513413506013 - nodes in this community are weakly interconnected._
- **Should `Community 1` be split into smaller, more focused modules?**
  _Cohesion score 0.08636977058029689 - nodes in this community are weakly interconnected._
- **Should `Community 2` be split into smaller, more focused modules?**
  _Cohesion score 0.05714285714285714 - nodes in this community are weakly interconnected._