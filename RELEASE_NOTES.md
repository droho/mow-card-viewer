# Card Viewer 0.7.0 — release notes

## Release focus

Official standalone public release of the Man O' War Card Viewer.

## Core release changes

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

## RC2 correction pass

A post-publication visual review identified remaining Polish player-facing strings in parts of the English UI and an ambiguous Dwarf upgrade-card sigil. RC2 corrected both without changing game data or gameplay logic.

- completed English labels, helper text, status badges, empty states and Compare/card-relation surfaces;
- removed Polish collapse/expand labels generated from CSS in English mode;
- replaced the Dwarf upgrade-card sigil with a neutral hammer-and-anvil engineering emblem.

## RC3 correction pass

A further live review identified a reproducible freeze when switching the interface from English back to Polish. RC3 removes the observer feedback loop and completes the language-cycle correction.

- supplemental translation is EN-only; Polish restoration remains owned by the core i18n layer;
- corrected mobile language-toggle attribute ownership;
- closed three additional English UI leftovers found during the full audit;
- added `by Droho` attribution linking to `https://www.instagram.com/midlifeminiatures`;
- added a `Fleet Builder ↗` link to `https://mowfleetbuilder.com`;
- added a compact mobile-only creator / Fleet Builder strip.

## Unchanged boundaries

- Data Core remains read-only and unchanged;
- no Fleet Builder or Game Companion changes;
- no change to `mow.fleet 0.1.2`;
- accepted WD1 weapon-diagram payload is not forked or rewritten;
- no backend, accounts or cross-device state synchronization.
