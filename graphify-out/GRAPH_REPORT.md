# Graph Report - GUILD  (2026-08-16)

## Corpus Check
- cluster-only mode — file stats not available

## Summary
- 903 nodes · 1681 edges · 114 communities (110 shown, 4 thin omitted)
- Extraction: 94% EXTRACTED · 6% INFERRED · 0% AMBIGUOUS · INFERRED: 98 edges (avg confidence: 0.52)
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `67311684`
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
- Community 41
- Community 50

## God Nodes (most connected - your core abstractions)
1. `apiFetch()` - 81 edges
2. `useAuth()` - 40 edges
3. `useToast()` - 32 edges
4. `react` - 32 edges
5. `playerName()` - 22 edges
6. `resolveMediaUrl()` - 21 edges
7. `ApiError` - 18 edges
8. `decodeProto()` - 12 edges
9. `postProto()` - 11 edges
10. `encode_protobuf()` - 11 edges

## Surprising Connections (you probably didn't know these)
- `AdminPage()` --calls--> `useAuth()`  [EXTRACTED]
  FrontEnd/src/pages/AdminPage.jsx → FrontEnd/src/features/auth/context/AuthContext.jsx
- `updateMyProfile()` --calls--> `apiFetch()`  [EXTRACTED]
  FrontEnd/src/features/dashboard/services/playerApi.js → FrontEnd/src/services/api/client.js
- `AvatarWithFallback()` --calls--> `resolveMediaUrl()`  [EXTRACTED]
  FrontEnd/src/pages/LeaderboardPage.jsx → FrontEnd/src/utils/mediaUrl.js
- `get_player_stats()` --calls--> `APIError`  [INFERRED]
  free fire api/Api/InGame.py → free fire api/app.py
- `get_player_stats()` --calls--> `ProtobufError`  [INFERRED]
  free fire api/Api/InGame.py → free fire api/app.py

## Import Cycles
- None detected.

## Communities (114 total, 4 thin omitted)

### Community 0 - "Community 0"
Cohesion: 0.05
Nodes (75): AdminPage, MemberDetailsPage, NotificationsPage, SkeletonProfile(), ActivityTab(), truncate(), GAMES, GuildPlayersTab() (+67 more)

### Community 1 - "Community 1"
Cohesion: 0.04
Nodes (46): dependencies, bcrypt, cookie-parser, cors, dotenv, express, express-rate-limit, google-auth-library (+38 more)

### Community 2 - "Community 2"
Cohesion: 0.09
Nodes (36): addPlayerByGameUid(), ADMIN_ROLES, assignRole(), autoCancelExpiredActions(), bcrypt, ChangeLog, claimLeadership(), completeTransfer() (+28 more)

### Community 3 - "Community 3"
Cohesion: 0.08
Nodes (20): App(), GuildPage, LeaderboardPage, MembersPage, ReelPage, ProtectedRoutes(), FullPageSkeleton(), Skeleton() (+12 more)

### Community 4 - "Community 4"
Cohesion: 0.06
Nodes (34): framer-motion, dependencies, framer-motion, react, react-dom, react-icons, react-router-dom, socket.io-client (+26 more)

### Community 5 - "Community 5"
Cohesion: 0.07
Nodes (25): mongoose, errorHandler(), notFound(), bcrypt, mongoose, userSchema, allowedOrigins, app (+17 more)

### Community 6 - "Community 6"
Cohesion: 0.15
Nodes (25): Exception, get_garena_token(), get_major_login(), Perform major login with the provided credentials Args: logintoken (str): The…, Get Garena token using uid and password Args: uid (str): User ID password…, get_player_personal_show(), get_player_stats(), Perform a fuzzy account search by keyword. Args: server_url (str): Base URL of… (+17 more)

### Community 7 - "Community 7"
Cohesion: 0.09
Nodes (25): applyToGuild(), ChangeLog, disbandGuild(), getGuildProfile(), getPrivateGuildView(), Guild, GUILD_ADMIN_ROLES, GuildPlayer (+17 more)

### Community 8 - "Community 8"
Cohesion: 0.14
Nodes (22): GalleryPage, MediaCard(), SkeletonMediaGrid(), MediaTab(), GalleryPage(), IMAGE_EXTENSIONS, IMAGE_MIMES, validateMediaFile() (+14 more)

