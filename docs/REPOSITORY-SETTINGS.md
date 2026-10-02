# GitHub owner setup

## Observed on 2026-10-02 before initialization

The authenticated GitHub API showed this repository as public with default branch `main`. The branch metadata reported `protected: false`, and the repository rulesets endpoint returned an empty list. No open pull requests were present.

The only commit was [the verified initial commit](https://github.com/pills-carter/pills-adventure/commit/f02ebf9c5ba97386532bf7750f86d4fcde90b4fb), dated 2022-10-17, containing a two-line README. A verified signature authenticates a commit's signing provenance; it does not establish application security.

The following are owner setup tasks. Committing this file, CODEOWNERS, or SECURITY.md does not activate them. These settings were not changed by this baseline.

## Configure now

- [ ] Protect `main` with a branch rule/ruleset: require a pull request, block force pushes and deletion, and require resolved review conversations.
- [ ] For a sole maintainer, do not require an independent approval that nobody can supply. When another reviewer joins, require one approval, code-owner review, and dismissal of stale approvals.
- [ ] Enable private vulnerability reporting and verify the **Report a vulnerability** flow. Until enabled, SECURITY.md explains the fallback; no private email is invented.
- [ ] Review available secret scanning and push protection settings and enable them. Check alert delivery to the owner. Do not assume an ignore rule replaces scanning.
- [ ] Review repository access and account recovery/2FA. Keep admin access narrow.
- [ ] Restrict Actions permissions to what is needed; use read-only workflow tokens by default and avoid allowing workflows to approve their own pull requests.

## Configure after app import

- [ ] Add real CI for lint, types, relevant tests, and builds. Require only status checks that actually exist and have run successfully.
- [ ] Add dependency updates for the selected package manager and actual manifest directories; enable available dependency alerts/review.
- [ ] Add appropriate code scanning for the imported languages and build layout.
- [ ] Pin Actions dependencies to reviewed full commit SHAs and maintain those pins.
- [ ] Choose an explicit licence before advertising the project as open source.

## Verify

Re-read branch/ruleset metadata after setup, test a disposable PR against the rules, and confirm security reporting availability. Record outcomes without credentials. Until verified, describe controls as pending rather than enabled.

References: [rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets), [private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/configuring-private-vulnerability-reporting-for-a-repository), and [secret scanning](https://docs.github.com/en/code-security/secret-scanning/introduction/about-secret-scanning).
