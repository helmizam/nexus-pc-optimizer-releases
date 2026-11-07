# Security policy

## Supported versions
Only the latest release receives fixes. NEXUS shows a notice when your version is no longer supported; it never
disables local maintenance features because a version is outdated.

## Reporting a vulnerability
Please do **not** open a public issue. Report privately through GitHub's **"Report a vulnerability"** (Security tab)
of this repository, with steps to reproduce and the NEXUS version (Settings › About).

## How releases are protected
- Built and tested by an automated pipeline from a private repository; only approved artifacts are published here.
- Each release has a signed manifest and SHA-256 checksum; the in-app updater verifies both before installing.
- Updates never restart Windows automatically and never run without your confirmation.
