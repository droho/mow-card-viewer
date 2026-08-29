# Card Viewer 0.7.0 — release notes

## Release focus

First official standalone public release candidate for the Man O' War Card Viewer.

## User-visible changes from the July preview

- synchronized release-critical presentation with accepted Data Core v13;
- corrected HIGH / LOW targeting semantics for locations belonging to both target bands;
- overlap locations are shown once, between HIGH and LOW rows, matching physical-card reading order;
- corrected Skaven purchased-crew presentation for Deathburner, Doombringer and Warp Raider;
- full English interface alongside the established Polish interface;
- removed the unfinished standalone Card Emulator / `Talia` product surface;
- cleaned internal build/version labels from player-facing UI;
- simplified Below Waterline presentation to numeric `SAVE` and `SINKS AT` fields;
- improved mobile weapon-diagram sizing and forced diagrams to remain in their intended light presentation in system dark mode;
- mobile navigation polish: compact language switch, previous/next controls for Units/Cards/Rules, clearer Units controls, consistent section-entry animation;
- desktop navigation alignment cleanup.

## Unchanged boundaries

- Data Core remains read-only;
- no Fleet Builder or Game Companion changes;
- no change to `mow.fleet 0.1.2`;
- accepted WD1 weapon-diagram payload is not forked or rewritten;
- no backend, accounts or cross-device state synchronization.
