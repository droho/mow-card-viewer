# CV-REL-01D-CORR-01 RC2 — regression report

Date: 2026-08-29

**PASS — correction-scope regression / manual review accepted.**

## Parent baseline

RC2 is a bounded correction of the live Card Viewer 0.7.0 RC1. The full RC1 static/data regression remains the inherited baseline. Parent production commit: `15a157c2b3da1daa659908420beef49a7f78809e`; parent live `index.html` SHA-256: `85677e7e1e0a3f945014f99991f0715c5a905f4c22362c8cb287a96decf56d38`.

## Correction scope

1. Complete the remaining English player-facing UI strings, especially Compare and card-relation surfaces.
2. Replace the ambiguous Dwarf upgrade-card sigil with a hammer-and-anvil emblem.

## Data / diagram non-regression

The following embedded canonical payload constants are byte-identical between RC1 and RC2:

- `WEAPON_DIAGRAMS`;
- `UNITS`;
- `CARDS`;
- `CARD_DECKS`;
- `TAG_DEFINITIONS`;
- `DB_META`;
- `CARD_RELATION_DATA`;
- `CARD_RELATIONS`;
- `CARD_RELATION_FAMILIES`;
- `MOW_LOCATION_MATCHES`;
- `UNIT_RULES_DATA`;
- `RULE_PROFILE_INDEX`;
- `RULE_ARCHETYPE_INDEX`;
- `GENERIC_RULE_INDEX`;
- `GLOBAL_FAQ_DATA`;
- `GLOBAL_RULE_CANONICAL_LAYER`;
- `FAQ_RULE_TARGET_MAP`;
- `GLOBAL_RULE_ALIASES`;
- `GLOBAL_RULE_INDEX`.

Therefore the correction does not mutate game data, target-band semantics, FAQ content, card data, unit data, or the accepted WD1 weapon-diagram payload.

## English UI audit

Representative English rendering was exercised for Units, Cards, Rules and all four Compare modes. A high-confidence Polish-remnant detector returned:

- Units: 0;
- Cards: 0;
- Rules: 0;
- Compare / Full analysis: 0;
- Compare / Side by side: 0;
- Compare / Differences only: 0;
- Compare / Shared only: 0.

The pass covered the live-defect vocabulary including Polish diacritics and terms such as `Brak`, `Wybierz`, `WSPÓLNE`, `WARIANT`, `jednostek`, `Potwierdzone`, `Lokacje`, `Zwiń/Rozwiń` and `Rodzina modelu`.

## Visual correction

The Dwarf upgrade-card emblem was changed from the ambiguous star-like symbol to a hammer-and-anvil engineering mark. No Dwarf card text or game rule was changed.

## Manual gate

The user manually reviewed and accepted the RC2 review candidate on 2026-08-29.

## Scope guard

- Data Core unchanged;
- Fleet Builder unchanged;
- Game Companion unchanged;
- `mow.fleet 0.1.2` unchanged;
- no production write is part of this sealed artifact.
