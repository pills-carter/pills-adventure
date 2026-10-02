# Security policy

## Supported scope

The current repository baseline contains documentation and structure only. No runnable release is supported yet. After the app import, security fixes will target the latest maintained version on `main`; there is no older-version support commitment.

## Reporting a vulnerability

Do not disclose vulnerabilities, credentials, exploit details, or personal records in public issues or pull requests.

If GitHub displays **Security → Report a vulnerability**, use that private reporting flow for this repository. Its availability depends on the owner enabling private vulnerability reporting; this file does not enable it.

If that option is absent, use an already-established private channel to the owner, or open a public issue containing only a request to establish a private security contact. Do not include vulnerability details in that request. No security email or response-time commitment has been configured in this baseline.

A private report should include the affected commit/version, component, impact, minimal reproduction using synthetic data, and any suggested fix. Never send a working credential or a real personal database. Coordinate disclosure privately with the owner.

## Sensitive data exposure

If a credential is committed, revoke or rotate it first and invalidate affected sessions. Removing a file or adding an ignore rule does not remove it from history, forks, or existing clones. Notify the owner privately and coordinate any history cleanup; do not force-push a rewrite without approval. For personal data exposure, remove public access where possible and assess copies and affected records privately.

## Local application security requirements

- Bind web, API, and PostgreSQL services to loopback by default. LAN/phone access requires a separate review and TLS/session configuration.
- No public signup or shipped default admin password. Provision the owner locally and hash passwords; preserve the existing bcryptjs implementation until reviewed deliberately.
- Keep authentication tokens in appropriately configured HttpOnly cookies. Set an explicit SameSite policy and Secure under HTTPS; never log tokens. Review local HTTP exceptions before enabling network access.
- Validate Origin/CSRF protections for cookie-authenticated state-changing requests. Use exact allowed frontend origins; CORS alone is not CSRF protection.
- Check authentication and ownership on every private resource. Validate input, rate-limit login attempts, and return errors without secrets or stack traces.
- Store uploads outside public web paths, validate size and content, generate server-side filenames, block path traversal, and authorize downloads.
- Keep secrets on the backend. No secrets in `NEXT_PUBLIC_*`, client bundles, shared contracts, fixtures, or logs.
- Keep backups private and protected at rest. Verify restore against a disposable database before replacing live data.

These are acceptance requirements, not claims about controls already implemented. Track repository settings separately in [the setup checklist](docs/REPOSITORY-SETTINGS.md).
