# Threats, Vectors, and Attacks (Security+ SY0-701)

## Malware Families

- **Virus** — needs a host file and usually a user's action to spread.
- **Worm** — self-propagates across networks with no user action. (Hands-on contrast: this is why segmentation exists.)
- **Trojan** — malicious code disguised as legitimate software.
- **RAT (remote access trojan)** — gives the attacker interactive control of the machine.
- **Ransomware** — encrypts data (or threatens publication — double extortion) for payment.
- **Keylogger** — records keystrokes to steal credentials and content.
- **Spyware** — quietly monitors and exfiltrates user activity.
- **Logic bomb** — dormant code that fires on a condition: a date, an event, an absence.
- **Rootkit** — hides deep in the OS (kernel-level is hardest to detect) to maintain stealthy persistence.
- **Backdoor** — a hidden access path that bypasses normal authentication.
- **Bloatware / PUP** — unwanted bundled software; a hygiene and attack-surface issue.

Delivery and persistence vocabulary: **dropper** (installs the payload), **loader** (fetches and runs later stages), **shellcode** (small payload code, often the first stage), **fileless malware** (lives in memory, scripts, and legitimate tools — "living off the land").

## Social Engineering

- **Phishing** — fraudulent messages soliciting clicks or credentials. Variants: **spear phishing** (targeted at a person/group), **whaling** (executives), **smishing** (SMS), **vishing** (voice calls).
- **Business email compromise (BEC)** — a compromised or convincingly spoofed executive/vendor mailbox used to redirect payments or data.
- **Pretexting** — an invented scenario ("I'm from IT, I need your code") to extract cooperation.
- **Baiting** — a lure: a poisoned USB drop, a "free" download.
- **Typosquatting / brand impersonation** — look-alike domains and identities that borrow trust.
- **Watering hole** — compromising a site the targets already visit.
- **Influence and disinformation campaigns** — shaping perception at scale rather than compromising a machine.
- **Newer forms to recognize:** **quishing** (phishing via QR code), **deepfake voice/video** impersonation on calls, MFA-fatigue (push bombing) — flooding approval prompts until the user taps yes.
- Influence levers the exam names: authority, urgency, scarcity, fear, greed, likability, social proof, consistency.

## Application Attacks

- **Injection** — untrusted input executed as code or query: SQL injection, LDAP injection, XML injection. (Your navi-weblab drills these in a lab.)
- **XSS (cross-site scripting)** — attacker script runs in a victim's browser: stored (persisted on the server), reflected (in the response), DOM-based (client-side).
- **CSRF** — the victim's authenticated browser is tricked into sending a forged request; **SSRF** — the *server* is tricked into making requests to internal targets.
- **Privilege escalation** — gaining higher rights than granted, vertically or horizontally.
- **Broken access control / IDOR** — reaching objects by changing an identifier the app failed to authorize.
- **Race condition** — exploiting timing between check and use (TOCTOU).
- **Buffer overflow** — writing past a buffer's bounds to corrupt memory or execute code.
- **Pass-the-hash** — replaying a captured password hash instead of the password itself.
- **API attacks** — abusing exposed endpoints, missing rate limits, or excessive data exposure.
- **Directory traversal** — `../` sequences reaching files outside the web root.

## Network Attacks

- **DoS / DDoS** — denying service by exhaustion; DDoS distributes the flood across many sources (botnets), often with amplification (a small spoofed query triggers a large reply to the victim).
- **DNS poisoning** — corrupting a resolver's cache so a name resolves to the attacker's address; **domain hijacking** — seizing control of the domain registration itself.
- **On-path attack** (formerly man-in-the-middle) — the attacker sits between parties, relaying and reading/altering traffic.
- **Credential replay** — captured credentials or tokens reused verbatim against the service.
- **DNS spoofing, ARP poisoning, rogue DHCP** — layer-2/3 trust abuses steering traffic to the attacker on a local network.
- **Evil twin / rogue AP** — a fake wireless access point harvesting connections.
- **Bluetooth attacks** — Bluejacking (unsolicited messages), Bluesnarfing (data theft over Bluetooth).
- **RFID cloning and jamming** — copying badge signals or drowning wireless channels.
- **Zero-day exploitation** — attacking a vulnerability with no patch available.

## Indicators of Malicious Activity

What defenders actually watch for:

- **Account and authentication anomalies** — impossible travel, concurrent sessions from distant locations, repeated failed logins, logins at unusual hours.
- **Host indicators** — unexpected processes, new services or scheduled tasks, beaconing at regular intervals, resource consumption spikes, files appearing in odd locations.
- **Network indicators** — traffic to newly registered or known-bad domains, DNS tunneling patterns (long encoded subdomains), data exfiltration volumes, scanning behavior.
- **Published/looming signals** — threat intel matches (IPs, hashes, domains) against your logs; the term for the artifacts themselves is **indicators of compromise (IoCs)**.
- Behavioral framing: tools and behaviors persist longer than hashes — TTPs outlive IoCs, which is why mature detection keys on technique, not just signatures.

Hands-on cross-refs: navi-scribe parses the auth logs where failed-login patterns surface; navi-recon shows what an attacker's scan looks like from the inside.