### Community 9 - "Community 9"
Cohesion: 0.11
Nodes (19): { encodeProto, decodeProto, postExpectContinue, postForm, safeJson }, {
  GARENA_TOKEN_URL,
  MAJOR_LOGIN_URL,
  CLIENT_SECRET,
  CLIENT_ID,
  RELEASEVERSION,
  DEBUG,
}, getGarenaToken(), { MajorLogin }, searchClanByName(), ACCOUNT_KEYS, ACCOUNTS, CLIENT_ID (+11 more)

### Community 10 - "Community 10"
Cohesion: 0.14
Nodes (23): cacheGet(), cacheSet(), CLAN_ACTIVITY_TYPE, { encodeProto, decodeProto, postExpectContinue }, enrichPlayers(), getClanMainPageInfo(), getClanOfficers(), getGuildMembers() (+15 more)

### Community 11 - "Community 11"
Cohesion: 0.19
Nodes (17): AppRoutes(), BottomNavbar(), navItems, DesktopNavbar(), navItems, useUnreadCount(), MobileHeader(), Navbar() (+9 more)

### Community 12 - "Community 12"
Cohesion: 0.09
Nodes (22): author, bugs, url, description, devDependencies, nodemon, engines, node (+14 more)

### Community 13 - "Community 13"
Cohesion: 0.13
Nodes (20): addComment(), getGallery(), getLimit(), getMyMedia(), getPendingForAdmin(), Media, moderateMedia(), mongoose (+12 more)

### Community 14 - "Community 14"
Cohesion: 0.10
Nodes (17): { ACCOUNTS, RATE_LIMIT_MAX, RATE_LIMIT_WINDOW_MS }, { ApiError }, app, authenticate(), cors, crypto, doLogin(), express (+9 more)

### Community 15 - "Community 15"
Cohesion: 0.10
Nodes (20): ADMIN_ROLES, bcrypt, ChangeLog, detectGuildStatus(), DUMMY_BCRYPT_HASH, { emitPlayerStatsUpdate, emitPlayerProfileUpdate }, GAMES, generateToken() (+12 more)

### Community 16 - "Community 16"
Cohesion: 0.15
Nodes (11): EnterUidRegionPage, OnboardingPage, ToastDemoPage, useToast(), completeOnboarding(), submitUidRegion(), EnterUidRegionPage(), REGIONS (+3 more)

### Community 17 - "Community 17"
Cohesion: 0.13
Nodes (15): getNotifications(), getUnreadCount(), markRead(), Notification, jwt, Membership, protect(), requireRole() (+7 more)

### Community 18 - "Community 18"
Cohesion: 0.15
Nodes (11): ProfilePage, PasswordInput(), usePlayerProfile(), getMyProfile(), updateMyProfile(), usePlayerStatsSocket(), AVATAR_EXTENSIONS, AVATAR_MIMES (+3 more)

### Community 19 - "Community 19"
Cohesion: 0.19
Nodes (14): clampPercent(), computeTotals(), getGuildLeaderboard(), getPlayerLeaderboard(), Guild, Membership, num(), PlayerProfile (+6 more)

### Community 20 - "Community 20"
Cohesion: 0.17
Nodes (13): getMajorLogin(), aesCbcDecrypt(), aesCbcEncrypt(), ApiError, crypto, decodeProto(), encodeProto(), https (+5 more)

### Community 21 - "Community 21"
Cohesion: 0.20
Nodes (7): ModeStatsCard(), PlayerIdCard(), RankingCard(), SeasonStatsSection(), MediaPreviewCard(), API_ORIGIN, resolveMediaUrl()

### Community 22 - "Community 22"
Cohesion: 0.18
Nodes (13): { emitPlayerStatsUpdate, emitPlayerProfileUpdate }, getMyProfile(), Guild, Membership, PlayerProfile, syncProfileFromMembership(), updateMyProfile(), validateSeasonStats() (+5 more)

### Community 23 - "Community 23"
Cohesion: 0.14
Nodes (13): changePassword(), checkGuildUid(), deleteAccount(), logout(), verifyLeaderPassword(), authBotPrevention, { authLimiter }, { botPrevention } (+5 more)

### Community 24 - "Community 24"
Cohesion: 0.20
Nodes (13): edge, EDGE_CANDIDATES, edgeProc, evaluate(), { execFileSync, spawn }, fs, getJson(), main() (+5 more)

