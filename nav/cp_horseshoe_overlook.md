# Nav -- Chapter 2: Horseshoe Overlook (camp `cp_horseshoe_overlook`)

**status:** research-integrated <!-- scaffold | research-integrated | live-observed | reconciled -->
**last_reconciled:** 2026-10-30
**research_run:** P2 2026-10-30 (single deep-research result; P1 folded in)

**Type:** main-story zone (Chapter 2 camp; the open map)
**Linear?:** yes (with optional branches; mission order is partly free)
**Chapter:** 2 Horseshoe Overlook

## Entry

From `cp_colter` via E1. The camp is north of Flatneck Station, just east of the Dakota River, in the Heartlands, New Hanover. New Hanover, Ambarino, Lemoyne and most of West Elizabeth are open.

## Exit

To `cp_clemens_point` via E2, by finishing "A Strange Kindness" (Dutch, Dewberry Creek; the proposed camp is abandoned and Clemens Point is taken instead).
**Type:** story-gate
**Point of no return:** chapter-bound. Chapter 2 mission strands (Money Lending I-III, We Loved Once and True, Pouring Forth Oil II), Chapter 2 companion activities (Five Finger Fillet with Lenny; hunting with Charles and the homestead robbery with Javier continue into a later chapter) and Chapter 2-only item requests (Abigail $5, Jack's thimble, Javier's Oleander Sage, Mary-Beth's pen, Jack's comic, Pearson's rabbit, Sean's bourbon) close.

> **Cross-system dependency** -- see `dependencies.md` DEP-015.
> **Cross-system dependency** -- see `dependencies.md` DEP-016.

## Outgoing edges

- E2 (`cp_horseshoe_overlook`, `cp_clemens_point`) -- story-gate, finish "A Strange Kindness"
- E7 (any camp, `st_new_austin`) -- conditional; New Austin is off-limits for now

## Entry tips (3 max)

1. Do every Chapter 2 camp item request and companion activity before "A Strange Kindness"; they close with the chapter.
2. Sparing Jimmy Brooks in the first mission gives the Pen valuable; the Raven Black Shire is obtainable only in the fourth mission.
3. Collectible strands open here (cards, dinosaur bones, dreamcatchers, the Jack Hall Gang and Poisonous Trail hunts); see `items/collectibles.md` for routing.

## Sequential gates

| # | Gate (mission, giver) | What it unlocks or closes | tier |
|---|---|---|---|
| 1 | "Polite Society, Valentine Style" (Uncle, Valentine), entry | sparing Jimmy Brooks gives the Pen valuable (its later loss is a late-chapter detail) | progression |
| 2 | "Americans at Rest" (Javier, Smithfield's Saloon, Valentine) | Thomas Downes (Charity Handbill) can be met once, before or after this mission | progression |
| 3 | "Who is Not without Sin" (Reverend Swanson, Flatneck Station) | Phineas T. Ramsbottom ("Smoking and other Hobbies", cigarette cards) becomes available after it | progression |
| 4 | "Exit Pursued by a Bruised Ego" (Hosea, Dakota River) | first Bharati Grizzly encounter; Raven Black Shire obtainable only here; wilderness-camp meat seasoning unlocks after it | progression |
| 5 | "Money Lending and Other Sins I and II" (Leopold Strauss, camp) | depositing any collected debt in the donation box unlocks the Camp Ledger (camp upgrades, fast travel map); Honor mission, expires at the end of the chapter; Chick's Treasure Map comes from the debtor Chick Matthews here | progression |
| 6 | "Good, Honest, Snake Oil" (Curtis Malloy, Valentine sheriff) | Honor mission; unlocks bounty hunting (Valentine and Saint Denis posters); does not expire until a late chapter (documented exception to the Honor-missions-expire rule) | progression |
| 7 | "The Spines of America" (Hosea, Carmody Dell) | meets the Emerald Ranch fence (sells the Lock Breaker); what unlocks the fence is disputed | progression |
| 8 | "Blessed are the Meek?" (Micah, jail near Strawberry) | unlocks the Joshua Brown bounty (Strawberry) | progression |
| 9 | "The First Shall Be Last" (Javier, Upper Montana River) | afterwards a unique random encounter (Javier asks for help rescuing Bill) can fire until a later chapter | progression |
| 10 | "A Fisher of Men" (Abigail) | unlocks Jeremy Gill's "A Fisher of Fish" strand and the Chapter 2-only Abigail and Jack item requests | progression |
| 11 | "We Loved Once and True I-III" (Mary Linton, a letter in camp; Cumberland Forest) | Honor; finish before the chapter-ending mission | progression |
| 12 | "Pouring Forth Oil I-IV" (John Marston, train robbery) | part II auto-skips after 4 in-game hours of being active; one source lists I and II as Honor missions and another omits them | progression |
| 13 | optional branch: "An American Pastoral Scene" (Micah); "The Sheep and the Goats" (John, Valentine auction) | the first may be played in Chapter 2 or a later chapter | progression |
| 14 | "A Strange Kindness" (Dutch, Dewberry Creek), exit | edge `rg_heartlands` to `rg_scarlett_meadows`, one-way | progression |

_source: https://www.gtabase.com/red-dead-redemption-2/missions/?lang=en ; https://reddead.fandom.com/wiki/Missable_Content_in_Redemption_2 ; https://reddead.fandom.com/wiki/Camps ; https://www.truetrophies.com/t234780/lending-a-hand-trophy ; https://www.powerpyx.com/red-dead-redemption-2-full-walkthrough-all-story-missions/ ; https://www.rdr2.org/guides/fences-locations-guide/ ; https://www.gamerevolution.com/guides/450811-red-dead-redemption-2-lock-breaker-guide (P2 research 2026-10-30) · capture: web_fetch · confidence: medium · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression · missable: yes · entity: leopold_strauss · entity-status: friendly_ [Contradicted across sources -- see notes]
> see npcs/leopold_strauss.md for full summary
> **Cross-system dependency** -- see `dependencies.md` DEP-001.
> **Cross-system dependency** -- see `dependencies.md` DEP-002.
> **Cross-system dependency** -- see `dependencies.md` DEP-003.
> **Cross-system dependency** -- see `dependencies.md` DEP-012.

## Optional branches / shortcuts

- "An American Pastoral Scene" can be deferred to a later chapter.
- New Austin is lethal for the player character in this phase of the game; bones, legendary animals and fish there are for later.

## Common confusions

- A reader comment (2018) reports that doing Uncle's mission first at the start of Chapter 2 made four camp members vanish; unverified.
_source: https://www.powerpyx.com/red-dead-redemption-2-full-walkthrough-all-story-missions/ (P2 research 2026-10-30) · capture: web_fetch · confidence: low · enemy-tier: 1 · puzzle-tier: 1 · category: mainline · spoiler: progression_ [Single source -- verify · class:forum]

## Sources

- https://www.gtabase.com/red-dead-redemption-2/missions/?lang=en
- https://reddead.fandom.com/wiki/Missable_Content_in_Redemption_2
- https://www.truetrophies.com/t234780/lending-a-hand-trophy
- https://www.powerpyx.com/red-dead-redemption-2-full-walkthrough-all-story-missions/
