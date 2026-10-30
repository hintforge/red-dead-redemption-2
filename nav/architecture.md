# Red Dead Redemption 2 -- Architecture

**status:** research-integrated <!-- scaffold | research-integrated | live-observed | reconciled -->
**last_reconciled:** 2026-10-30
**research_run:** P1 2026-10-30; P2 2026-10-30 (each a single deep-research result, no second tool to compare against)

Cross-zone structural primitives. The persona reads this file for all cross-zone reasoning -- lookahead warnings (Rule 2), backtrack queries (Rule 3), reachability checks (Rule 4), locks-and-keys notifications (Rule 5). Per-zone gate lists live in `nav/<zone>.md` (created at P2) and reference this file's graph by edge ID. Drift between this file and per-zone files is a bug; run a consistency pass after each ingestion.

## Hintforge manifest

<!-- Read by the reader at session start (see docs/corpus-format.md §3). Bump corpus-core-version only when a change to docs/corpus-format.md would break an older reader; see the Versioning subsection in that doc. game-version-* fields describe the game build the corpus was authored against (player-supplied at setup; required as of v3); they are orthogonal to corpus-core-version (which is the schema axis). -->

```
corpus-core-version: 6
game-version: "latest (Steam build 13773296)"
game-version-platform: "PC / Steam"
game-version-as-of: 2026-10-30
vector-extensions: npcs, factions, reputation
```

## Vector extensions

<!-- Wizard populates from Step 7 conditional-creation decisions. One entry per extension created. Reader uses this list to route topical questions to the right folder. -->

- `npcs/` -- named individual NPCs (any `entity-status`: hostile, friendly, convertible, party, neutral), indexed by `npcs/index.md`. Generic-mob combat content continues to route via the `enemy` vector to `mechanics.md` (no folder needed for that).
- `factions/` -- group entities the player has a relationship with (gangs, law enforcement, town powers), indexed by `factions/index.md`
- `reputation/` -- reputation tracks (Honor, bounty), indexed by `reputation/index.md`

## Zone Graph

**Game-type label:** open-world-explorative-only (one continuous five-state map; no instanced dungeons; interiors such as the cave behind the Elysian Pool waterfall are part of the open map)
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles ; https://www.powerpyx.com/red-dead-redemption-2-all-dinosaur-bones-locations/ (P1 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Confirmed: 3 sources, 1 language]

**Localization-mechanism class:** hybrid (map-system plus landmark): guides locate collectibles relative to the in-game map lettering ("north of the O in Ambarino"); treasure maps are landmark or picture puzzles. P1 corrects the earlier map-system guess. P2 found nothing showing the in-game map to be insufficient for orientation, so no `localization.md` toolkit is written.
_source: https://reddead.fandom.com/wiki/Dinosaur_Bones ; https://reddead.fandom.com/wiki/Dreamcatchers ; https://www.ign.com/wikis/red-dead-redemption-2/Treasure_Maps (P1 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Confirmed: 2 sources, 1 language]

**Entry node:** `rg_grizzlies_west` (Chapter 1 camp `cp_colter`, snowbound and scripted).
**Hub nodes:** none fixed; the gang camp moves between chapters (see Chapter ↔ Zone Mapping).
**Source-language set:** English (developer language). Official localizations also include Simplified and Traditional Chinese, French, German, Italian, Japanese, Korean, Polish, Brazilian Portuguese, Russian, Spanish and Latin American Spanish. The top three player-region languages were not measured; German and Spanish sources were read in P1, Russian was not.
_source: https://www.pcgamingwiki.com/wiki/Red_Dead_Redemption_2 (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Single source -- verify · class:community-wiki]

**Name collisions to keep apart** (guides reuse these words for different things):

- "Colter": the Chapter 1 title (`ch1_colter`), the abandoned mining town (`tn_colter`), and the mountain region it sits in (`rg_grizzlies_west`).
- "Horseshoe Overlook": the Chapter 2 title and the camp outside Valentine (`cp_horseshoe_overlook`).
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_

- Guides disagree on which state a landmark belongs to (Bluewater Marsh, Roanoke Ridge, Butcher Creek, Emerald Station, Grizzlies West). Key everything on the named landmark, not the state label.
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles ; https://www.powerpyx.com/red-dead-redemption-2-all-dinosaur-bones-locations/ ; https://www.gamepro.de/artikel/red-dead-redemption-2-fundorte-aller-legendaere-tiere-trapper-locations,3336448.html (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_ [Contradicted across sources -- see notes]

