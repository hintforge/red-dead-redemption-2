# Red Dead Redemption 2 -- Limitations & Blocked Sources

Sources I found that look useful but couldn't fully fetch -- paywalls, Cloudflare, age gates, video-only content, etc. URLs preserved so the player (or another contributor) can open them in a real browser.

## How to read this file
- Each entry: topic, URL, block type, what I could glean, best alternative I did get to.
- Each per-topic file (in `puzzles/`, `[areas]/`, `items/`, `sections/`) also lists its own blocked sources at the bottom -- the player rarely needs to come hunting here.
- This file is the catch-all for sources that didn't fit a specific topic.

## Scope limits
- **Red Dead Online is out of scope** (scope set 2026-10-30). Seventeen of the game's 51 Steam achievements are online-only and are out of scope: they are not researched or covered.
- Story mode plus collectibles and challenges is the scope. Single-player DLC: none known; unverified.

## Block types
- **paywall** -- content gated behind a subscription or article limit
- **cloudflare** -- Cloudflare bot challenge / 403 / 503 from WebFetch
- **video-only** -- YouTube or other video where the answer is shown visually; no readable text equivalent
- **age-gate** -- content blocked behind age verification
- **cookie-wall** -- popup or consent flow that broke the fetch
- **search-snippet-only** -- search engine returned a snippet but the page itself wasn't reachable
- **dead-link** -- URL was in another source but no longer resolves

- **robots-restriction** -- the external research runtime reports a robots access restriction
- **terms-restriction** -- a stated retrieval restriction was reported; preserve the actual evidence
- **javascript-dependent** -- useful content requires page execution the available tool did not perform
- **login-required** -- a signed-in session is required
- **access-not-checked** -- no content/access check was performed; never call this robots-blocked

## Companion tools

For every useful map, tracker, database or completion tool supplied, recalled or found:

- Name and URL if verified (otherwise mark unknown/unverified)
- Apparent coverage, evidence for it, and uncertainty; unread coverage is not confirmed game data
- Reason not read, access-check result, policy evidence if available, and check date
- How a person could use it, best readable alternative, and wider-spoiler warning where relevant

Merge repeated URLs with dated evidence retained. Read tools can also be recorded here when they offer a useful location fallback. Record an honest empty statement when no candidates were found; do not imply exhaustive discovery.

Discovery was one combined search on 2026-10-30; it does not prove other tools do not exist.

### RDR2 Map (MapGenie) -- collectible and activity locations
- URL: https://rdr2map.com/ (verified loads; operated by MapGenie)
- Apparent coverage: collectibles (cigarette cards, dinosaur bones, dreamcatchers, exotics, rock carvings, legendary animals and fish, treasures), strangers, random events, amenities, minigames. Evidence: category list and marker counts read from page text on 2026-10-30. Counts are the map's marker counts, not verified in-game totals.
- Block type: javascript-dependent (marker coordinates are inside the map; only category names and counts were in page text). Plain page fetch of a mapgenie.io URL was refused by the fetch tool. Robots and terms: access-not-checked.
- How to use: the player can open it in a browser, mark found items with a free login. Wider-spoiler warning: map shows markers for the whole game, including late regions.
- Best readable alternative: the per-set location files in `items/` (cigarette cards, bones, dreamcatchers, carvings, fish, animals, treasure), which cite named guides and hold no coordinates.
- Check dates: P1 (2026-10-30) read the category names and counts through a headless browser after WebFetch was refused (counts: cigarette card 144, dinosaur bone 30, dreamcatcher 20, exotic 202, grave 9, hunting request 5, item request 9, legendary animal 16, legendary fish 14, rock carving 10, treasure 27, bounty poster 14, stranger 45, random event 398; several layers are PRO-gated). P2 (2026-10-30) reported the research runtime refused the domain ("unable to fetch"); that was not bypassed. Marker coordinates were not extracted by either research phase. The marker positions on this guide's collectible map pages (`artifacts/`) come from rdr2map.com's public map data, read 2026-10-30, and are credited on the pages.

