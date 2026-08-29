# Card Viewer 0.7.0 RC3 — controlled correction deployment and rollback

## Preconditions

1. RC3 Review R3 manual review is accepted.
2. Exact RC3 `index.html` SHA-256 is `da4b05f01ba6d63dd20d0700d693a2f96805a1f97ba2a4a17923502f874eba1b`.
3. Production repo remains `droho/mow-card-viewer`.
4. Existing custom domain / DNS / HTTPS configuration is not changed for this correction.
5. Current production parent remains RC2 commit `ec586a176a4dbf004b8cadaf0ef840fa6a1bba74`.

## Controlled replacement

1. Upload the exact RC3 replacement payload to `main` using the user-controlled GitHub workflow.
2. Do not edit files in the GitHub editor.
3. Commit the replacement as one correction commit.
4. Verify the committed `index.html` corresponds to the accepted RC3 SHA.
5. Wait for the GitHub Pages deployment for the new commit to complete successfully.
6. Do not change `CNAME`, DNS or Pages custom-domain settings.
7. Fetch the live HTTPS root with a cache-busting query and verify its SHA-256 equals the accepted RC3 hash.
8. Perform the bounded live smoke below.

## Mandatory RC3 live smoke

- root HTTPS returns 200 and HTTP still redirects to HTTPS;
- repeat PL -> EN -> PL at least three times without freeze;
- repeat the language cycle once on mobile;
- English Units / Cards / Rules / Compare contain no observed Polish UI remnants;
- Dwarf upgrade representative still uses the hammer-and-anvil emblem;
- `by Droho` opens `https://www.instagram.com/midlifeminiatures`;
- `Fleet Builder ↗` opens `https://mowfleetbuilder.com`;
- mobile creator / builder strip remains compact and usable;
- representative HIGH / HIGH+LOW / LOW ship card remains correct;
- weapon diagram remains light in system dark mode;
- `robots.txt` and `LEGAL_NOTICE.html` remain reachable.

## Rollback

If RC3 deployment or live smoke fails:

1. revert production `main` to parent RC2 commit `ec586a176a4dbf004b8cadaf0ef840fa6a1bba74`;
2. do not alter DNS, CNAME or the custom domain unless failure is independently proven infrastructure-related;
3. preserve the failed RC3 commit and evidence;
4. diagnose and create a new correction candidate rather than silently editing RC3.
