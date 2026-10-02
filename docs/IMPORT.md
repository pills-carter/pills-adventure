# Import the existing local app

## Preserve the working copy

1. Make a private backup of the existing source, database, and uploads outside this checkout. Do not upload that backup to GitHub.
2. Record the actual Node/package-manager versions, lockfiles, Next.js/NestJS versions, Prisma version, ports, routes, and database configuration privately. Never paste connection strings into an issue.
3. Confirm a restore using disposable data/storage before changing the live app. Keep the existing running copy intact during the import.

## Import source deliberately

1. Create a branch from `main`.
2. Copy reviewed frontend source into `apps/web/` and backend source into `apps/api/`. Do not copy `.git`, `.env*` values, dependency folders, build output, database dumps, uploads, logs, or archives.
3. Preserve the existing manifests and package-manager lockfiles. Do not introduce a root workspace manager or upgrade frameworks as part of this baseline migration.
4. Keep the API's Prisma schema and migration history together in `apps/api/prisma/`. Inspect seed scripts: use synthetic data, no fixed owner password, no live credentials.
5. Add `.env.example` files containing placeholder values and descriptions for variables actually used by the code. Configure explicit loopback hosts, non-conflicting ports, and exact web origins. Generate real secrets locally; never use sample values in a live app.
6. Review asset files manually. `.gitignore` cannot distinguish a legitimate UI image from a private trading screenshot and does not untrack files already committed.
7. Inspect `git status --short`, `git diff --cached --stat`, and `git diff --cached` before committing. Review untracked/new files and run a maintained secret scanner locally before the first source push; document which tool/version and scope were checked. Do not paste scanner findings containing secrets publicly.

## Reproduce before switching over

Document the actual per-app install, development, build, lint/type-check, test, Prisma generation, and migration commands. Use the chosen package manager's lockfile-preserving install mode. Do not publish guessed commands.

Use a disposable database first. Confirm migrations, synthetic seed data, login, persistence, attachment access, and exports. Check unauthenticated access is rejected and services listen only on intended interfaces. Never run a reset or destructive migration against the owner's live database.

Only switch the working app to this source after local verification. Import and verify remaining pages in separate segments using [MVP.md](MVP.md).

## Add automation with the source

Add lint/type-check/test/build CI when manifests and real commands exist. Give workflows minimal permissions, pin third-party actions to reviewed full commit SHAs, and avoid secrets in untrusted PR jobs. Add dependency update configuration for the actual package locations. Enable code and secret scanning appropriate to the repository. Until then, this baseline has no CI status that can establish application correctness or security.
