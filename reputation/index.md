# Red Dead Redemption 2 -- Reputation

**status:** research-integrated <!-- scaffold | research-integrated | live-observed | reconciled -->
**last_reconciled:** 2026-10-30
**class:** reputation

## Why this file exists

This file is the corpus's roster for reputation tracks. Honor is a mechanical meter (discounts, outfits, loot, achievement-linked) and bounty/law escalation is a second track. The general rules of each system live in `mechanics.md`; this folder holds per-track pointers.

## Roster

| entity-id | display name | entity-status | status | first-encounter zone | missable |
|---|---|---|---|---|---|
| `honor` | Honor | unspecified | research-integrated | `rg_grizzlies_west` | Honor missions are chapter-bound |
| `bounty` | Bounty and law | unspecified | research-integrated | `rg_heartlands` | one later bounty can be lost |

## Pointer rules

- Per-track detail lives in `reputation/<entity-id>.md`; this file is the index.
