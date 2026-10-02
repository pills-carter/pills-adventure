# Repository boundary decision

Status: baseline architectural recommendation, 2026-10-02.

## Decision

Keep Pills Performance in this repository. Keep AegisAgent separate, and keep ecommerce/API-test work outside this repository. The web and API for Pills Performance belong together because they serve the same product and often require coordinated changes.

## Evidence and limits

Before initialization, [pills-adventure](https://github.com/pills-carter/pills-adventure) was public, on `main`, with only its verified 2022-10-17 initial commit and a 32-byte README. No application source was present.

[aegisagent-workspace](https://github.com/pills-carter/aegisagent-workspace) was public, on `main`, with a README-only initial commit dated 2026-06-24. Its README describes an AegisAgent web app for NHID and bots monitoring. This establishes a different intended product, not a working implementation or shared dependency.

The intended Pills Performance scope comes from the owner's existing local-app requirements. Repository metadata alone cannot prove what is implemented on the owner's computers. Private repository findings are kept out of this public document.

## Why separate

| Project type | Primary concern | Reason for an independent repository |
| --- | --- | --- |
| Pills Performance | Personal routines, trading journal, training, reviews | Local data, coordinated web/API UX, private records |
| AegisAgent | Cloud/non-human identity and bot monitoring | Different permissions, integrations, threat model and release lifecycle |
| Ecommerce API tests | Testing shop endpoints and integrations | Different API contracts, test credentials, and access requirements |

Sharing TypeScript or NestJS is not enough reason to merge unrelated products. Keep secrets, permissions, releases, issue backlogs, and deployment decisions separate. Link related projects where appropriate without importing private test data or histories into a public repository.

Reconsider extracting a shared package only after a concrete, independently testable component is used by multiple projects. Share reviewed code through a versioned package or focused copy; never merge entire products solely to avoid a few duplicated helpers.
