# Security Fundamentals (Security+ SY0-701)

## The CIA Triad

Every security decision protects one or more of three properties:

- **Confidentiality** — information is only accessible to authorized people and systems. Encryption, access controls, and classification protect it.
- **Integrity** — information is accurate, complete, and unchanged by unauthorized hands. Hashing, digital signatures, and version control protect it.
- **Availability** — information and systems are reachable when authorized users need them. Redundancy, backups, and capacity planning protect it.

Exam habit: when a scenario names a control, ask which leg of the triad it serves first. A hash check serves integrity, not confidentiality — hashing hides nothing.

## AAA: Authentication, Authorization, Accounting

- **Authentication** — proving an identity claim: passwords, MFA, certificates, biometrics.
- **Authorization** — what that proven identity is allowed to do: permissions, group membership, policy.
- **Accounting** — recording what was done: logs, audit trails, session records.

The exam also uses AAA for the RADIUS/TACACS+ framework — the same three words, run by a server. Accounting is the leg people forget; it is why logging questions exist.

## Zero Trust

Zero trust removes the idea of a trusted internal network. Its motto: never trust, always verify — every request is authenticated and authorized as if it came from an untrusted network.

- **Control plane** — where policy decisions are made and enforced: the **policy engine** (evaluates trust algorithms and inputs), the **policy administrator** (issues the decision/commands), and adaptive identity signals feeding them.
- **Data plane** — where traffic actually flows and is gated: the **policy enforcement point (PEP)** sits in front of each resource and allows or blocks based on the control plane's decision. Subjects pass through implicit trust zones only after the PEP admits them.

Memory hook: the control plane *decides*, the data plane *does*. If a question asks where enforcement happens, the answer is the PEP in the data plane.

## Threat Actors and Their Attributes

Classify an actor by **resources/funding**, **sophistication/capability**, **motivation**, and **intent**:

- **Nation-state** — government-backed; highest funding and sophistication; long-dwell espionage or strategic disruption (APT behavior).
- **Organized crime** — financially motivated; well funded; ransomware and fraud at scale.
- **Hacktivist** — ideologically motivated; defacement, leaks, DDoS as protest.
- **Insider threat** — authorized access abused, maliciously or negligently; the access is legitimate, the use is not.
- **Shadow IT** — not an actor but a condition: unsanctioned systems staff deploy themselves, outside security's visibility.
- **Competitor / criminal syndicate / individual hacker** — vary widely in funding and skill; motivation separates them (advantage, profit, curiosity/notoriety).

## Threat Intelligence

- **OSINT** — open-source intelligence: public feeds, blogs, disclosures, social media.
- **Threat feeds and ISACs** — industry sharing groups (e.g., FS-ISAC for finance) distribute indicators and TTPs.
- **Dark web monitoring** — watches criminal markets and forums for leaked data and planned campaigns.
- **Vulnerability databases** — CVE/NVD catalog known weaknesses; pair with exploit intelligence before prioritizing.
- Intelligence types: **strategic** (executive, long-term), **operational** (campaign-level), **tactical** (TTPs and indicators for defenders).

## Security Controls: Type and Category

Two independent axes — exam questions mix them deliberately.

By **category** (who/what implements it):

- **Managerial** — policies, risk assessments, governance.
- **Operational** — people-driven: training, procedures, guards.
- **Technical** — technology: firewalls, encryption, MFA.
- **Physical** — locks, fences, cameras, bollards.

By **type** (what it does in time):

- **Preventive** — stops it before it happens (firewall rules, access control).
- **Deterrent** — discourages the attempt (signage, visible cameras).
- **Detective** — notices it happening or after (IDS alerts, audit logs).
- **Corrective** — restores after an incident (backups, patching).
- **Compensating** — an alternate control used when the primary one can't be met.
- **Directive** — instructs behavior (policy documents, training requirements).

A camera is physical/detective (or deterrent when visible); a written policy is managerial/directive. Name both axes when the question gives you room.

## Other Core Vocabulary

- **Risk** — likelihood × impact of a threat exploiting a vulnerability.
- **Threat** — anything with potential to cause harm; a **vulnerability** is the weakness it exploits.
- **Zero-day** — a vulnerability unknown to the vendor, or exploited before a patch exists.
- **Data classifications** — public, internal, confidential, restricted (names vary; sensitivity rises left to right). Data states: at rest, in transit, in use — each state gets different controls.
