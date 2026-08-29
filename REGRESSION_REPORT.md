# CV-REL-01D-CORR-02 RC3 — regression report

Date: 2026-08-29

**PASS — correction-scope regression / final R3 manual review accepted.**

## Parent baseline

RC3 is a bounded correction of the live Card Viewer 0.7.0 RC2.

Parent production commit: `ec586a176a4dbf004b8cadaf0ef840fa6a1bba74`  
Parent live `index.html` SHA-256: `aac3e258ea9b0451126f6aa32eab9e1a5e4327c5e9a8001a3c6a6bc016cd7035`

## Trigger / root cause

RC2 was reproduced freezing on **EN -> PL**.

The supplemental RC2 translation layer and the pre-existing core i18n layer both restored the same `placeholder`, `aria-label` and `title` attributes. On EN -> PL, their MutationObservers repeatedly rewrote those attributes and reacted to one another, producing an unbounded observer / microtask feedback loop.

## RC3 correction

1. Supplemental translation is EN-only.
2. Polish restoration is owned exclusively by the core i18n layer.
3. `#cvLangMobileToggle` is excluded from generic core attribute restoration and remains owned by the language-switch helper.
4. Three additional English audit leftovers were corrected:
   - `90° / ½ ruchu` -> `90° / ½ movement`;
   - `Wybierz jednostkę dla tego slotu.` -> `Choose a unit for this slot.`;
   - `Brak dopasowania do tabeli units` -> `No match in the units table`.
5. Final accepted R3 presentation adds:
   - `by Droho` -> Instagram `midlifeminiatures`;
   - `Fleet Builder ↗` -> `mowfleetbuilder.com`;
   - a compact mobile-only creator / builder strip.

## Automated gates inherited from the RC3 correction audit

- desktop PL -> EN -> PL: PASS in Units, Cards, Rules and Compare;
- mobile PL -> EN -> PL: PASS in Units, Cards, Rules and Compare;
- mobile language-toggle text / aria after return to PL: PASS;
- six repeated EN / PL stress cycles: PASS;
- selected-unit Compare EN audit: 0 high-confidence Polish UI leftovers;
- empty-state Compare EN audit: 0 high-confidence Polish UI leftovers;
- Units / Cards / Rules EN audit: 0 high-confidence Polish UI leftovers;
- browser page errors during those tests: 0.

## Final R3 presentation-only delta

RC3 Review R3 differs from the already-tested RC3 Review R2 only by:
- one mobile-only CSS block;
- one mobile-only creator / builder strip markup block.

No language-switching or application logic changed in R3.

## Data / diagram non-regression

The RC3 correction audit confirmed identical embedded payloads vs RC2 for:

- `UNITS`;
- `CARDS`;
- `CARD_DECKS`;
- `TAG_DEFINITIONS`;
- `DB_META`;
- `CARD_RELATION_DATA`;
- `MOW_LOCATION_MATCHES`;
- `UNIT_RULES_DATA`;
- `WEAPON_DIAGRAMS`.

No Data Core, game semantics or WD1 payload was changed.

## Manual gate

The user manually reviewed RC3 Review R3 and accepted it on 2026-08-29.

Accepted `index.html` SHA-256:

`da4b05f01ba6d63dd20d0700d693a2f96805a1f97ba2a4a17923502f874eba1b`

## Scope guard

- Data Core unchanged;
- Fleet Builder unchanged;
- Game Companion unchanged;
- `mow.fleet 0.1.2` unchanged;
- no production write is part of this sealed artifact.
