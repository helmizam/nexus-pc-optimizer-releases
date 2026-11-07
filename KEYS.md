# Release signing keys

NEXUS release manifests (`manifest.json`) are signed with ECDSA P-256 / SHA-256 (IEEE P1363 signature, base64,
in `manifest.json.sig`). The NEXUS application contains these public keys and refuses any update whose manifest
signature does not verify, or whose installer SHA-256 does not match the signed manifest.

| Key ID | Curve | Public key (X, Y — base64url) |
|---|---|---|
| `nexus-release-1` | P-256 | X `XFEO5lU9DyfoHluUWIcWVQpeChgKUMSkOSFF9FNADEM` · Y `1iMWrmeZcoPFzhrksHBeNTRdOOEdvlciA0CWMoKKE0M` |

Key rotation: a new key is added to the application before it is used, so older versions can still verify it during
the transition.
