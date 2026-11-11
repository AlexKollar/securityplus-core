# Security Operations and Incident Response (Security+ SY0-701)

## Incident Response Process — Order Matters

The SY0-701 incident response process runs in this order:

1. **Preparation** — plans, playbooks, tools, training, and tabletop exercises *before* anything happens.
2. **Detection** — monitoring and alerts surface a potential incident.
3. **Analysis** — validate it: is it real, what is affected, how severe? (Some frameworks merge detection and analysis; the exam keeps both words — watch the options.)
4. **Containment** — stop the bleeding: isolate hosts, disable accounts, block indicators — short-term first, then long-term.
5. **Eradication** — remove the root cause: malware, persistence mechanisms, the compromised account or vulnerability.
6. **Recovery** — restore systems to production, patched and monitored, in phases.
7. **Lessons learned** — post-incident review: what failed, what worked, what changes. Its output feeds back into preparation.

Mnemonic discipline: containment never comes before analysis on the exam, and eradication never comes before containment. If a scenario says "the team isolated the server," the *next* step they ask about is eradication, not recovery.

## Digital Forensics Basics

- **Order of volatility** — collect the most fragile evidence first. From most to least volatile:
  1. CPU registers and cache
  2. RAM / system memory
  3. Network state and running processes (temporary system state)
  4. Disk and storage media
  5. Backups and archived/logged data (least volatile)
  Memory before disk: pulling the plug first destroys RAM evidence — a classic scenario trap.
- **Chain of custody** — documented, unbroken record of who held the evidence and when; gaps break legal admissibility.
- **Legal hold** — a directive to preserve data for litigation, overriding normal retention/deletion.
- **Imaging** — bit-for-bit copies verified by hash; work on the image, never the original. A **write blocker** prevents altering the source during acquisition.
- **Preservation vs acquisition vs analysis** — hold data safely, capture it faithfully, then examine the copy.

Hands-on echo: navi-scribe's timelines practice the log side of this — events in order, sources cited.

## The Monitoring Stack: SIEM, SOAR, EDR

- **SIEM (security information and event management)** — collects and correlates logs from everything; the detection and alerting brain. Correlation rules connect a failed-login burst to a successful login to an alert (navi-scribe flags by hand what a SIEM automates).
- **SOAR (security orchestration, automation, and response)** — playbooks that act on alerts: enrich, triage, contain — automation for the repetitive parts of response.
- **EDR (endpoint detection and response)** — deep telemetry and response on endpoints: process trees, file/registry changes, isolate-host and kill-process actions. **XDR** extends the same idea across email, network, identity, and cloud. **DLP** watches data itself — classifying and blocking sensitive content leaving via email, web, or USB.
- Supporting sources: **NetFlow**, **full packet capture**, **vulnerability scan reports**, and **threat feeds** all pour into this stack.

## Vulnerability Management

- **Scanning** — credentialed scans (logged in; deeper, more accurate) vs non-credentialed (the attacker's outside view). Agent-based scanning covers laptops off the network.
- **CVSS (Common Vulnerability Scoring System)** — a 0–10 severity score from exploitability and impact metrics. It measures *severity*, not your *risk*: a 9.8 on an isolated test box may matter less than a 7.5 on the payment server. Environmental context turns scores into priorities.
- **Penetration testing** — authorized humans simulating attack: rules of engagement, scope, and written authorization define it. Vocabulary: **known environment** (full info given), **unknown environment** (black box), **partially known** (between them).
- **Vulnerability response workflow** — identify, prioritize by score *and* exposure, remediate or accept with justification, verify by rescan.
- **False positives/negatives in scans** — a reported vuln that isn't there vs a real one the scanner missed; validation (and the pen test) keeps both honest.

## Hardening Baselines

- **Secure baselines** — a defined hardened configuration for each OS/app class; **benchmarks** (e.g., CIS) publish them; **configuration management** enforces them and flags drift.
- Practical hardening moves the exam rewards: disable unused ports/services, remove default accounts and credentials, least-functionality installs, patch cadence, application allow-listing, endpoint protection on, encryption at rest on.
- **Group Policy (Windows) and configuration profiles (MDM)** are the delivery mechanisms; **baseline deviation reports** are the detective control.

## Risk Management Terms

- **Risk assessment** — identify assets, threats, vulnerabilities; score by **likelihood × impact**. Quantitative (money values: SLE = asset value × exposure factor; ALE = SLE × annual rate of occurrence) vs qualitative (high/medium/low judgment).
- **Risk handling** — **accept** (knowingly live with it), **mitigate** (controls reduce it), **transfer** (insurance, outsourcing), **avoid** (stop the activity). Residual risk is what remains after controls.
- **Risk register** — the living list: risk, owner, likelihood, impact, response, status.
- **Business impact analysis (BIA)** — names critical processes and the numbers recovery lives by: **RTO** (recovery time objective — how fast service must return), **RPO** (recovery point objective — how much data loss, in time, is tolerable), **MTTR** (mean time to repair), **MTBF** (mean time between failures).
