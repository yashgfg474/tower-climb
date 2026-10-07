# Week-1 MVP — What to Build

## Goal
Playable public-or-private experience: a party can climb **one tower**, fight, cash out or continue, beat or die to **one boss**, in **under ~20 minutes**.

## In scope
| System | Spec |
|---|---|
| Party | 1–4 players |
| Weapons | 1 melee + 1 ranged |
| Powers | A few (small set, readable) |
| Floors | 4–6 + 1 boss |
| Tower | **One** |
| Meta UI | Cash-out / climb decision after floor |
| Combat | Real-time; server-authoritative |
| Social | Dead players **spectate** |
| Onboarding | First 60s = action (minimal lobby) |
| Persistence | Optional light for week-1; don’t block fun if saves slip — prefer simple win/loot stats if time |
| Monetization | **None** that gates first win |

## Out of scope (week 1)
- Multiple towers / seasons
- Difficulty tiers
- Weekly leaderboards
- Heist mode
- Daily seeded tower
- Passes / products / cosmetics
- Huge ability trees or gun catalogs

## Build path (roles)
1. **User:** Roblox Studio on laptop; playtest; publish.
2. **game dev:** Luau systems — combat, floors, UI, DataStores when needed, shipping path.
3. **roblox game dev (RGD):** Design judgment, trend checks, metadata/growth advice when soft-launching.

## Suggested Studio order
1. Greybox vertical floors + spawn + floor clear trigger  
2. Melee hit + ranged projectile (server validates)  
3. Cash-out / climb UI + loot stub  
4. Random upgrade picker (3 options, pick 1)  
5. Boss placeholder + win/lose  
6. Party + spectate  
7. Polish pass: mobile HUD, death feedback, extract screen  

## Definition of done
- [ ] Solo and 2+ player run completable  
- [ ] Cash-out works and ends run with loot shown  
- [ ] Climb can wipe and still feels fair  
- [ ] Boss reachable  
- [ ] Spectate on death  
- [ ] Playable on phone resolution  
