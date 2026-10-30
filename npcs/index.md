# Red Dead Redemption 2 -- NPCs

**status:** research-integrated <!-- scaffold | research-integrated | live-observed | reconciled -->
**last_reconciled:** 2026-10-30
**class:** npcs

## Why this file exists

This file is the corpus's roster for the named individual NPCs -- the player-facing index of "who is in this class, and where do I read about each one." The class covers any named individual NPC regardless of `entity-status`; hostility is a state, not a class identity. Per-entity detail lives in `npcs/<entity-id>.md`. Entities beyond the player's current chapter (1-2) stay hidden by the spoiler ceiling in `warning_tiers.md`; a roster row for a hidden entity keeps its name out of read-time answers.

Scope note: the research surfaced strangers and quest-givers with real content (listed below). Gang members, antagonists and most other cast appear in P1 and P2 only as mission givers or in one-line fates, so they do not yet have files; if the player asks about one, the reader answers from the chapter files and a live lookup. Entity files for them are deferred, not forbidden (`deferred-to: live play` or a later research phase).

## Roster

| entity-id | display name | entity-status | status | first-encounter zone | missable |
|---|---|---|---|---|---|
| `leopold_strauss` | Leopold Strauss | friendly | research-integrated | `cp_horseshoe_overlook` | Money Lending parts are chapter-bound |
| `deborah_macguiness` | Deborah MacGuiness | friendly | research-integrated | `rg_heartlands` | no |
| `francis_sinclair` | Francis Sinclair | friendly | research-integrated | `tn_strawberry` | no |
| `phineas_ramsbottom` | Phineas T. Ramsbottom | friendly | research-integrated | `rg_heartlands` | no |
| `jeremy_gill` | Jeremy Gill | friendly | research-integrated | `rg_bayou_nwa` | Fisherman's Hat |
| `ms_hobbs` | Ms. Hobbs | friendly | research-integrated | `tn_valentine` | no |
| `algernon_wasp` (hidden) | Algernon Wasp | friendly | research-integrated | `tn_saint_denis` | card and note |
| `brother_dorkins` (hidden) | Brother Dorkins | neutral | research-integrated | `tn_saint_denis` | yes |

## Pointer rules

- Per-entity detail lives in `npcs/<entity-id>.md`. The reader opens those files for entity-shaped questions; this file is the index, not the answer surface.
- Claims about an entity continue to route to their primary-vector destination. The entity overlay aggregates the claim into the per-entity file in parallel.
- Hidden entities (`entity-hidden: yes`) keep their full content in the per-entity file; read-time tier gating handles concealment.

## Sources

- Per-entity source citations live in the primary-vector files each entity file points to, not here.
