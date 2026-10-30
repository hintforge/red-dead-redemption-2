# Red Dead Redemption 2 — Hintforge Companion

![Red Dead Redemption 2 companion status — coverage, verification, spoiler control, save reader, and tools](assets/readme-status-card.svg)

A spoiler-controlled hint companion for **Red Dead Redemption 2**'s story mode, built for the long ride: collectibles, challenges, missables, and what each chapter quietly closes behind you. Built in the [Hintforge](https://github.com/hintforge/builder) format: a sidekick that answers only from these guide files, at the spoiler level you set, and that keeps track of where you are so you can step away and pick back up.

## Use it

You need a Hintforge reader running in Claude Code, Codex, or OpenClaw. Point it at this repo:

> Load the Red Dead Redemption 2 guide from github.com/hintforge/red-dead-redemption-2

Then just ask: *"what will I miss if I finish this chapter," "where's the nearest cigarette card," "where was I."* Runtime setup lives in [`hintforge/reader`](https://github.com/hintforge/reader).

## Spoilers

**You** decide how much this guide volunteers, through two dials: enemy warnings and puzzle hints. Out of the box it names no enemies ahead of time and, for puzzles, only says what kind of puzzle you are looking at. On top of the dials, it holds back everything past Chapter 2 until you tell it you've moved on, so later chapters, characters' fates and late regions stay off the table. Where the sources disagree, it says so rather than picking one.

## Collectible maps

Two map pages ship in `artifacts/`. `full_map.html` is the one to use while playing: it shows only collectibles that fit your chapter and spoiler settings, with filters, search and tick boxes for what you've found. `full_map_all_markers.html` shows every story-mode marker and is a spoiler page, for opening on purpose. The map picture is made from MapGenie's tiles and the marker positions come from rdr2map.com; both are credited on the pages.

## What's inside

A structured Markdown guide to story mode: core mechanics and settings, the camps and regions chapter by chapter, weapons, items and upgrades, every collectible set (cigarette cards, dinosaur bones, dreamcatchers, rock carvings, exotics, legendary animals and fish, treasure maps, graves and more) with where to find each one, the Honor and bounty systems, the strangers and characters you meet, the single-player achievements, and the points of no return. Red Dead Online is out of scope. The companion reads and writes only the files you control.
