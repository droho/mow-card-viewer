# CV-REL-01C RC1 — regression report

## Result

**PASS — RC1 static/data regression and release-shell checks.**

The release candidate is based on the exact manually accepted CV-REL-01B R3A artifact. CV-REL-01C changes only public release identity/canonical metadata and removes/hides legacy engineering provenance from player-facing surfaces. Canonical game-data payloads are unchanged.

## Accepted input seal

- CV-REL-01B R3A SHA-256: `0ffbb9bc5753a6922b4183da30db474b16de904f8b24f5049a1936cebdf6e8a5` — PASS.
- Data Core v13 SHA-256: `1ddb0b70bfc0d2e504f8877fa052a54a7466919036f9d668f41bf204c3d003ca` — PASS.
- `PRAGMA user_version = 13` — PASS.
- `PRAGMA integrity_check = ok` — PASS.

## Exact game-data projection checks

- unit profiles: 73 / DB 73 — PASS;
- hit locations: 311 / DB 311 — PASS;
- combat weapons: 91 / DB 91 — PASS;
- combat special-rule rows: 172 / DB 172 — PASS;
- target-band memberships: 185 / DB 185 — PASS;
- target-band membership set exactly equals Data Core v13 — PASS;
- split HIGH/LOW profiles: 20 — PASS;
- overlap locations: 24 across 12 profiles — PASS;
- cards: 219, exact `card_id` set vs Data Core — PASS;
- card decks: 17, exact `deck_id` set — PASS;
- magic cards: 114, exact `card_id` set — PASS;
- magic decks: 6, exact deck-key set — PASS.

### FAQ/Errata projection

Data Core contains 71 `annual_faq_errata` source rows. The Viewer intentionally exposes 66 deduplicated global FAQ records. The union of their `source_faq_ids` covers all 71 Data Core rows exactly — PASS.

The five apparent count differences are the paired Tzeentch FAQ rows consolidated for Bane Tower / Great Winged Terror; no source FAQ is lost.

## Mandatory fixtures

- Empire Greatship: HIGH rolls 4/5/6 — PASS;
- Empire Greatship: overlap HIGH+LOW rolls 2/3 — PASS;
- Empire Greatship: LOW rolls 4/5/6 — PASS;
- Dwarf Dreadnought: split profile with zero false overlap — PASS;
- Skaven Deathburner: purchased crew / no fixed numeric crew — PASS;
- Skaven Doombringer: purchased crew / no fixed numeric crew — PASS;
- Skaven Warp Raider: purchased crew / no fixed numeric crew — PASS.

## Payload preservation vs accepted R3A

The following JavaScript data literals are byte-identical to accepted R3A:

- `UNITS` — PASS;
- `CARDS` — PASS;
- `CARD_DECKS` — PASS;
- `WEAPON_DIAGRAMS` — PASS;
- `GLOBAL_FAQ_DATA` — PASS.

Therefore the CV-REL-01C release shell did not mutate game data or the accepted shared weapon-diagram payload.

## Release-shell checks

- public page title identifies Card Viewer 0.7.0 — PASS;
- canonical URL is `https://cards.mowfleetbuilder.com/` — PASS;
- no `noindex` directive — PASS;
- public `robots.txt` allows crawling — PASS;
- public CNAME is `cards.mowfleetbuilder.com` — PASS;
- player-facing internal WD1/build/database footers and engineering kickers are hidden — PASS;
- legal notice is linked from the UI — PASS;
- standalone Card Emulator UI is absent — PASS;
- ship/card/rule/compare deep-link routing remains present — PASS;
- PL/EN layer remains present — PASS;
- reduced-motion handling remains present — PASS;
- weapon-diagram forced-light behavior from accepted R3/R3A remains present — PASS.

## Browser/manual evidence inheritance

The accepted B stage supplied successful browser smoke on 320/360/390 px mobile, system dark-mode diagram rendering and 1440×900 desktop, followed by user/manual acceptance of exact R3A after the narrow duplicate-animation correction.

The current execution environment blocks a fresh local Chromium navigation to file/localhost content, so RC1 browser evidence is not falsely marked as newly executed. Because RC1 does not change game logic/data and its UI changes are limited to release identity and hiding old technical provenance, the remaining publication smoke is explicitly retained in CV-REL-01D after deployment.

Raw machine-readable/static evidence is in `REGRESSION_RAW.txt`.
