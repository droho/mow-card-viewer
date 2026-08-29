# Card Viewer 0.7.0 RC2 — controlled correction deployment and rollback

## Preconditions

1. RC2 manual review is accepted.
2. Exact RC2 `index.html` SHA-256 is verified before upload.
3. Production repo remains `droho/mow-card-viewer`.
4. Existing custom domain / DNS / HTTPS configuration is not changed for this correction.

## Controlled replacement

1. Upload the exact RC2 replacement payload to `main` using the user-controlled GitHub workflow.
2. Do not edit files in the GitHub editor.
3. Commit the replacement as one correction commit.
4. Verify the committed `index.html` corresponds to the accepted RC2 SHA.
5. Wait for the GitHub Pages deployment for the new commit to complete successfully.
6. Do not change `CNAME`, DNS or Pages custom-domain settings.
7. Fetch the live HTTPS root and verify its SHA-256 equals the RC2 accepted hash.
8. Perform the bounded live smoke below.

## Mandatory RC2 live smoke

- root HTTPS returns 200 and HTTP still redirects to HTTPS;
- English Units contains no observed Polish UI remnants;
- English Cards: Dwarf upgrade representative uses the new hammer-and-anvil emblem and English helper/status text;
- English Rules loads/searches correctly;
- English Compare: representative pair in Full analysis, Side by side, Differences only and Shared only;
- PL ↔ EN switch remains functional;
- representative HIGH / HIGH+LOW / LOW ship card remains correct;
- mobile controls remain functional;
- weapon diagram remains light in system dark mode;
- `robots.txt` and `LEGAL_NOTICE.html` remain reachable.

## Rollback

If RC2 deployment or live smoke fails:

1. revert production `main` to parent production commit `15a157c2b3da1daa659908420beef49a7f78809e` (RC1);
2. do not alter DNS, CNAME or the custom domain unless the failure is independently proven to be infrastructure-related;
3. preserve the failed RC2 commit and evidence;
4. diagnose and create a new correction candidate rather than silently editing RC2.
