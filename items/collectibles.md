# Red Dead Redemption 2 -- Collectibles and challenges

**status:** research-integrated
**last_reconciled:** 2026-10-30
**research_run:** P1 2026-10-30; P2 2026-10-30 (each a single deep-research result)

Overview of every collectible set in scope (story mode plus collectibles and challenges; Red Dead Online is out of scope). Each set has its own location file with one table row per find, written so a later map page can read it: region, nearest named landmark, short location text, chapter gate, spoiler tag. **No coordinates exist in any source read; none are invented.** Totals below are in-game totals as the sources state them; a third-party map's marker counts are noted where they differ.

Design note (zipper, 2026-10-30): this file owns totals, windows, challenges and the 100% tracker; each `collectible_*.md` file owns the per-find rows. `nav/architecture.md` "Locks and Keys" repeats some finds along the key axis (what a lock needs) and is a second view of the same sources, not independent documentation.

| Set | File |
|---|---|
| Cigarette cards (144) | [`collectible_cigarette_cards.md`](collectible_cigarette_cards.md) |
| Dinosaur bones (30) | [`collectible_dinosaur_bones.md`](collectible_dinosaur_bones.md) |
| Dreamcatchers (20) | [`collectible_dreamcatchers.md`](collectible_dreamcatchers.md) |
| Rock carvings (10) | [`collectible_rock_carvings.md`](collectible_rock_carvings.md) |
| Exotics (orchids, plumes, eggs) | [`collectible_exotics.md`](collectible_exotics.md) |
| Legendary animals (16) | [`collectible_legendary_animals.md`](collectible_legendary_animals.md) |
| Legendary fish (13 plus a bonus) | [`collectible_legendary_fish.md`](collectible_legendary_fish.md) |
| Graves (9) | [`collectible_graves.md`](collectible_graves.md) |
| Treasure hunts | [`collectible_treasure_maps.md`](collectible_treasure_maps.md) |
| Bounty posters | [`collectible_bounty_posters.md`](collectible_bounty_posters.md) |
| Hunting requests, camp item requests, companion activities, homestead stashes | [`collectible_requests_and_stashes.md`](collectible_requests_and_stashes.md) |

## Totals and windows

