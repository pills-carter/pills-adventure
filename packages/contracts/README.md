# Shared contracts (optional)

Reserve this directory for small TypeScript request/response types genuinely shared by the web and API apps. Add a package only when duplication justifies it; this baseline has no workspace package configuration.

Do not export Prisma clients, database models containing password hashes, server configuration, tokens, or secrets to the frontend. Shared TypeScript types do not replace runtime validation at the API boundary.
