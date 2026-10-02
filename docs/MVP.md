# MVP import and completion plan

The owner has reported a working local Pills Performance app. This repository has not yet received or independently verified that source. Import working functionality instead of regenerating it. Use one reviewable page/module per PR and get local confirmation before the next segment.

| Stage | Deliverable | Acceptance evidence |
| --- | --- | --- |
| 0. Preserve | Private backup; inventory manifests, schema, ports, and source | Restore rehearsal succeeds; no personal data staged |
| 1. Foundation | Existing web/API apps, lockfiles, sanitized env examples, Prisma migrations | Documented clean setup; loopback services; login/logout work; unauthenticated private API requests fail |
| 2. Today | Habits and daily logs | Edits persist after reload; repeated saves do not duplicate completions; dates use the selected local day |
| 3. Trading | Journal and private chart uploads | Reload persistence; invalid/oversize files rejected; unauthenticated attachment access denied |
| 4. Training | Training, sleep, meals and recovery | Existing entries survive import; edit/delete and simple meal inputs work |
| 5. Reviews | Weekly/monthly charts and PDF/Excel export | Correct period totals using synthetic fixtures; readable charts; no unauthorized export; formula-like input handled safely |
| 6. Settings | Accent theme and easy time picker | Theme applied consistently; 12/24-hour preference persists; keyboard/mobile interaction works |
| 7. Resilience | Backup/restore and end-to-end verification | Backup restored into a disposable DB; records and attachment links reconcile; malformed restore rejected; live data preserved on failure |

## Release gate

- [ ] Installation, actual runtime versions, ports, and all commands documented from the imported source.
- [ ] Authentication, logout/session expiry, ownership, CSRF and upload/download controls verified.
- [ ] No production credentials, personal records, chart files, or database dumps in Git history.
- [ ] Lint, type checking, relevant tests, and builds run against committed lockfiles.
- [ ] Backup/restore verified and sensitive data locations documented privately.
- [ ] Owner completes the main Today → Trading → Training → Review → Export journey.

## After the local MVP

PWA/offline behaviour and phone access can follow, with explicit private-cache and network controls. Do not delay importing working features to add cloud infrastructure, microservices, multi-user roles, ecommerce, or NHI monitoring.
