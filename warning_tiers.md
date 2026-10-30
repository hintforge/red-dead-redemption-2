# Warning / hint tiers (Red Dead Redemption 2)

Two independent tier flags control how much info the guide volunteers *preemptively*, before the player asks. Higher tiers include everything from lower. Each set independently.

## The player's current settings

- **Enemies: Tier 0** -- set 2026-10-30
- **Puzzles: Tier 1** -- set 2026-10-30

To change: "set enemy warning to tier N" / "set puzzle tier to N." Update this section with the date.

## Playthrough-progress ceiling (game-specific)

Starting ceiling for a new playthrough: Chapter 1-2 (Colter / Horseshoe Overlook). Until the player says they have progressed, treat anything tagged `spoiler: late-game`, `spoiler: story`, or belonging to Chapter 3 onward (including the epilogue and any map region the player has not reached) as gated: do not volunteer it, and do not confirm or deny its existence. Raising a tier above does not lift this ceiling; only the player stating a new chapter does (record it in `CHECKPOINT.md`). Red Dead Online is out of scope for this guide.

---

# Enemy tiers (0-5)

### Tier 0 -- No warning
- No mention of enemies before encounter.
- No "watch out for X," no enemy-type names in route hints.
- Boss existence hidden. No boss prep.
- Permitted: post-encounter help on request.

### Tier 1 -- Mobs only
- Regular enemy types named in route hints when relevant.
- Boss existence still hidden.
- Boss-drop loot may be referenced obliquely ("a fight at the end drops a useful item").

### Tier 2 -- Mobs + boss-drop heads-up
- Tier 1 + explicit warning that a boss fight is coming at the end of an area.
- No boss name, no mechanics, no recommended loadout.

### Tier 3 -- Boss prep
- Tier 2 + name the boss generically ("a heavy mech," "a mutant cluster") and recommend loadout swaps.
- No mechanics walkthrough, no phase descriptions.

### Tier 4 -- Boss prep + materials
- Tier 3 + crafting materials worth stocking for ammo / consumables before the fight.
- Still no mechanics walkthrough during the fight.

### Tier 5 -- Full boss strategy
- Tier 4 + phase-by-phase mechanics, ability combos, common failure modes, cheese strats.

---

# Puzzle tiers (0-3)

The hint ladder (Lvl 1 nudge → Lvl 2 more → Lvl 3 step-by-step) is **request-based** -- the player asks for what they want. The puzzle *tier* controls how much is delivered **automatically on entry**, before they ask.

### Tier 0 -- Silent
- No puzzle info preempted. Player asks for everything via the Lvl 1/2/3 ladder.

### Tier 1 -- Mechanic identified (suggested default)
- On entry to a puzzle room, name the puzzle type and core mechanic in one short sentence: "this is a rotation puzzle with two cranks," "this is a polarity-flip relay."
- Don't deliver Lvl 1 nudge unless asked.

### Tier 2 -- Auto-nudge
- Tier 1 + deliver the **Lvl 1 nudge automatically** on entry.

### Tier 3 -- Full walkthrough
- Deliver the **Lvl 3 step-by-step** automatically on entry. Use sparingly -- for sections the player wants to blow through.

### Per-puzzle ladder requests are NOT tier changes
A "Lvl 2" or "Lvl 3" request on a specific puzzle is a **one-off escalation** for that puzzle only. The tier flag does NOT change. Next puzzle resets to whatever the flag says. To change permanently, the player says "set puzzle tier to N."

---

## Implementation note

Before delivering preemptive info, check **both** tier settings here. When in doubt between tiers, err stricter. The player can always raise.

For multi-contributor / GitHub-distributed guides, every claim and section carries explicit tier metadata (`enemy-tier` and `puzzle-tier`) plus a `category` field so the aggregator can render reader-tier-appropriate output.

## Breach log

None yet.
