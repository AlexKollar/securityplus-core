# Identity and Access Management (Security+ SY0-701)

## Authentication Factors and MFA

- **Something you know** — password, PIN.
- **Something you have** — smart card, hardware token, phone app, security key.
- **Something you are** — biometrics: fingerprint, face, iris, voice.
- **Somewhere you are** — location/geolocation as a supporting signal.
- **Something you do** — behavioral patterns.

**MFA** requires two or more *different factor types*. Two passwords are not MFA; a password plus a TOTP code is. TOTP (time-based one-time password) codes roll every ~30 seconds from a shared secret; HOTP is counter-based. Push approvals are convenient but vulnerable to MFA fatigue attacks — number matching is the mitigation.

**Passwordless** authentication (FIDO2/WebAuthn security keys, platform authenticators) removes the shared secret entirely: the private key never leaves the device, and phishing resistance is the headline benefit.

## Password Policies and Account Hardening

- Length beats complexity theater: longer passphrases resist brute force exponentially.
- Policy controls the exam lists: minimum length, complexity, history (no reuse), maximum/minimum age, lockout threshold and duration, and screening new passwords against known-breached lists.
- Credential attacks this defeats: brute force, dictionary, **password spraying** (one common password, many accounts — stays under per-account lockout), credential stuffing (breached pairs replayed).
- Vaults and managers: a **password manager** per user; a **privileged access management (PAM)** vault for admin credentials, with check-out, rotation, and session recording.

## Biometrics — Accuracy Vocabulary

- **False acceptance rate (FAR)** — an impostor is accepted. The dangerous error.
- **False rejection rate (FRR)** — a legitimate user is rejected. The annoying error.
- **Crossover error rate (CER/EER)** — the point where FAR equals FRR; the single-number accuracy comparison for systems. Lower is better.

## Access Control Models

- **RBAC (role-based)** — permissions attach to roles; users inherit by role membership. Scales best; the enterprise default.
- **ABAC (attribute-based)** — decisions from attributes of user, resource, action, and environment (department, clearance, time of day, device posture). Most flexible, most complex.
- **MAC (mandatory)** — the system enforces labels/classifications; users cannot override. Government/classified systems.
- **DAC (discretionary)** — the resource owner decides who gets access. Home file-sharing is the everyday example.
- **Rule-based** — access granted or denied by administrator-set conditions (firewall ACLs are the classic case).
- **Least privilege** and **separation of duties** overlay every model: no one holds more access than the job needs, and no one person controls a sensitive process end to end.

## ACLs and Permissions

- An **access control list** names, per resource, who may do what. Filesystem ACLs, firewall rules, and router ACLs are the same idea at different layers.
- Permission models: read/write/execute on files; allow/deny ordering matters — first match wins in most firewall ACLs, with an implicit deny at the end.
- Periodic **access reviews / attestation** catch privilege creep: access granted for a project that quietly becomes permanent.

## Federation, SSO, and Protocols

- **SSO (single sign-on)** — authenticate once, access many connected systems. Convenience plus a single strong gate to defend.
- **Federation** — trust across organizations/domains so identities from one are accepted by another.
- **SAML** — XML-based assertions; the enterprise web SSO standard (identity provider asserts identity to the service provider).
- **OAuth 2.0** — an *authorization* framework: delegated access via tokens ("let this app read my photos"), not itself authentication.
- **OpenID Connect (OIDC)** — the authentication layer built on top of OAuth 2.0; adds the ID token. Exam trap: "OAuth for login" really means OIDC.
- **Kerberos** — ticket-based authentication in Windows domains: KDC issues ticket-granting tickets; service tickets grant access. Time sync matters (tickets expire).
- **RADIUS** — network access AAA (802.1X, VPN) over UDP; **TACACS+** — device administration AAA over TCP, separates all three AAA functions and encrypts the full payload. Diameter is RADIUS's successor in telecom contexts.

## Privileged Access and Account Lifecycle

- **Provisioning/deprovisioning** — accounts created on hire, changed on transfer, disabled immediately on departure. Orphaned accounts are a standing audit finding.
- **Just-in-time access** — privileged rights granted for a window, then revoked, instead of standing admin rights.
- **Account audits** — review dormant accounts, shared accounts, and service accounts (non-human, often over-privileged and unrotated).
- **Group-based provisioning** and role mining keep RBAC honest as organizations change.

Hands-on cross-ref: navi-hashlab covers how stored credentials fall (hashing, salting, cracking) — the reason these controls exist.
