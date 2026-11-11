# Cryptography (Security+ SY0-701)

## Symmetric vs Asymmetric

**Symmetric** — one shared key encrypts and decrypts. Fast, ideal for bulk data; the problem is getting the key to both sides safely.

- **AES** — the standard block cipher; key sizes 128/192/256 bits. AES-256 is the answer the exam wants for strong symmetric encryption.
- **DES** — legacy 56-bit key; broken by brute force. Retired.
- **3DES** — DES applied three times; legacy, slow, being retired.
- **ChaCha20** — modern stream cipher, common in TLS on devices without AES hardware acceleration.
- Modes matter: **ECB** leaks patterns (identical plaintext blocks → identical ciphertext) and is effectively never the right answer; CBC, GCM, and CTR are the serious modes. **GCM** adds integrity (authenticated encryption) — AES-GCM is a favorite pairing.

**Asymmetric** — a mathematically linked key pair: public key encrypts (or verifies), private key decrypts (or signs). Slow; used for key exchange, signatures, and small payloads.

- **RSA** — factoring-based; keys 2048+ bits.
- **Diffie-Hellman (DH / ECDH)** — key *exchange*, not encryption itself: two parties derive a shared secret over a public channel.
- **ECC (elliptic curve)** — same security at smaller key sizes (P-256 ≈ RSA-3072 strength class); phones and TLS prefer it.
- **DSA / ECDSA** — signature algorithms.
- **Hybrid encryption** is the real-world answer: asymmetric crypto exchanges a fresh symmetric key, symmetric crypto moves the data. TLS works exactly this way.

## Hashing

A hash is a one-way fingerprint: fixed-length output, deterministic, avalanche on any input change. Hashes protect **integrity**, never confidentiality.

- **MD5** — 128-bit; collision-broken. Legacy only, never for security decisions.
- **SHA-1** — 160-bit; collision-broken (SHAttered), retired for certificates.
- **SHA-2 family** — SHA-256 and SHA-512 are the exam standards.
- **SHA-3** — a different construction (sponge), standardized as the next generation.
- **HMAC** — a hash keyed with a secret: integrity *plus* authenticity between parties sharing the key.
- **Salting** — a unique random value stored with each password hash, so identical passwords produce different hashes and precomputed rainbow tables die. Salting does not slow an attacker down per-guess — that is **key stretching**.
- **Key stretching / slow KDFs** — bcrypt, PBKDF2, scrypt, and Argon2 deliberately make each password guess expensive, blunting dictionary attacks. (navi-hashlab demos salt + stretching side by side; navi-cryptex computes the raw hashes.)

## Digital Signatures and PKI

- **Digital signature** — hash the data, encrypt the hash with the sender's *private* key. Anyone verifies with the public key: authenticity, integrity, and non-repudiation in one move.
- **Certificate** — binds a public key to an identity, signed by a **certificate authority (CA)**. X.509 is the certificate format.
- **Chain of trust** — root CA (offline, self-signed, pre-trusted) → intermediate CAs → end-entity certificates. Browsers ship root stores.
- **Certificate types** — validation levels: **DV** (domain control only), **OV** (organization vetted), **EV** (extended vetting). By name: **wildcard** (`*.example.com`, one level), **SAN** (multiple names in one cert), **code-signing** (software), **email** (S/MIME), root vs intermediate vs end-entity.
- **Validation status** — **CRL** (published revocation list) vs **OCSP** (real-time status query); OCSP stapling lets the server present a recent status proof.
- **Key escrow** — a third party holds a copy of a private key for recovery (with all the trust questions that implies).
- **Wildcard and SAN traps** — a wildcard private key copied to many servers multiplies the blast radius of one theft.

## Key Exchange and Perfect Forward Secrecy

- In-band exchange (inside the protected channel protocol, e.g., TLS's ECDHE) vs out-of-band (verify fingerprints over a different channel).
- **Ephemeral keys** — fresh per session. **Perfect forward secrecy (PFS)**: because session keys are ephemeral (ECDHE), stealing the server's long-term private key later does not decrypt recorded past sessions.
- **Key length math the exam loves:** symmetric 128-bit ≈ asymmetric RSA 3072-bit ≈ ECC 256-bit in practical strength — that's why ECC wins on constrained devices.

## Cryptographic Attacks (Concept Level)

- **Collision** — two inputs, one hash; breaks integrity uses of MD5/SHA-1.
- **Birthday attack** — collisions arrive after about √n tries (a 128-bit hash gives ~64-bit collision resistance).
- **Brute force / dictionary** — against passwords and weak keys; mitigated by length, salt, stretching.
- **Rainbow tables** — precomputed hash chains; defeated by salting.
- **Downgrade attack** — forcing a protocol to an older, weaker version (the negotiation is the target).
- **Key stretching bypass isn't one** — remember the defense side too: the exam pairs every attack with its countermeasure. Salting defeats rainbow tables; stretching defeats fast guessing; PFS defeats later key compromise; authenticated modes (GCM) defeat tampering.
