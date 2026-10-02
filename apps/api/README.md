# API application

Import the existing Pills Performance NestJS app here, including its reviewed Prisma schema and migrations under `prisma/`. This is a placeholder, not a running server.

Expected module responsibilities: auth, habits/daily logs, trading, training/recovery, reviews/exports, settings, and backup/restore. Preserve existing models and API contracts until a reviewed migration changes them.

Bind to loopback by default. Keep credentials in ignored local configuration. Authenticate all private routes, enforce ownership, validate DTOs, and redact logs. Uploads and exports must be served through authorized handlers from storage outside the checkout. Preserve working package versions and document real commands when imported.

Follow [the import checklist](../../docs/IMPORT.md).