| Set | Verified total | Earliest safe | Missable? | Verdict across sources | tier |
|---|---|---|---|---|---|
| Cigarette cards | 144 = 12 sets of 12 | Chapter 2 | not missable; selling a card breaks the set you need to hold | agree | progression |
| Dinosaur bones | 30 | Chapter 2 (strand accepted) | no | agree | none |
| Dreamcatchers | 20 (one map site showed 21) | Chapter 2 | no | agree, one outlier | none |
| Rock carvings | 10 | Chapter 2 | no (the Old Brass Compass in Sinclair's house can be missed) | agree | none |
| Legendary animals | 16 (one 100% page says "of 14") | Chapter 2 | one-time kills | agree, one outlier | progression |
| Legendary fish | 13 for the strand | Chapter 2 | Fisherman's Hat is missable | agree | progression |
| Treasure hunts | 7 traced; sources count 3 to 11 | Chapter 2 | no | disagree (marker vs stash vs chain counting) | progression |
| Bounty posters | 14 on PC per one guide, 10 per another, 6 poster towns | Chapter 2 | yes, one bounty can be lost (details in the gated table below) | disagree | progression |
| Hunting requests | 5 | Chapter 2 | no | agree | progression |
| Camp item requests | about 20 rows in the wiki table vs 9 map markers | Chapter 2 | yes | disagree (markers are likely fetch-item world spots) | progression |

_source: https://www.powerpyx.com/red-dead-redemption-2-100-guide-checklist/ ; https://reddead.fandom.com/wiki/Dinosaur_Bones ; https://reddead.fandom.com/wiki/Dreamcatchers ; https://reddead.fandom.com/wiki/Rock_Carvings ; https://www.shacknews.com/article/108175/all-legendary-animal-locations-in-red-dead-redemption-2 ; https://www.rdr2.org/guides/red-dead-redemption-2-bounty-hunting-missions-guide/ ; https://rdr2map.com/ (P1 and P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_ [Contradicted across sources -- see notes]

Gated windows and details for the same sets (and two sets that open late). Everything in this table is story-tier.

| Set | Gated detail | Earliest safe | Latest safe | tier |
|---|---|---|---|---|
| Cigarette cards | New Austin cards in the epilogue | Chapter 2 | post-story | story |
| Dinosaur bones | 8 of the 30 are in New Austin | Chapter 2 (strand accepted) | post-story | story |
| Dreamcatchers | none beyond the window | Chapter 2 | post-story | story |
| Rock carvings | none beyond the window | Chapter 2 | post-story | story |
| Exotics | 5 requests, 19 item types, 182 items by one tally; commenters disagree on losses; the map's 202 markers do not equal 182 requested items | Chapter 4 after "The Gilded Cage" | post-story | story |
| Legendary animals | one-time kills | Chapter 2 | post-story | story |
| Legendary fish | a bonus catfish trip after the 13 | Chapter 2 | post-story | story |
| Graves | 9 (Hosea and Lenny counted separately); not missable | post-story | post-story | story |
| Treasure hunts | none beyond the window | Chapter 2 | post-story | story |
| Bounty posters | Anthony Foreman's bounty can be lost | Chapter 2 | epilogue | story |
| Hunting requests | request 5 only in the epilogue | Chapter 2 | post-story | story |
| Camp item requests | windows differ per row | Chapter 2 | per row, Chapter 2 to epilogue | story |

_source: https://www.powerpyx.com/red-dead-redemption-2-100-guide-checklist/ ; https://reddead.fandom.com/wiki/Dinosaur_Bones ; https://reddead.fandom.com/wiki/Dreamcatchers ; https://reddead.fandom.com/wiki/Rock_Carvings ; https://www.shacknews.com/article/108175/all-legendary-animal-locations-in-red-dead-redemption-2 ; https://www.rdr2.org/guides/red-dead-redemption-2-bounty-hunting-missions-guide/ ; https://rdr2map.com/ (P1 and P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_ [Contradicted across sources -- see notes]

## Challenges (9 categories of 10 tiers)

- The nine challenge categories are Bandit, Explorer, Gambler, Herbalist, Horseman, Master Hunter, Sharpshooter, Survivalist and Weapons Expert; each has 10 tiers. Examples: Survivalist tier 9 is catching a fish of at least 19 lb; Horseman tier 10 is breaking every wild horse breed. The Explorer, Gambler and Herbalist tier lists were not read.
_source: https://www.ign.com/wikis/red-dead-redemption-2/Collectibles ; https://reddead.fandom.com/wiki/Missions_in_Redemption_2 (P1 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Confirmed: 2 sources, 1 language]

- The Master Hunter tier-9 challenge gates the legendary panther's appearance; tier 10 is killing it (see `collectible_legendary_animals.md`).
_source: https://www.ign.com/wikis/red-dead-redemption-2/Collectibles ; https://www.powerpyx.com/red-dead-redemption-2-legendary-animals-locations/ (P1 and P2 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_ [Confirmed: 2 sources, 1 language]
> **Cross-system dependency** -- see `dependencies.md` DEP-009.

## Completion tracker (100%)

- The 100% list is structured as: Missions and Events (all story missions; 10 stranger strands; 5 bounties; 25 chance encounters; 1 bushwhack; 6 gang hideouts), Collectibles (1 point of interest; 9 graves; 1 cigarette card set; 30 dinosaur bones; 13 legendary fish; all exotics; 10 rock carvings; all hunting requests; 1 treasure chain; 20 dreamcatchers), Compendium (50 of 178 animals; 10 of 72 equipment; 10 of 30 fish; 6 gangs; 10 of 19 horse breeds; 20 of 43 plants; 48 of 59 weapons), Player (max cores; horse bond level 4; challenges) and Misc (5 shacks; 5 legendary animals; 4 table games; 5 ranters; 1 hotel bath; 1 show; 1 theatre; 6 recipe types; coach, home, shop and train robbery). Missed Honor missions do not block 100%.
_source: https://www.powerpyx.com/red-dead-redemption-2-100-guide-checklist/ (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression · achievement: best_in_the_west · achievement-hidden: no · trigger_type: collection_ [Single source -- verify · class:editorial-en]
> **Cross-system dependency** -- see `dependencies.md` DEP-022.

- The wiki says one dinosaur bone and one rock carving suffice for 100%, while the PowerPyx checklist says all; the sources disagree on whether one or three treasure chains are needed.
_source: https://reddead.fandom.com/wiki/Dinosaur_Bones ; https://reddead.fandom.com/wiki/Rock_Carvings ; https://www.powerpyx.com/red-dead-redemption-2-100-guide-checklist/ ; https://www.powerpyx.com/red-dead-redemption-2-treasure-map-locations-solutions/ (P1 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none_ [Contradicted across sources -- see notes]

- Completing any one collectible strand unlocks the "Collector's Item" achievement; the rock carvings strand is the fastest.
_source: https://www.powerpyx.com/red-dead-redemption-2-trophy-guide-roadmap/ ; https://reddead.fandom.com/wiki/Dreamcatchers ; https://steamcommunity.com/stats/1174180/achievements (P1 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none · achievement: collectors_item · achievement-hidden: no · trigger_type: collection_ [Confirmed: 3 sources, 1 language]

## Minigames

- The four table minigames are poker, blackjack, dominoes and Five Finger Fillet (a third-party map shows 6, 3, 3 and 4 locations). The "Hobby Horse" achievement needs each started; winning is not required.
_source: https://www.powerpyx.com/red-dead-redemption-2-100-guide-checklist/ ; https://rdr2map.com/ ; https://www.powerpyx.com/red-dead-redemption-2-trophy-guide-roadmap/ (P1 research 2026-10-30) · capture: web_fetch · confidence: high · enemy-tier: 0 · puzzle-tier: 0 · category: mainline · spoiler: none · achievement: hobby_horse · achievement-hidden: no · trigger_type: collection_ [Confirmed: 3 sources, 1 language]

## Suggested low-backtrack order (derived)

The order is derived from the access windows above; no source states it.

| Step | Chapter | What to do | tier |
|---|---|---|---|
| 1 | 2 | From Horseshoe Overlook sweep the Heartlands, Valentine, Cumberland and Grizzlies for dreamcatchers, rock carvings, Heartlands bones and Valentine and Emerald Ranch cards; start the Jack Hall Gang and Poisonous Trail treasure hunts; hunt the ungated legendary animals; do every Chapter 2 item request and companion activity before leaving the camp | progression |
| 2 | 3 | From Clemens Point do Scarlett Meadows, Rhodes and Braithwaite cards, the legendary fox, coyote and bluegill, the High Stakes hunt, the Landmarks of Riches hunt (its first map is found in Chapter 2) and the Chapter 3 requests | late-game |
| 3 | 4 | From Shady Belle do Saint Denis cards, the Bayou Nwa and Bluewater Marsh orchids and plumes after "The Gilded Cage", and the swamp and river legendary fish and animals; finish everything camp-related first | late-game |
| 4 | 6 | Do the remaining Honor missions and the homestead stashes before the chapter's last mission | late-game |
| 5 | epilogue | Do every New Austin find, the epilogue bounties and the graves after the credits | story |

_source: model analysis 2026-10-30, derived from the windows in `items/collectibles.md` and the per-set files · capture: derived · confidence: low · enemy-tier: 3 · puzzle-tier: 3 · category: mainline · spoiler: story_
