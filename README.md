# Pills Performance

Pills Performance is a personal, local-first app for tracking daily routines, trading, training, sleep, meals, recovery, and reviews. This repository keeps the GitHub name `pills-adventure` and provides the home for its source code.

**Current status:** repository baseline only. The existing local app has not been imported, and this checkout is not runnable yet. There are no dependency manifests, database migrations, or automated application checks here. Features below describe the intended app, not functionality shipped by this commit.

## MVP

- One owner account, with authenticated access and no public registration.
- Today view for habits and daily logs with as few taps as possible.
- Trading journal with private chart uploads; training and recovery tracking.
- Simple meal tracking without requiring weighed macros.
- Weekly and monthly reviews, trends, and PDF/Excel exports.
- Settings for accent colours and 12/24-hour time; easy time entry.
- Backup and verified restore before relying on the app for personal records.

The first deployment stays on the owner's PC. Phone/LAN access and PWA support follow after the local baseline is verified. Trading features record activity; they do not place trades or hold exchange credentials.

## Planned structure

| Path | Responsibility |
| --- | --- |
| `apps/web/` | Next.js App Router frontend using React and TypeScript |
| `apps/api/` | NestJS API, authentication, validation, and persistence |
| `apps/api/prisma/` | Schema and reviewed migrations, added with the app import |
| `packages/contracts/` | Optional shared API types; no server secrets or database client |
| `docs/` | Architecture, MVP acceptance criteria, import and repository setup |
| `.github/` | Contribution review and issue templates |

PostgreSQL stores application data; Prisma manages database access. DBeaver is a local database tool, not an application dependency. Private uploads, exports, logs, and backups belong outside the checkout.

## Start here

```sh
git clone https://github.com/pills-carter/pills-adventure.git
cd pills-adventure
```

1. Read [the architecture](docs/ARCHITECTURE.md) and [MVP plan](docs/MVP.md).
2. Follow [the import checklist](docs/IMPORT.md) to bring in the working local app one module at a time. Preserve its working versions and lockfiles.
3. Record the actual install, development, migration, and verification commands when those manifests arrive. Do not assume `npm install` or `npm run dev` works in this baseline.
4. Complete the owner-only [GitHub settings checklist](docs/REPOSITORY-SETTINGS.md).

## Data and security

This is a public source repository. Never commit personal journals, real chart uploads, database dumps, passwords, session tokens, API keys, or populated Postman environments. Use synthetic examples. `.gitignore` is a convenience, not a security boundary: review staged content before each commit.

Read [SECURITY.md](SECURITY.md) before reporting a vulnerability and [CONTRIBUTING.md](CONTRIBUTING.md) before making changes. This baseline does not establish a security certification or prove the local app is secure.

## Project boundaries

Pills Performance remains separate from cloud identity monitoring and ecommerce/API-testing projects. See [the repository boundary decision](docs/REPOSITORY-BOUNDARIES.md).

## Licence

No licence has been selected in this baseline. Public visibility alone does not grant an open-source licence; the owner should make that choice explicitly before inviting reuse.