- "Lakay" is a settlement that holds collectible spots.
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 2 · puzzle-tier: 2 · category: mainline · spoiler: late-game_

- "Clemens Point" is a camp; "Clemens Cove" is the shore area name one overview text uses near Rhodes.
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 2 · puzzle-tier: 2 · category: mainline · spoiler: late-game_

- Chapter 4: the Fandom wiki titles it "Saint Denis"; its camp is Shady Belle, and the in-game Journal reportedly labels it "Shady Belle". "The Battle of Shady Belle" is a separate mission that ends Chapter 3.
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 2 · puzzle-tier: 2 · category: mainline · spoiler: late-game_

- "Lakay" is also a temporary camp (the same place, a different role), used between the island chapter and the next.
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_

- "Pronghorn Ranch" is a camp and a workplace in the epilogue, and unrelated to the Legendary Pronghorn animal.
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_

### Nodes

| id | name | kind | belongs to | tier |
|---|---|---|---|---|
| `st_new_hanover` | New Hanover | state | | none |
| `st_ambarino` | Ambarino | state | | none |
| `st_lemoyne` | Lemoyne | state | | none |
| `st_west_elizabeth` | West Elizabeth | state | | none |
| `st_new_austin` | New Austin | state | | none |
| `rg_heartlands`, `rg_cumberland_forest`, `rg_roanoke_ridge` | The Heartlands, Cumberland Forest, Roanoke Ridge | regions | New Hanover | none |
| `rg_grizzlies_west`, `rg_grizzlies_east` | Grizzlies West, Grizzlies East | regions | Ambarino | none |
| `rg_scarlett_meadows`, `rg_bayou_nwa`, `rg_bluewater_marsh` | Scarlett Meadows, Bayou Nwa, Bluewater Marsh | regions | Lemoyne | none |
| `rg_big_valley`, `rg_tall_trees`, `rg_great_plains` | Big Valley, Tall Trees, Great Plains | regions | West Elizabeth | none |
| `rg_cholla_springs`, `rg_rio_bravo`, `rg_gaptooth_ridge`, `rg_hennigans_stead` | Cholla Springs, Rio Bravo, Gaptooth Ridge, Hennigan's Stead | regions | New Austin | none |
| `tn_valentine`, `tn_annesburg`, `tn_emerald_ranch`, `tn_van_horn`, `tn_rhodes`, `tn_saint_denis`, `tn_lagras`, `tn_strawberry`, `tn_blackwater`, `tn_armadillo`, `tn_tumbleweed`, `tn_thieves_landing`, `tn_colter`, `tn_wapiti` | towns and settlements (Valentine, Annesburg, Emerald Ranch, Van Horn, Rhodes, Saint Denis, Lagras, Strawberry, Blackwater, Armadillo, Tumbleweed, Thieves Landing, Colter, Wapiti reservation) | towns | various | none |
| `pl_fort_wallace`, `pl_fort_mercer`, `pl_sisika`, `pl_manzanita_post`, `pl_macfarlanes_ranch`, `pl_elysian_pool`, `pl_flat_iron_lake` | named places | landmarks | various | none |
| `cp_colter` | Colter camp | camp, Chapter 1 | `rg_grizzlies_west` | none |
| `cp_horseshoe_overlook` | Horseshoe Overlook | camp, Chapter 2 | `rg_heartlands` | progression |
| `cp_clemens_point` | Clemens Point | camp, Chapter 3 | `rg_scarlett_meadows` | late-game |
| `cp_shady_belle` | Shady Belle | camp, Chapter 4 | `rg_bayou_nwa` | late-game |
| `cp_beaver_hollow` | Beaver Hollow | camp, Chapter 6 | `rg_roanoke_ridge` | late-game |
| `isl_guarma`, `tn_aguasdulces` | detached island and its town | story places | off the five-state map | story |
| `cp_lakay` | Lakay (transitional camp; the settlement holds collectible spots) | camp | `rg_bayou_nwa` near Lagras | story |
| `cp_pronghorn_ranch`, `cp_beechers_hope` | epilogue camps | camps | West Elizabeth (Beecher's Hope in Great Plains) | story |

_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 (navbox, P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Single source -- verify · class:community-wiki]

Map marker counts seen on one third-party map (marker counts, not verified in-game totals): 23 fast-travel markers, 10 train stations, 13 stagecoach markers, 7 camp markers, 13 gang hideouts, 45 stranger markers, 67 landmarks.
_source: https://rdr2map.com/ (P1 research 2026-10-30) · capture: browser_fetch · confidence: medium · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Single source -- verify · class:community-wiki]

### Edges

| ID | From | To | Type | Direction | Condition | Point of no return | Notes | tier |
|---|---|---|---|---|---|---|---|---|
| E1 | `cp_colter` | `cp_horseshoe_overlook` | story-gate | one-way | finish the mission "Eastward Bound" | chapter-bound | the Chapter 1 camp is never a camp again | progression |
| E2 | `cp_horseshoe_overlook` | `cp_clemens_point` | story-gate | one-way | finish "A Strange Kindness" (or skip ahead via "An American Pastoral Scene") | chapter-bound | Chapter 2 strands, companion activities and Chapter 2-only item requests expire | late-game |
| E3 | `cp_clemens_point` | `cp_shady_belle` | story-gate | one-way | finish "The Battle of Shady Belle" | chapter-bound | Chapter 3 strands expire | late-game |
| E4 | `cp_shady_belle` | `isl_guarma` | story-gate | one-way | finish "Banking, The Old American Art" | permanent | camp tithing box, item requests and companion activities end; the Give to the Poor, Errand Boy and Friends With Benefits windows close here | story |
| E5 | `isl_guarma` | `cp_lakay` | story-gate | one-way | finish the island missions | permanent | free roam on the island ends after two named missions; island-only animals become missable | story |
| E5b | `cp_lakay` | `cp_beaver_hollow` | story-gate | one-way | finish "That's Murfree Country" | chapter-bound | the camp moves; edge `rg_bayou_nwa` to `rg_roanoke_ridge`; some scarred Murfree horses come from this mission or Murfree encounters | late-game |
| E6 | `cp_beaver_hollow` | `cp_pronghorn_ranch` | story-gate | one-way | finish "Red Dead Redemption" | point-of-divergence | some Arthur-only valuables do not carry over; ending depends on Honor and the final choice | story |
| E6b | `cp_pronghorn_ranch` | `cp_beechers_hope` | story-gate | one-way | finish the last mission of the first epilogue part | chapter-bound | safehouses replace the gang camp | story |
| E7 | any camp | `st_new_austin` | conditional | two-way | New Austin is off-limits and lethal for the player character in this campaign phase | chapter-bound | bounty hunters and a sniper | progression |
| E7b | any camp | `st_new_austin` | conditional | two-way | the epilogue lifts the restriction | none | New Austin holds 8 dinosaur bones, 2 to 3 legendary animals (the Tatanka Bison's location is disputed between guides) and 2 to 4 legendary fish (sources disagree on which waters are in New Austin; see Corpus inconsistencies in `dependencies.md`) | story |
| E8 | any town with a station | any town with a station | fast-travel | two-way | trains and stagecoaches; camp fast travel needs a camp upgrade bought at the Ledger | none | the Ledger unlocks after Leopold Strauss's first "Money Lending and Other Sins" mission (Chapter 2) | progression |
| E9 | `cp_beechers_hope` | full map | hub-spoke | two-way | after the credits | none | graves, "It's Art" and "Bountiful" are post-story only | story |

_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://reddead.fandom.com/wiki/Missable_Content_in_Redemption_2 ; https://www.powerpyx.com/red-dead-redemption-2-all-dinosaur-bones-locations/ ; https://www.ign.com/wikis/red-dead-redemption-2/Camp_Guide_-_How_to_Upgrade,_Fast_Travel,_and_All_Upgrades (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Single source -- verify · class:community-wiki]
> **Cross-system dependency** -- see `dependencies.md` DEP-014.

**Edge types:**
- `story-gate` -- passing this edge advances the story; usually one-way at time of passing
- `one-way` -- direction is permanently fixed
- `optional` -- player's choice; access is permanent
- `hub-spoke` -- connection between hub node and a dungeon/zone; usually bidirectional
- `fast-travel` -- fast-travel network edge
- `conditional` -- access depends on a flag (item, story progress, NG+)

**Point-of-no-return subtypes:**
- `permanent` -- passing locks out the source zone forever
- `chapter-bound` -- access ends at chapter transition, may resume later
- `missable-trigger` -- passing locks out a missable item or quest in another zone
- `point-of-divergence` -- choice gate; alternative branch becomes unreachable

## Chapter ↔ Zone Mapping

Chapter titles and counts from the Fandom mission list and the IGN mission list. Mission total: the wiki states 109 (94 story plus 15 Honor missions), above the 104-107 range an earlier brief expected; the variance is sub-part counting.
_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles (P1 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Confirmed: 2 sources, 1 language]

| Chapter | Zones | Notes | tier |
|---|---|---|---|
| 1 Colter | `cp_colter`; only `rg_grizzlies_west` is open (snowbound, scripted) | 6 missions in 2 possible orders; Arthur cannot leave camp except on certain missions | none |
| 2 Horseshoe Overlook | `cp_horseshoe_overlook`; New Hanover, Ambarino, Lemoyne and most of West Elizabeth are open | 24 missions (25 if "An American Pastoral Scene" is played here); the Ledger, Dead Eye growth, fishing and most collectible strands open here | progression |
| 3 Clemens Point | `cp_clemens_point`; same open map as Chapter 2 | 20 missions (21 with "An American Pastoral Scene") | late-game |
| 4 Saint Denis (camp: Shady Belle) | `cp_shady_belle`; same open map, Saint Denis-centred missions | 16 missions including 4 optional | late-game |
| 5 Guarma | `isl_guarma` only until the return, then `cp_lakay` briefly | 7 missions plus 3 that straddle Chapters 5 and 6 | story |
| 6 Beaver Hollow | `cp_beaver_hollow`; mainland as before | 25 missions | late-game |
| Epilogue 1 Pronghorn Ranch | `cp_pronghorn_ranch`; mainland including New Austin | 11 missions | story |
| Epilogue 2 Beecher's Hope | `cp_beechers_hope`; full mainland | 12 missions plus an optional credits mission | story |

_source: https://reddead.fandom.com/wiki/Missions_in_Redemption_2 ; https://www.ign.com/wikis/red-dead-redemption-2/Collectibles ; https://www.powerpyx.com/red-dead-redemption-2-all-dinosaur-bones-locations/ (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Single source -- verify · class:community-wiki]

Mission names per chapter are written in `sections/chapter_*.md`, where they are tagged by chapter.

## Optional Content

| Name | Unlock condition | Access window | Parent zone | Recommended chapter | Failure mode | tier |
|---|---|---|---|---|---|---|
| Stranger strands (31 per the wiki: 26 standalone plus 5 that are also Honor missions) | meeting each stranger | many run through the whole story; some are chapter-bound | various | as met | several are missable (see `sections/missables.md`) | progression |
| Money Lending and Other Sins (Strauss debts) | camp, Chapter 2 after the first five missions | per chapter (I-III Chapter 2, later parts in later chapters) | camp | 2 | can auto-cancel if a debtor is knocked out or killed in a homestead robbery | progression |
| Event areas (Castor's Ridge, Appleseed Timber Co., Central Union Railroad Camp) | visit over time | stages across the story chapters | various | any | stages can skip if left too long | progression |
| Legendary Gunslingers strand | stranger | Chapter 2 on | various | 2 | Calloway's Revolver and Midnight's Pistol can be missed | progression |
| Vampire (Saint Denis) | find 5 markings, midnight | any | `tn_saint_denis` | 4 | Ornate Dagger lost if met while wanted | progression |
| Homestead stashes | see `items/collectible_requests_and_stashes.md` | limited; some lost to story | various | 2 | missable | progression |
| Collectible sets (cigarette cards, dinosaur bones, dreamcatchers, rock carvings, exotics, legendary animals and fish, graves, treasure hunts, bounty posters, hunting requests, item requests) | see `items/collectibles.md` | see `items/collectibles.md` | various | 2 | see `items/collectibles.md` | progression |

_source: https://reddead.fandom.com/wiki/Missable_Content_in_Redemption_2 ; https://www.rdr2.org/guides/red-dead-redemption-2-missable-quests-guide/ ; https://www.powerpyx.com/red-dead-redemption-2-all-weapons-locations/ (P1 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_ [Confirmed: 2 sources, 1 language]

## Support Topology

### Save stations

There is no named "save point". A manual save exists (pause menu, "Story" tab, Save Game / Load Game), with 15 manual slots; Load Game also offers the latest autosave.
_source: https://www.pcgamer.com/red-dead-redemption-2-rdr2-how-to-save/ ; https://www.pushsquare.com/guides/red-dead-redemption-2-how-to-save-and-load-the-game-manually ; https://steamcommunity.com/app/1174180/discussions/0/3781372149103901929 (P2 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Confirmed: 3 sources, 1 language]

Autosaves exist and the game can be finished on autosaves alone; players advise overwriting or deleting the autosave before quitting so that a manual save loads next. Saving is blocked during missions (missions use checkpoints) and at the very beginning of the game; one poster says combat blocks it too.
_source: https://www.pushsquare.com/guides/red-dead-redemption-2-how-to-save-and-load-the-game-manually ; https://steamcommunity.com/app/1174180/discussions/0/3781372149103901929 ; https://www.pcgamer.com/red-dead-redemption-2-rdr2-how-to-save/ (P2 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Confirmed: 3 sources, 1 language]

Saving while sitting in a wilderness-camp tent respawns you at that exact spot on load; any other save respawns in the general area. Wilderness camps allow sleeping up to 56 hours in a row and cannot be pitched near towns, settlements, gang hideouts, roads, train tracks or water.
_source: https://reddead.fandom.com/wiki/Camps (P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Single source -- verify · class:community-wiki]

Whether sleeping in camp itself autosaves was not confirmed by any source read, and no in-game name for a save point was found; the gang-camp bed and hotel beds are time-skip points.
_source: model analysis 2026-10-30 from the P2 research gap notes · capture: derived · confidence: low · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_

### Fast-travel network

| Node type | Cost | Restrictions | Unlocked when | tier |
|---|---|---|---|---|
| Gang-camp fast-travel map (on Arthur's wagon) | free per use; unlock = a lodging upgrade ($220) then a second upgrade ($325) = $545 (Special/Ultimate Edition: 20% off) | one-way (cannot travel back to camp with it); visited destinations only; the horse comes only if close; more than one use per in-game day empties the horse's stamina core | the Ledger opens after depositing a Money Lending I or II debt (Chapter 2); free with no upgrade in a late chapter | progression |
| Wilderness camp (player-pitched) | free; same upgrade required | same destination list plus Colter (wilderness-camp only; one commenter disputes this); not near towns, roads or water | after the lodging upgrade | progression |
| Stagecoach | paid, about $5-$15 | one guide says it is locked in a state where the player has a bounty; two others say it needs no bounty anywhere; cannot take the player to camp; visited destinations only | from Chapter 2 | none |
| Train (ticket from a station post office clerk) | paid, about $5-$15 | usable with a bounty; boarding without a ticket gives a train-robbery bounty; stations only in West Elizabeth, New Hanover and Lemoyne; Riggs and Wallace stations are reachable only by train | from Chapter 2 | none |
| Mission-end travel offer | free | only at the end of some missions; refusing removes the ride back to camp | any | none |
| Surrender to law (after vandalism or assault) | Honor, money, jail days | delivers to the state's main town | any | none |
| Cinematic-camera auto-ride (horse) | free | must be on a road toward the waypoint; not teleport; hostiles still attack | any | none |

_source: https://reddead.fandom.com/wiki/Fast_Travel ; https://www.powerpyx.com/red-dead-redemption-2-how-to-unlock-fast-travel/ ; https://www.rdr2.org/guides/red-dead-redemption-2-unlock-fast-travel-guide/ ; https://www.gamepro.de/artikel/red-dead-redemption-2-so-funktioniert-die-schnellreise,3336864.html [translated from: de] ; https://vgtimes.ru/guides/52683-bystroe-peremeschenie-v-red-dead-redemption-2-tri-prostyh-sposoba.html [translated from: ru] ; https://www.mejoress.com/es/desbloquear-viaje-rapido-en-red-dead-redemption-2/ [translated from: es] (P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_ [Contradicted across sources -- see notes]

The camp fast-travel list names 23 fixed places (22 reachable from the map plus Colter): Annesburg, Braithwaite Manor, Butcher Creek, Caliga Hall, Colter (wilderness camp only), Cornwall Kerosene & Tar, Emerald Ranch, Lagras, Rhodes, Saint Denis, Strawberry, Valentine, Van Horn Trading Post, Wapiti Indian Reservation, plus the current gang camp while the gang lives there; the epilogue adds Armadillo, Beecher's Hope, Benedict Point, Blackwater, MacFarlane's Ranch, Manzanita Post, Pronghorn Ranch, Thieves' Landing and Tumbleweed. The Fandom count of 23 matches the third-party map's 23 markers; another site's layer lists only 20, omitting three of them.
_source: https://reddead.fandom.com/wiki/Fast_Travel ; https://guides4gamers.com/red-dead-redemption-2/pois/fast-travel/ ; https://rdr2map.com/ (P1 and P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Contradicted across sources -- see notes]

Stagecoach destinations: Annesburg, Emerald Station, Rhodes, Saint Denis, Strawberry, Valentine, Van Horn Trading Post, plus Armadillo, MacFarlane's Ranch, Tumbleweed (after the first epilogue part) and Blackwater (epilogue). Train stations with a ticket office: Annesburg, Emerald Ranch, Rhodes, Riggs Station, Saint Denis, Valentine, Wallace Station.
_source: https://reddead.fandom.com/wiki/Fast_Travel (P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Single source -- verify · class:community-wiki]

### Hub access

| Fact | tier |
|---|---|
| There is no fast travel into the gang camp: the camp map and the stagecoach are one-way out; return by riding, by auto-ride to a waypoint, or by taking a train or stagecoach to the nearest town and riding. The wiki lists the current gang camp as a destination only when travelling from a wilderness camp. | progression |
| Absent from camp more than three days costs Arthur Honor on return; Javier, Charles or Bill may ride out to fetch him. | progression |
| No corpses or hogtied people in camp; fast travelling into camp with a dead NPC on the horse bugs the entry scene. The same rules apply at every later camp. | progression |
| Camp location per chapter: see the Chapter ↔ Zone Mapping table above and the per-camp files in this folder. | progression |

_source: https://www.powerpyx.com/red-dead-redemption-2-how-to-unlock-fast-travel/ ; https://www.gamepro.de/artikel/red-dead-redemption-2-so-funktioniert-die-schnellreise,3336864.html [translated from: de] ; https://www.mejoress.com/es/desbloquear-viaje-rapido-en-red-dead-redemption-2/ [translated from: es] ; https://reddead.fandom.com/wiki/Fast_Travel (P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_ [Single source -- verify · class:community-wiki]

Camp locations per chapter, from the Fandom camp table: Chapter 1 Colter (abandoned mining town, Grizzlies West near Spider Gorge); Chapter 2 north of Flatneck Station just east of the Dakota River in the Heartlands; Chapter 3 Scarlett Meadows, west shore of Flat Iron Lake; Chapter 4 a manor in Bayou Nwa; Chapter 5 a chapel ruin on the island, then Lakay in Bayou Nwa near Lagras; Chapter 6 a hill basin by a cave in Roanoke Ridge; Epilogue 1 Pronghorn Ranch (West Elizabeth); Epilogue 2 Beecher's Hope (Great Plains, West Elizabeth).
_source: https://reddead.fandom.com/wiki/Camps ; https://www.gtabase.com/red-dead-redemption-2/missions/?lang=en (P2 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Confirmed: 2 sources, 1 language]

## Locks and Keys

Every row names its key or marks it unknown. Rows with a disputed key or chapter gate are in the second table.

Design note (zipper, 2026-10-30): the rows for stashes, treasure hunts, legendary animals and fish, bounty posters and similar finds are the lock-and-key view of facts whose per-find detail lives in `items/collectible_*.md` (for example `items/collectible_requests_and_stashes.md`). Both views are kept on purpose: this table answers "what does this lock need?", the item files answer "where is each find?". They repeat one set of sources, so they count as ONE source, never two, when a later pass counts independent documentation.

| Lock location | Key required | Key source | Visible before key? | Notes | tier |
|---|---|---|---|---|---|
| Camp Ledger beside the donation box (camp upgrades, wagon restocks) | deposit any debt from "Money Lending and Other Sins I and II" | debtors around New Hanover (Chapter 2) | yes | last usable at a later camp | progression |
| Camp fast-travel map, Arthur's wagon | the two lodging upgrades ($220 then $325) via the Ledger | Ledger (camp) | no, appears after purchase | free in a late chapter | progression |
| Locked doors and stagecoach locks (anywhere) | Lock Breaker (about $25) | any fence: south of Emerald Ranch in the Heartlands, north of Rhodes, the Saint Denis market, Van Horn Trading Post; also given automatically during a story mission | yes | one guide: opens any lock but not safes | progression |
| Safes (homesteads, shops) | dynamite (gun stores, or camp once upgraded) | gun stores in all towns | yes | one source only; combination cracking not covered | none |
| New Austin (Cholla Springs, Rio Bravo, Gaptooth Ridge, Hennigan's Stead) | reach the epilogue | story | yes (on the map) | 8 dinosaur bones, the Cougar and Pronghorn legendary animals (plus the Tatanka Bison per GamePro only), Largemouth Bass and the channel catfish (the New Austin fish count is disputed, 2 to 4; see `items/collectible_legendary_fish.md`) | story |
| Guarma free roam | only between the island's first mission and completion of both of its two named missions | story (Chapter 4 exit) | no (off-map) | closes permanently without glitches | story |
| Elysian Pool waterfall cave (New Hanover): Poisonous Trail treasure and the dreamcatcher reward painting | a lantern; hidden tunnels | key source not stated in any source read (key: unknown) | yes (cave mouth) | Ancient Arrowhead painting appears after all 20 dreamcatchers | none |
| Legendary Panther, Bolger Glade | complete the Master Hunter challenge tier 9 (one commenter: all other tiers too) | challenges (any region) | no (does not spawn) | | progression |
| Legendary Alligator near Lakay, Bayou Nwa | finish the Chapter 4 mission "Country Pursuits" | story | no | a PowerPyx commenter also reports a Chapter 4 gate | late-game |
| Robin Koninsky cigarette card, Saint Denis theatre table by the stage | finish "Fatherhood and Other Dreams" and watch all performances | Chapter 4 story plus theatre | no | | late-game |
| One card per cigarette set (12 cards) | accept "Smoking and other Hobbies" (Phineas, after "Who is Not without Sin") | Chapter 2 | no (card spawns later) | cards can also be bought in Premium Cigarette packs | progression |
| 30th dinosaur bone (not inspectable, no Eagle Eye highlight) | complete the first part of "A Test of Faith" (meet Deborah MacGuiness, Heartlands) | Chapter 2 | yes | bones vanish once inspected | progression |
| Some exotic orchid spawns | reach the matching Algernon request; collecting all but one of a type early shows ordinary flowers at the last spot | Chapter 4 "Duchesses and Other Animals" | partly | reader comments only | late-game |
| "Do Not Seek Absolution I-II" | Honor level 4 (average) or higher | the player's conduct | no | Chapter 6 only | late-game |
| "Honor, Amongst Thieves" | agree to help Captain Monroe during "Archeology for Beginners" | Chapter 6 | no | | late-game |
| "Of Men and Angels" | completed "Brothers and Sisters, One and All" (Chapter 4) | Saint Denis | no | before "The Fine Art of Conversation" | late-game |
| Robbie Laidlaw bounty (Rhodes station poster) | deliver Mark Johnson and collect a family photo at the Old Harry Fen hut | Rhodes area, Chapter 4 on | no | target at a cabin or cotton field near Braithwaite Manor | late-game |
| Joaquin Arroyo and Esteban Cortez bounties (Tumbleweed jail) | the first epilogue part's "Gainful Employment" plus the Del Lobo execution event in Tumbleweed | New Austin, epilogue | no | Arroyo's map is lost after the bounty | story |
| Anthony Foreman bounty (Saint Denis police) | Foreman left alive in "No, No and Thrice, No" (Chapter 4) plus "Gainful Employment" | story | no | target via the bartender at a tavern in northeast Saint Denis | story |
| Strawberry jail (Joshua Brown poster) | re-entry is locked; wait or pay off the bounty | Strawberry | yes | | progression |
| Aberdeen Pig Farm side room (south door) | follow the man on the porch inside first; alternative: shoot out the window | Aberdeen Pig Farm | yes | the story gate of this stash is not stated | none |
| Lonnie's Shack stash | interrogate the last surviving occupant (kill 3 of 4) | Lonnie's Shack | no (location varies) | save first | none |
| Catfish Jacksons stash | threaten the son with the living-room shotgun | Catfish Jacksons cabin | no | interacts with Money Lending V | late-game |
| Watson's Cabin kitchen-table lockbox ($73) | rest twice so the four sons appear, then kill them | Watson's Cabin | yes | a shotgun from the cellar suffices for the achievement | none |
| Chez Porter barn stash (upper floor) | Javier's home-robbery companion activity (Chapter 2 and a later chapter) | camp | yes | Ambarino, near Whinyard Strait (search snippet) | progression |
| Van Horn Mansion table money | residents present at random times | south of Van Horn Trading Post | yes | | none |
| Jack Hall Gang hunt, first map | buy from the stranger Maximo near Flatneck Station; if gone or dead, any fence ("All That Glitters") | Heartlands, Chapter 2 | n/a | | progression |
| Poisonous Trail hunt, first map | lockbox under the bed by the door, Cairn Lodge (snowy northwest) | Ambarino, Chapter 2 | n/a | final cache needs a lantern | progression |
| High Stakes hunt, first map | lasso and hogtie a treasure-hunter chance encounter (after "The New South"); after 3 failed encounters buy from fences | Chapter 3 | n/a | | late-game |
| Mended (torn) map treasure, tiny cave west of Twin Rocks, New Austin | torn map 1 (drawer, hut at the start of Little Creek River) plus torn map 2 (drawer, Manito Glade) | West Elizabeth, Chapter 2 on; when the treasure opens is disputed (first epilogue part per one source, only after the story per others; see Corpus inconsistencies in `dependencies.md`) | n/a | reward: Otis Miller's Revolver and photographs | story |
| Le Tresor des Morts hunt | pre-order, Special or Ultimate Edition only | n/a | n/a | 5 gold bars | progression |
| Landmarks of Riches hunt | examine the plaque on the back of the Obelisk, northwest of Strawberry past Owanjila | West Elizabeth, Chapter 2 on | n/a | | late-game |
| Elemental Trail hunt | shoot the rope holding a corpse by the foot, far west New Austin by the Sea of Coronado; loot the map | New Austin, first epilogue part on | n/a | | story |
| Jeremy Gill channel catfish trip (Rio Bravo) | mail all 13 legendary fish; the invitation cannot arrive before the second epilogue part | post offices | no | | story |
| Graves (9) | story completed | n/a | yes (sites exist) | | story |
| Unique horses (Mahogany Bay, Raven Black, Rachel, Buell) | their missions ("Outlaws from the West", "Exit Pursued by a Bruised Ego", "The Wheel", stranger "The Veteran") | story | n/a | start part IV of "The Veteran" after the epilogue to keep Buell | story |

_source: https://reddead.fandom.com/wiki/Fast_Travel ; https://reddead.fandom.com/wiki/Camps ; https://reddead.fandom.com/wiki/Missable_Content_in_Redemption_2 ; https://reddead.fandom.com/wiki/A_Test_of_Faith ; https://www.rdr2.org/guides/fences-locations-guide/ ; https://www.rdr2.org/guides/landmark-of-riches-treasure-hunt/ ; https://www.rdr2.org/guides/elemental-trail-treasure-hunt/ ; https://www.powerpyx.com/red-dead-redemption-2-treasure-map-locations-solutions/ ; https://powerpyx.com/red-dead-redemption-2-homestead-stash-locations ; https://www.powerpyx.com/red-dead-redemption-2-legendary-animals-locations/ ; https://www.rdr2.org/guides/red-dead-redemption-2-bounty-hunting-missions-guide/ ; https://www.truetrophies.com/t234780/lending-a-hand-trophy (P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Single source -- verify · class:community-wiki]
> **Cross-system dependency** -- see `dependencies.md` DEP-004.

Disputed or unknown keys:

| Lock location | Key required | Notes | tier |
|---|---|---|---|
| First fence (Emerald Ranch) | unlocked after "The Spines of America" per GameRevolution, or after "Pouring Forth Oil" per rdr2.org (which also says it can be visited earlier) | unresolved; both values kept | progression |
| Willard's Rest homestead lockbox (beside the bed), north of Van Horn per a commenter | teach the resident to hunt, return two days later, shooting contest, dinner | the chapter gate is disputed (after "A Fork in the Road" per the wiki, after the first Chapter 6 mission per PowerPyx) | late-game |
| Carmody Dell stash (may count for "Breaking and Entering") | key: unknown -- the PowerPyx author could not confirm | gap | progression |
| Gang hideouts as locks | key: unknown -- no source read lists story-mode hideout unlock conditions | gap | progression |

_source: https://www.gamerevolution.com/guides/450811-red-dead-redemption-2-lock-breaker-guide ; https://www.rdr2.org/guides/fences-locations-guide/ ; https://reddead.fandom.com/wiki/Missable_Content_in_Redemption_2 ; https://powerpyx.com/red-dead-redemption-2-homestead-stash-locations (P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 2 · puzzle-tier: 2 · category: mainline · spoiler: late-game_ [Contradicted across sources -- see notes]
