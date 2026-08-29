# Card Viewer 0.7.0 RC1 — deployment and rollback runbook

## Preconditions

1. Central acceptance identifies the exact RC ZIP SHA-256 and `index.html` SHA-256.
2. No RC file has changed after acceptance.
3. Read-only DNS preflight confirms `cards.mowfleetbuilder.com` can be assigned safely.
4. `droho/mow-card-viewer` is still absent or is confirmed to be the intended empty publication target.

## Publication sequence — CV-REL-01D only

1. Create `droho/mow-card-viewer` as the production repository.
2. Publish the exact accepted RC public files without modifying `index.html`.
3. Verify the committed `index.html` hash equals the accepted RC hash.
4. Enable GitHub Pages from `main` / repository root.
5. Configure the Pages custom domain as `cards.mowfleetbuilder.com`.
6. If GitHub requests domain verification, add exactly the GitHub-provided TXT challenge and wait for verification.
7. Add/confirm DNS `cards` CNAME → `droho.github.io` only after the no-conflict preflight.
8. Wait for DNS and GitHub Pages custom-domain recognition.
9. Enable/enforce HTTPS when GitHub makes the option available.
10. Perform live smoke on the final HTTPS hostname.

## Mandatory live smoke

- root page loads without console/runtime failure;
- canonical URL is the production hostname;
- PL → EN → PL works;
- Units: Greatship overlap presentation and Dreadnought split profile;
- Cards: open representative normal and magic cards;
- Rules: search/open a rule and FAQ;
- Compare: load two units and switch comparison view;
- deep links: one `#ship:`, one `#card:`, one `#rule:`, one compare hash;
- mobile navigation at approximately 390 px;
- system dark mode: weapon diagram remains light;
- no standalone `Talia` / Card Emulator entry point;
- `LEGAL_NOTICE.html` is reachable;
- `robots.txt` is public and does not disallow `/`.

## Rollback

Because this is a new standalone hostname/repository, rollback does not require migration of user state.

If live smoke fails before DNS/custom-domain activation:
- disable Pages or stop before DNS write;
- correct only through a new RC, never edit the accepted RC silently.

If live smoke fails after DNS/custom-domain activation:
1. disable GitHub Pages custom-domain publication or remove the new `cards` DNS record;
2. preserve the failed release commit and evidence for diagnosis;
3. do not redirect users to the preview repository as a substitute production release;
4. create a corrected RC2 through the release process;
5. republish only after acceptance.