### Community 25 - "Community 25"
Cohesion: 0.18
Nodes (10): LIMITS, MIME_TYPES, path, crypto, memory, multer, path, upload (+2 more)

### Community 26 - "Community 26"
Cohesion: 0.18
Nodes (10): DEFAULT_MEMBERS, getMemberById(), getMembers(), GuildMember, mongoose, guildMemberSchema, mongoose, express (+2 more)

### Community 27 - "Community 27"
Cohesion: 0.19
Nodes (12): getPlayerPersonalShow(), getPlayerRank(), splitPasses(), BR_BY_ID, BR_TIERS, CS_BY_ID, CS_STAR_TIERS, CS_TIERS (+4 more)

### Community 28 - "Community 28"
Cohesion: 0.26
Nodes (8): isMobile(), Toast(), ToastContainer(), ToastContext, ToastProvider(), MAX_VISIBLE_TOASTS, TOAST_COLORS, TOAST_DURATIONS

### Community 29 - "Community 29"
Cohesion: 0.27
Nodes (10): analyzeBehavior(), botPrevention(), checkHoneypot(), crypto, fingerprintStore, generateFingerprint(), HONEYPOT_FIELDS, isSuspiciousFingerprint() (+2 more)

### Community 30 - "Community 30"
Cohesion: 0.22
Nodes (9): addRates(), authHeaders(), getPlayerStats(), postProto(), searchAccountByKeyword(), setPlayerGalleryShowInfo(), { ACCOUNTS }, { getGarenaToken, getMajorLogin } (+1 more)

### Community 31 - "Community 31"
Cohesion: 0.22
Nodes (8): plugins, rules, react/only-export-components, react/rules-of-hooks, $schema, oxc, typescript, warn

### Community 32 - "Community 32"
Cohesion: 0.36
Nodes (6): LoginForm(), isMobileDevice(), loadGsiScript(), SocialLogin(), googleLogin(), AuthPage()

### Community 33 - "Community 33"
Cohesion: 0.29
Nodes (7): requestOrigin(), resubmitMedia(), uploadAvatar(), uploadMedia(), persistValidatedFile(), membershipSchema, mongoose

### Community 34 - "Community 34"
Cohesion: 0.38
Nodes (7): completeOnboarding(), createGuild(), getMe(), serializeUser(), submitUidRegion(), emitPlayerProfileUpdate(), emitPlayerStatsUpdate()

### Community 36 - "Community 36"
Cohesion: 0.70
Nodes (4): detectFileType(), matches(), startsWithAscii(), validateUploadedFile()

### Community 37 - "Community 37"
Cohesion: 0.40
Nodes (4): app, express, path, NOTE: the page HTML is a template literal; String.raw keeps \n escapes intact

### Community 38 - "Community 38"
Cohesion: 0.50
Nodes (3): authLimiter, rateLimit, writeLimiter

## Knowledge Gaps
- **281 isolated node(s):** `GAMES`, `STATUS_FILTERS`, `TYPE_LABEL`, `MOCK_PLAYER`, `tabs` (+276 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **4 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `apiFetch()` connect `Community 0` to `Community 32`, `Community 3`, `Community 8`, `Community 11`, `Community 16`, `Community 18`?**
  _High betweenness centrality (0.022) - this node is a cross-community bridge._
- **Why does `react` connect `Community 11` to `Community 0`, `Community 32`, `Community 3`, `Community 8`, `Community 16`, `Community 18`, `Community 21`, `Community 28`, `Community 31`?**
  _High betweenness centrality (0.014) - this node is a cross-community bridge._
- **Why does `getMemberById()` connect `Community 26` to `Community 33`?**
  _High betweenness centrality (0.008) - this node is a cross-community bridge._
- **What connects `GAMES`, `STATUS_FILTERS`, `TYPE_LABEL` to the rest of the system?**
  _281 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `Community 0` be split into smaller, more focused modules?**
  _Cohesion score 0.05412371134020619 - nodes in this community are weakly interconnected._
- **Should `Community 1` be split into smaller, more focused modules?**
  _Cohesion score 0.043478260869565216 - nodes in this community are weakly interconnected._
- **Should `Community 2` be split into smaller, more focused modules?**
  _Cohesion score 0.08636977058029689 - nodes in this community are weakly interconnected._