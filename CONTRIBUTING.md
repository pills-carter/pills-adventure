# Contributing

Keep changes small enough to review and verify independently. This repository is the source home for a single-owner local app.

## Workflow

1. Start from current `main` and create a short-lived branch, such as `feat/today-import` or `fix/export-layout`.
2. Explain the problem and acceptance criteria in an issue or pull request. Report vulnerabilities privately using [SECURITY.md](SECURITY.md).
3. Import or change one page/module at a time. Preserve existing behaviour and wait for the owner's local verification before proceeding to the next module.
4. Use synthetic fixtures and screenshots. Review `git status --short` and `git diff --cached` before committing; inspect new files as well as modifications.
5. Open a pull request using the supplied template. Describe validation honestly, including checks that could not run.
6. Merge after review and relevant checks. Never force-push `main` or rewrite its initial history.

## Implementation expectations

- TypeScript for application code; validate all API input at runtime.
- NestJS owns authentication, authorization, database access, uploads, and exports. Browser code must not receive secrets or directly access PostgreSQL.
- Authenticate every private read/write route, including file download, backup, restore, and export. An unlinked UI control is not access control.
- No real personal data or credentials in tests, issue descriptions, screenshots, logs, or sample files.
- Commit dependency lockfiles and reviewed Prisma migrations. Document schema changes and their backup/rollback implications.
- Avoid unrelated reformatting and dependency upgrades in an app-import PR.
- Do not add public registration, cloud hosting, telemetry, SMS, or exchange connectivity without an explicit scope decision.

## Verification

This initial baseline has no application test runner. For documentation changes, verify links, paths, and examples. After importing the app, document real commands for linting, type checking, relevant tests, and builds. Add tests for meaningful risks such as unauthorized record access, duplicate writes, unsafe uploads, and destructive restore behaviour.

Do not claim that a README checklist, passing build, or `.gitignore` proves security. Dependency review, secret detection, and runtime security checks are separate controls.

## UX

Keep routine tracking quick, mobile-friendly, and accessible. Honour the owner's selected accent and clock format. Prefer simple meal inputs and easy time entry. Check export readability and charts as well as on-screen layout.
