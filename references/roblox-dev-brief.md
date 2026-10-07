# Roblox Pro-Tier Developer Research Brief
**As of:** Wed Oct 7, 2026 (Asia/Calcutta)  
**Scope:** Factual, actionable inputs for a pro-tier Roblox developer assistant roadmap  
**Method:** Prefer create.roblox.com / Creator Hub / DevForum / Luau.org / Rojo docs; third-party charts labeled as such

---

## Executive summary
- **Platform is retention-first in 2026:** Recommended For You now weights **D1 / D2–7 / D8–28** play days, playtime, co-play, qualified sessions, and spend — not just clicky thumbnails. Ads can seed consideration; **organic RFY ranking uses only Home-recommendation cohorts**. ([discovery docs](https://create.roblox.com/docs/discovery), [newsroom Jun 15 2026](https://about.roblox.com/newsroom/2026/06/optimizing-discovery-great-games-reach-millions-players-roblox))
- **What’s hot:** Simulation/“brainrot” collectibles, long-lived RP (Brookhaven, Adopt Me!), survival/horror-adjacent (99 Nights…), anime action RPG (Blox Fruits), shooters (RIVALS), dress-up/avatar social. Official taxonomy is **core-loop genres** (Action, Simulation, Survival, etc.), not themes like “horror.” ([genres](https://create.roblox.com/docs/production/publishing/experience-genres); concurrent snapshot ~Oct 6 2026 via third-party chart mirror — treat CCU numbers as approximate)
- **Money stack changed:** Passes = **70%** of Robux spent to you; Creator Rewards (Jul 24 2025) replaced Engagement-Based/Premium payouts — **5 Robux** when an Active Spender plays 10+ min in one of their first 3 experiences that day; Audience Expansion = **35%** of first $100 Qualifying Purchases for attributed new/reactivated users (extra eligibility). DevEx: **≥30k Earned Robux**, standard **$0.0038**/Robux (~$114/30k); U.S. 18+ rate **$0.0054** on eligible purchases since **Jun 8 2026**. ([monetize](https://create.roblox.com/docs/monetize-experiences), [creator rewards](https://create.roblox.com/docs/creator-rewards), [DevEx](https://create.roblox.com/docs/production/monetization/developer-exchange), [18+](https://create.roblox.com/docs/production/monetization/18-plus-devex-rate))
- **Tech floor for “pro”:** Luau + client-server remotes + server-authoritative DataStores (ProfileStore-class session locking) + multi-client/mobile testing; optional Rojo/Git/Wally for teams. Never trust the client. ([security](https://create.roblox.com/docs/scripting/security/security-tactics), [remotes](https://create.roblox.com/docs/scripting/events/remote), [ProfileStore](https://github.com/MadStudioRoblox/ProfileStore), [Rojo](https://rojo.space/docs/v7/))
- **Best first serious project:** Ship a **small, tight core loop** (collector/obby-platformer or round-based minigame) via official Core curriculum → add persistence + one Game Pass → soft launch with accurate metadata + thumbnail personalization → iterate on D1 retention/bounce before genre chasing.

---

## Hot games / genres (2025–2026)

### Official genre system
Roblox discovery Charts use a **genre + optional subgenre** taxonomy (set in Creator Hub; changeable **once per 3 months**). Genres describe **core loop**, not theme. Examples: Action (Battlegrounds & Fighting), Simulation (Tycoon, Incremental, Idle), Survival (1 vs All, Escape), Roleplay & Avatar Sim (Life, Dress Up, Pet Care), Shooter, RPG, Obby & Platformer, Party & Casual, Strategy (Tower Defense), etc. ([genres docs](https://create.roblox.com/docs/production/publishing/experience-genres), [DevForum genre rollout](https://devforum.roblox.com/t/now-live-update-your-genre-and-subgenre/3265896))

**Charts surface:** “Top Playing Now” = real-time **CCU** sort (distinct from older “Popular” which is **not** pure CCU). ([Top Playing Now announcement](https://devforum.roblox.com/t/introducing-top-playing-now-on-charts/3529809))

### Representative hits (why they work) — approximate CCU from third-party Top Playing Now mirror ~Oct 6 2026
| Experience (examples) | Typical why-it-works | Notes |
|---|---|---|
| Steal An Egg / Steal a Brainrot–style sims | Ultra-clear hook, collectible progression, meme/cultural “brainrot” virality, frequent updates | Simulation; high CCU but trendy — **do not copy blindly**; differentiation + retention matter more in 2026 RFY |
| Brookhaven RP, Adopt Me! | Social sandbox + identity/pets, years of update cadence, friend co-play | Roleplay & Avatar Sim — hard to displace; mid-tier RP still cited as opportunity in community market reports |
| Murder Mystery 2 | Clear asymmetric roles, short rounds, social spectate | Survival / 1-vs-all archetype |
| 99 Nights in the Forest | Horror-adjacent survival loop, tension + progression | Theme lives under Survival/Action/Adventure genres |
| Blox Fruits | Anime combat + grinding RPG progression, content roadmap | RPG / Action RPG |
| RIVALS | Competitive shooter feel, high rating, skill expression | Shooter |
| Dress To Impress | Fashion/social competition, UGC culture, shareable moments | Roleplay & Avatar Sim / Dress Up |

**Caveat:** Exact CCU/visit figures from non-Roblox chart scrapers are **unverified**; use Creator Hub Charts / Top Playing Now live for decisions. Platform scale cited by Roblox: **~132M DAU** (Q1 2026). ([newsroom](https://about.roblox.com/newsroom/2026/06/optimizing-discovery-great-games-reach-millions-players-roblox))

### Monetization norms (high-level)
| Lever | Rule of thumb (official) |
|---|---|
| **Passes** | One-time privileges; **you earn 70%** of Robux spent on your own passes (affiliate sell of others’: 10% you / 60% original) |
| **Developer products** | Consumables / repeat buys (currency, ammo) |
| **Subscriptions / private servers / paid access** | Recurring or gate access |
| **Creator Rewards – Daily Engagement** | **5 Robux**/day when Active Spender (≥$9.99 Qualifying Purchases in last 60 days, not new/reactivated in last 60) plays **≥10 min** and experience is among **first 3** they launch that day. Live since **Jul 24 2025**. 60-day hold on awards. |
| **Creator Rewards – Audience Expansion** | **35%** of first **$100** Qualifying Purchases (anywhere on platform) for attributed New/Reactivated users; needs ID-verified + DevEx account + other conditions (incl. experience DAU thresholds in framework). |
| **DevEx** | Min **30,000** Earned Robux; **1 cash-out/calendar month**; standard **0.0038 USD**/Robux; legacy pre–Sep 5 2025 balances at **0.0035**; U.S. 18+ **0.0054** on eligible pass/dev product/sub/private-server earnings from age-verified U.S. 18+ players (R15/character eligibility rules) since **Jun 8 2026**. |

Former **Engagement-Based Payouts / Premium Payouts / Creator Affiliate** → **discontinued**, replaced by Creator Rewards. ([creator rewards](https://create.roblox.com/docs/creator-rewards), [DevForum live post](https://devforum.roblox.com/t/creator-rewards-is-live/3838257/1))

### Discovery / algorithm (public)
**Two stages:** Retrieval (consideration set) → Ranking (personalized order).  
**Ads/friends/search/charts can get you into consideration**; **RFY ranking signals are computed only on users acquired from Home recommendations** — ad/friend/social traffic does **not** boost RFY rank metrics. ([discovery](https://create.roblox.com/docs/discovery))

**Signal priority (Creator docs, post–Jun 2026 28-day expansion):**
1. **Most important:** Play-through rate; first-play bounce (&lt;60s, 61–180s); play days & playtime per user across **D1, D2–7, D8–28** (playtime capped 60 min/user/game/day in signal).
2. **Important:** Intentional co-play days; qualified play sessions; spend days; Robux spent per user.

**Quality filters that hurt exposure:** giveaway/Robux-bait titles, mismatched metadata vs gameplay, non-unique clones. ([discovery](https://create.roblox.com/docs/discovery))  
**Sponsored Experiences:** Ads Manager; tests blended Sponsored into RFY (labeled); **ad performance should not change organic RFY rank**. ([DevForum sponsored-in-RFY](https://devforum.roblox.com/t/upcoming-tests-sponsored-experiences-to-appear-within-recommended-for-you-on-home/3938575))

---

## Studio & tech stack

### Install / entry
- Download Studio from Creator Hub; Windows `RobloxStudio.exe` / Mac `RobloxStudio.dmg`; Win10+/macOS 10.14+ min, 8 GB RAM recommended. ([install Studio](https://create.roblox.com/docs/tutorials/curriculums/studio/install-studio))
- Free IDE = engine + client emulator + publish pipeline + in-Studio **Assistant**. ([experiences overview](https://create.roblox.com/docs/experiences))

### Experience vs place
- **Experience (game)** = published product players join.  
- **Place** = one 3D world/data model; start place loads first; more places = hubs/areas (teleports). Place upload size soft limit **~100 MB**. ([publish experiences/places](https://create.roblox.com/docs/production/publishing/publish-experiences-and-places))

### Studio UI mental model
| Panel | Role |
|---|---|
| **Explorer** | Hierarchy of the open place’s DataModel (Workspace, ServerScriptService, ReplicatedStorage, etc.) |
| **Properties** | Per-instance config |
| **Toolbox / Creator Store** | Models, audio, meshes, plugins; Asset Manager for game-local imports |
| **Viewport** | Build + playtest |

Default containers: **Workspace** (world), **ServerScriptService** (server-only scripts — keep secrets/logic here), **ReplicatedStorage** (shared modules/remotes), **StarterGui/PlayerScripts** (client). ([first experience tutorial](https://create.roblox.com/docs/tutorials/first-experience))

### Default Studio vs Rojo
| Default Studio | Rojo (+ VS Code/Git) |
|---|---|
| Fine for solo learning, greyboxing, small games | Pro/team: filesystem `.luau`, Git PRs, Selene/StyLua, Wally packages, luau-lsp |
| Scripts live in place file | Sync disk ↔ Studio; version control friendly |

Rojo = open-source project sync for professional tooling. ([Rojo docs](https://rojo.space/docs/v7/))

### Luau vs older Lua
- Roblox language = **Luau** (Lua 5.1–compatible + gradual typing, string interpolation, generalized iteration, Roblox APIs). Prefer `--!strict` + type annotations as skill grows. ([Luau Creator docs](https://create.roblox.com/docs/luau), [type checking](https://create.roblox.com/docs/luau/type-checking), [luau.org compatibility](https://luau.org/compatibility/))

### Client–server & remotes
- Multiplayer by default. **RemoteEvent** = one-way; **RemoteFunction** = request/response (avoid server→client Invoke when possible — disconnect/hang risk); **UnreliableRemoteEvent** = lossy/high-freq. Remotes in ReplicatedStorage (or shared container). ([remotes](https://create.roblox.com/docs/scripting/events/remote))
- **Never trust client:** validate types, ranges, ownership, cooldowns **on server**; critical economy/combat/progression server-authoritative. ([security tactics](https://create.roblox.com/docs/scripting/security/security-tactics))

### DataStore / ProfileStore (high level)
- **DataStoreService** = persistent cloud data per experience; **server Scripts only**; wrap calls in `pcall`; respect budgets. Enable Studio API access only on **test** experiences to avoid prod overwrite. ([data stores](https://create.roblox.com/docs/cloud-services/data-stores))
- **ProfileStore** (MadStudio, community standard) = session-locked player profiles (UpdateAsync + MessagingService) to prevent dupe/loss across servers — typical pro pattern vs raw SetAsync. ([ProfileStore GitHub](https://github.com/MadStudioRoblox/ProfileStore), [tutorial](https://madstudioroblox.github.io/ProfileStore/tutorial/))

### Packages / assets / publishing
- Cloud assets via `rbxassetid://…`; packages = versioned reusable hierarchies across places/games (Get Latest / AutoUpdate). Moderation before live visibility. ([assets](https://create.roblox.com/docs/projects/assets))
- Publish → Creator Hub versioning/history; configure genre, icon, thumbnails, maturity/compliance questionnaire.

### Official learning paths (URLs)
| Path | URL |
|---|---|
| Tutorials hub | https://create.roblox.com/docs/tutorials |
| Get started / templates (Platformer, Laser Tag, Racing) | https://create.roblox.com/docs/experiences |
| **Core curriculum** (greybox → script → polish platformer) | https://create.roblox.com/docs/tutorials/curriculums/core |
| Advanced curricula (env art, gameplay scripting, UI) | https://create.roblox.com/docs/tutorials/curriculums/curriculum-overview |
| Install Studio | https://create.roblox.com/docs/tutorials/curriculums/studio/install-studio |
| Education / lesson plans | https://about.roblox.com/education |
| Creator Hub (dashboard) | https://create.roblox.com/ |
| Docs home | https://create.roblox.com/docs |

---

## Build pipeline (idea → iterate)

| Stage | Do this | Exit criteria |
|---|---|---|
| **1. Idea** | Pick **one** core verb (collect, survive round, dress/compete, shoot). Check genre fit + differentiation vs Charts clones. | One-sentence loop + target session length |
| **2. Prototype** | Studio template or Core curriculum greybox; no monetization; playtest with friends | Fun in &lt;2 minutes without tutorial walls |
| **3. Core loop** | Server-authoritative scoring/inventory; remotes for input only | Repeatable session; clear win/progress feedback |
| **4. Progression** | Soft currency, unlocks, leaderboards; DataStore/ProfileStore | Return reason tomorrow (D1 hook) |
| **5. Monetization** | 1–3 ethical Passes (convenience/cosmetics/speed — not pay-to-ruin); optional Creator Rewards awareness | Purchase UX server-validated (`ProcessReceipt` for products) |
| **6. Polish** | Lighting, SFX, UI scale for phone; onboarding; bounce &lt;60s reduction | Device Simulator + real phone pass |
| **7. Soft launch** | Publish public; accurate title/desc/genre; 2–5 thumbnails + personalization; friends + Discord | Stable D1 retention vs similar-game benchmarks in Analytics |
| **8. Iterate** | Weekly content or balance; watch Home Recommendations signals; events | RFY explore→expand after update spikes |

**Starter templates:** Platformer / Laser Tag / Racing from Studio + Core curriculum place files. ([experiences](https://create.roblox.com/docs/experiences), [core](https://create.roblox.com/docs/tutorials/curriculums/core))

---

## Growth playbook

### On-platform
- **Thumbnails:** 16:9, ideally **1920×1080**; up to 10 images/videos on detail page; Home personalization needs **2–5 active** thumbs — optimize **qualified play-through**, not clickbait. Official testing: avg **+8.5%** QPTR (some +50%). Keep multiple winners live; don’t kill variants early. Avoid critical text at bottom (player-count overlay). ([thumbnails](https://create.roblox.com/docs/production/publishing/thumbnails), [staff tips thread](https://devforum.roblox.com/t/5-tips-from-roblox-staff-to-get-the-most-out-of-thumbnail-personalization/3471689/1))
- **Title/description/genre:** Accurate, unique, no Robux/giveaway bait; pick correct genre/subgenre for Charts sorts. ([discovery best practices](https://create.roblox.com/docs/discovery), [genres](https://create.roblox.com/docs/production/publishing/experience-genres))
- **SEO/tags/search:** Semantic search exists (“food games”); relevance + metadata integrity; mismatched content suppressed. ([discovery](https://create.roblox.com/docs/discovery))
- **Sponsored Experiences / Search ads / Ads Manager:** Buy consideration; monitor Acquisition sources; don’t expect ads to inflate RFY organic rank. ([acquisition](https://create.roblox.com/docs/production/analytics/acquisition), [monetize ads](https://create.roblox.com/docs/monetize-experiences))
- **Events / notifications / groups:** Experience Events + Community Groups + notifications for re-engagement. ([discovery](https://create.roblox.com/docs/discovery))
- **Update cadence:** Cultural/tentpole updates; RFY “explore” after content drops if new cohorts retain. Co-play/invites are explicit algorithm signals.
- **Friend invites / intentional co-play:** Design for join-friends and return-together — weighted in RFY.

### Off-platform (what creators report works, 2025–2026)
- **TikTok / YouTube Shorts:** 7–15s of **real core loop** (not fake graphics); watermark/share link; authenticity matches video-thumbnail policy direction.
- **Discord:** Patch notes, playtests, bug reports — community retention → co-play.
- **Influencers / Share Links:** Relevant for Audience Expansion attribution when users are new/lapsed; follow Creator Rewards anti-fraud rules (no alts/bots). ([creator rewards](https://create.roblox.com/docs/creator-rewards))

**Creator consensus theme (aligns with official 2026 RFY):** Retention & honesty beat thumbnail bait; clones and bait get suppressed; long-term play + friends + fair monetization win distribution.

---

## Pitfalls & pro habits

| Pitfall | Pro habit |
|---|---|
| Client-trusted currency/damage/purchases | Server authority; validate remotes; rate-limit; `ProcessReceipt` for products ([security](https://create.roblox.com/docs/scripting/security/security-tactics)) |
| Free models with backdoors | Vet Toolbox assets; prefer own/Creator Store reputable |
| DataStore race/dupe | Session-locked profiles (ProfileStore-class); `pcall` + retries |
| Solo playtest only | Studio **Server & Clients** (multi-client); Network Simulator; real devices ([testing modes](https://create.roblox.com/docs/studio/testing-modes)) |
| Desktop-only UI | Device Simulator; touch targets; scale with `UDim2`; test low-end phones ([device simulator](https://create.roblox.com/docs/studio/device-simulator)) |
| Laggy maps / unoptimized meshes | Streaming, LODs, few moving parts, profile MicroProfiler |
| Genre/theme confusion / clone metadata | Accurate genre; unique art+title; no bait ([discovery](https://create.roblox.com/docs/discovery)) |
| Kids-platform ToS violations | Community Standards, maturity questionnaire, age-appropriate content; no gambling-adjacent for kids; privacy-aware ([safety docs](https://create.roblox.com/docs/safety), [Community Standards / ToU](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use), [Safety Center](https://about.roblox.com/safety)) |
| Farming Creator Rewards | Bots/alts/teleport abuse → forfeit/ban ([creator rewards](https://create.roblox.com/docs/creator-rewards)) |

---

## Recommended first 30 days

**Single best first project (serious beginner → pro habits):**  
A **coin-collect / jump-power platformer** (official Core curriculum loop) **or** a **3–5 minute round-based party/survival minigame** — small map, one progression currency, one cosmetic Game Pass, ProfileStore (or solid DataStore tutorial) for coins/wins, mobile-friendly HUD. Avoid open-world RP, anime fighter, or brainrot clone as v1.

### Learning order (dense)
| Days | Focus |
|---|---|
| **1–3** | Install Studio; Explorer/Properties; Baseplate → publish private; complete “create first experience” / templates |
| **4–10** | **Core curriculum** Ch.1–2 (greybox + scripting + remotes mindset); Luau basics + `--!strict` intro |
| **11–14** | Client–server security pass; DataStores tutorial → add ProfileStore; multi-client test |
| **15–18** | UI on Device Simulator; polish lighting/VFX (Core Ch.3); one Pass + receipt validation |
| **19–22** | Metadata, icon, 3–5 thumbnails + personalization; genre; soft public launch |
| **23–30** | Analytics: Acquisition + Home Recommendations; fix bounce/D1; Discord + 2 short social clips; optional Rojo+Git if going team/pro |
| **After 30** | Advanced curriculum (gameplay scripting / UI); genre specialization; Ads only after retention is competitive |

---

## Source links (primary + key secondary)

### Official Creator Hub / docs
- https://create.roblox.com/docs  
- https://create.roblox.com/docs/experiences  
- https://create.roblox.com/docs/tutorials  
- https://create.roblox.com/docs/tutorials/curriculums/core  
- https://create.roblox.com/docs/tutorials/curriculums/curriculum-overview  
- https://create.roblox.com/docs/tutorials/curriculums/studio/install-studio  
- https://create.roblox.com/docs/production/publishing/experience-genres  
- https://create.roblox.com/docs/production/publishing/publish-experiences-and-places  
- https://create.roblox.com/docs/production/publishing/thumbnails  
- https://create.roblox.com/docs/discovery  
- https://create.roblox.com/docs/production/analytics/acquisition  
- https://create.roblox.com/docs/monetize-experiences  
- https://create.roblox.com/docs/creator-rewards  
- https://create.roblox.com/docs/production/monetization/developer-exchange  
- https://create.roblox.com/docs/production/monetization/18-plus-devex-rate  
- https://create.roblox.com/docs/cloud-services/data-stores  
- https://create.roblox.com/docs/scripting/events/remote  
- https://create.roblox.com/docs/scripting/security/security-tactics  
- https://create.roblox.com/docs/luau  
- https://create.roblox.com/docs/projects/assets  
- https://create.roblox.com/docs/studio/testing-modes  
- https://create.roblox.com/docs/safety  

### Roblox corporate / education
- https://about.roblox.com/newsroom/2026/06/optimizing-discovery-great-games-reach-millions-players-roblox  
- https://about.roblox.com/education  
- https://about.roblox.com/safety  

### DevForum announcements
- https://devforum.roblox.com/t/creator-rewards-is-live/3838257/1  
- https://devforum.roblox.com/t/recommended-for-you-algorithm-improvements-that-better-value-long-term-retention/4684575/1  
- https://devforum.roblox.com/t/introducing-top-playing-now-on-charts/3529809  
- https://devforum.roblox.com/t/now-live-update-your-genre-and-subgenre/3265896  
- https://devforum.roblox.com/t/upcoming-tests-sponsored-experiences-to-appear-within-recommended-for-you-on-home/3938575  
- https://devforum.roblox.com/t/5-tips-from-roblox-staff-to-get-the-most-out-of-thumbnail-personalization/3471689/1  

### Tooling / community standards (non-Roblox-owned but industry standard)
- https://rojo.space/docs/v7/  
- https://luau.org/compatibility/  
- https://github.com/MadStudioRoblox/ProfileStore  
- https://madstudioroblox.github.io/ProfileStore/tutorial/  

### Third-party (use cautiously; not authoritative stats)
- Charts mirrors / market threads for directional “what’s hot” only — always verify live on Roblox Charts / Creator Hub.

---

## Uncertainties / do-not-invent notes
- Exact live CCU, revenue shares for specific games, and “average ad CPA” are **not** asserted here from official docs.  
- Community “Market Friday” opportunity scores are **unofficial**.  
- Creator Rewards formulas and DevEx rates **can change** — re-check linked docs before productizing advice.  
- U.S. 18+ DevEx character eligibility is detailed and easy to break with R6 allowed — read the 18+ page before promising higher rates.
