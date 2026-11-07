# Privacy notice — NEXUS PC OPTIMIZER

NEXUS is freeware. **All PC maintenance features work without registering and without any network connection.**
There is no hidden telemetry.

## Data inventory

| Domain | What | Where | Protection | Retention |
|---|---|---|---|---|
| User identity | Registration e-mail, language, status, dates | Railway PostgreSQL `registered_users` | AES-256-GCM encryption at rest; lookup via keyed HMAC; masked in admin views | Until you delete your account; unverified registrations deleted after 7 days |
| License credentials | Serial (22 Base58 chars) | `licenses` | Only HMAC-SHA256 hash (versioned key) — not reversible, not viewable by anyone | Revoked licenses kept (hash only) for revocation integrity |
| Installation references | Random GUID created by the app | `installation_references` | Only a keyed hash is stored; app version and last check date | Deleted after 24 months without a check, or with your account |
| Operational events | Daily counters (activations, verification success, version distribution, optional module error counts) | `application_statistics` | No identifiers | 24 months |
| Security events | Event type, keyed hash of IP | `security_events` | IP never stored in clear | 180 days |
| Administrative audit | Who (masked admin e-mail), what, when, why | `admin_audit_logs` | Append-only (app + database trigger); no user e-mail addresses | Permanent (accountability) |
| On your PC | Settings, activity log, reports | `%LOCALAPPDATA%\NexusPCOptimizer` | Serial encrypted with Windows DPAPI (current user) | Until you delete it |

## What is sent, and when

| When | Data sent | Opt-in? |
|---|---|---|
| You register | E-mail, chosen language | You start it |
| License activation / weekly check | Serial, random installation reference, app version | Only if you activated a serial |
| Notification Centre / version policy | App version, channel | Only if the cloud service is configured |
| NEXUS update check | Nothing personal (downloads public GitHub release files) | — |
| Optional diagnostics (weekly) | App version, **count** of failed operations per module, self-update success/failure counts | **Off by default** — Settings › Privacy |

**Never sent:** installed-software lists, file names or paths, documents, browser history, cookies, passwords,
screenshots, CPU/RAM usage history, memory contents, hardware serial numbers, Windows account data, local logs.

## Your rights (from Account & License)
- **Copy of my data** – e-mailed after you confirm a link.
- **Replace a lost serial** – a new serial is issued after e-mail confirmation; the old one stops working.
- **Delete my account** – e-mail erased, licenses revoked, installation references removed, after e-mail confirmation.
- Disable optional diagnostics at any time (Settings).

Administrators can see masked e-mail addresses only; revealing a full address requires a stated reason and is
recorded in the audit history. Nobody can view a serial number after it is issued.
