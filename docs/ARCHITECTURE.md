# Architecture

## Scope and trust boundaries

Pills Performance serves one owner on a local PC. The browser uses a Next.js UI, the UI calls the NestJS API, and the API accesses PostgreSQL through Prisma. The API alone reads and writes private uploads and exports. No hosted service or payment provider is required for this MVP.

| Component | Responsibility | Boundary |
| --- | --- | --- |
| Next.js / React | Display, forms, navigation, charts | Treat browser input as untrusted; no server secrets |
| NestJS | Auth, validation, ownership, uploads, reviews and exports | Authorize each private request |
| Prisma / PostgreSQL | Durable records and schema migrations | Local database, least-privileged app credentials |
| Private filesystem | Chart uploads, exports, backups | Outside public routes and Git; authorize access |

Use configurable non-conflicting ports and exact matching origins. Record actual values during import instead of assuming this is the only local app. Loopback defaults must be explicit in startup configuration, including any container port mappings added later.

## Domain boundaries

| Area | Records / behaviour | MVP constraints |
| --- | --- | --- |
| Identity | Owner account and session lifecycle | No public signup or seeded reusable password |
| Today | Habits, completions, daily log | Consistent local-date handling; prevent duplicates |
| Trading | Journal entries and chart attachments | Recordkeeping only; authenticated file access |
| Training | Workouts and recovery | Simple entry and editing |
| Wellbeing | Sleep, meals, body/recovery notes | Private data; meal tracking need not require grams |
| Reviews | Weekly/monthly summaries and charts | Define date boundaries and use stored records |
| Exports | PDF and Excel | Private downloads; safe handling of spreadsheet formula-like input |
| Settings | Accent and 12/24-hour display | Display format must not change stored times |
| Backup | Versioned backup and restore | Validate format, prevent path traversal, verify before replacing data |

These are intended responsibilities. The existing schema and implementation have not been inspected in this repository. Preserve the working local app before making architectural changes.

## Local-first storage

Keep canonical database files, chart uploads, backups, and export output outside the checkout. Store file identifiers in the database rather than trusting client-provided paths. Back up metadata and referenced files consistently. Restoration must preserve their relationship and be tested in a disposable environment.

## Later expansion

Phone/LAN access introduces network exposure and needs HTTPS, access controls, firewall review, and session/CSRF validation. PWA caches must avoid private API responses and exports by default. Cloud migration, multi-user tenancy, cloud monitoring, and ecommerce are outside this MVP.