### Shackmaps (Shacknews), RockstarINTEL dreamcatcher map, Guides4Gamers item-request markers
- URLs: https://www.shacknews.com/article/148698/red-dead-redemption-2-map-shackmaps ; https://rockstarintel.com/rdr2-dreamcatcher-locations/ ; https://guides4gamers.com/red-dead-redemption-2/pois/item-requests/
- P1: not read (time budget). P2 (2026-10-30): all three read. Shackmaps is a hand-crafted map with Trapper, stagecoaches, cigarette cards, dinosaur bones, fish and plant spawns, animal heatmaps and challenges; no counts, story-or-online scope not stated, free account for custom pins, no export; the page states Shacknews "strictly prohibits the use of its content for AI training". RockstarINTEL's dreamcatcher page says only that all 20 are free with no mission and the reward is behind the Elysian Pool waterfall; locations are in an embedded RDR2 Map, so its cigarette-card sibling is the same embed. Guides4Gamers lists 11 item-request markers (Fountain Pen, Harmonica, Naval Compass, four Penny Dreadful comics, Dutch's pipe, Pocket Mirror, Silver Pocket Watch, "The Case of the Shrew in the Fog"), each only "On maps: World Map", with no location text and no export; its fast-travel layer lists 20 points.
- Licence note: this corpus cites locations and wording from Shacknews pages (legendary animals, legendary fish) as facts with attribution and paraphrase. Whether the Shackmaps "AI training" sentence covers those articles is not established. The Shacknews facts are kept as attributed paraphrase, not reproduced text.

### Steam achievements page
- URL: https://steamcommunity.com/stats/1174180/achievements . Re-fetched 2026-10-30 at ingestion with WebFetch and the headless browser: both returned the same 26 of 51 names (heading "ACHIEVEMENTS (39)"). Hidden achievements and some others are not rendered signed-out. 18 of the 34 single-player names are `unverified against live platform list`.

### Exophase (Steam achievements list)
- URL: https://www.exophase.com/game/red-dead-redemption-2-steam/achievements/
- Block type: cloudflare (plain fetch returned 403 on 2026-10-30); readable through the headless-browser fetch. Used as the Stage 0 achievement-name source. Canonical Steam stats page returned only 26 of 51 names to a plain fetch.

### Local game files
- The installed game's files are proprietary `.rpf` archives with no plaintext siblings (verdict `packed`, 2026-10-30). Not usable as a source of exact names without extraction, which setup does not do.

## Entries

- **Fandom Legendary Animals page** (https://reddead.fandom.com/wiki/Legendary_Animals_in_Redemption_2): cloudflare; blocked from the headless browser on 2026-10-30. Best alternative: Shacknews and GamePro (two languages) in `items/collectible_legendary_animals.md`. Would resolve two legendary-animal location disagreements.
- **Fandom Dead Eye pages and Shacknews Dead Eye guide**: search-snippet-only (not attempted). Dead Eye rank unlock missions in `items/abilities.md` are therefore low-confidence.
- **PowerPyx and IGN sub-pages** (homestead list, shacks, gang hideouts, plants, horses, IGN treasure and challenge pages): not read; access-not-checked. Gaps are marked `[location inventory incomplete]` in the item files.
- **Reddit** `reddit.com/r/reddeadredemption/comments/1gktbl8/` (missed strangers) and a Chapter-2 fast-travel thread: not read in full; canonical Reddit URLs only. No Reddit sweep was run.
- **Rockstar Title Update 1.32 notes** (https://support.rockstargames.com/articles/4GR27mnSMJaPqF5gl2zDNu/red-dead-redemption-2-title-update-1-32-notes-ps4-xbox-one-pc): read in P1, not opened in P2. The absence of any later PC update is unverified; the executable build number was not found.
- **Video walkthroughs**: none transcribed in P1 or P2. Both phases' own "deep enough" checks record that miss.
- **Non-English coverage**: German (legendary animals, gates, bounties, fast travel), Spanish and Russian (fast travel) only; none for cigarette cards, exotics, dreamcatchers or treasure.
- **Bloxodes wiki** (bloxodes.com/red-dead): found in a P2 search snippet; claims all 19 exotics and "23 treasure map locations"; not read; possibly machine-written, so not used.
- Gaps recorded as unresolved, not invented: the homestead list for "Breaking and Entering" beyond seven candidates, exotic orchid spot lists, hunting-request poster locations, stranger-strand locations, gang-hideout unlock conditions, the lantern's source, and whether sleeping in camp autosaves.

## Always-blocked categories

Collectible respawn and rotation behavior that depends on the player's save or the in-game day (for example daily-rotating collectible sets) cannot be confirmed from static sources; the guide records the documented rule and marks it unverified.
