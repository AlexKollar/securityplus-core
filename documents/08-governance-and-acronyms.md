# Governance, Risk, Compliance — and the Acronym Glossary (Security+ SY0-701)

## Policies, Standards, Procedures, Guidelines

The governance ladder, broadest first:

- **Policy** — the organization's official position, set by leadership: *what* and *why*. ("Data must be protected according to its classification.")
- **Standard** — mandatory specifics that implement a policy: *which* technologies and settings. ("AES-256 for data at rest.")
- **Procedure** — step-by-step instructions: *how*, in order.
- **Guideline** — recommended practice; helpful, not mandatory.

Exam sorting trick: mandatory = policy/standard/procedure; optional advice = guideline.

Policy documents you'll be asked to recognize: acceptable use policy (AUP), information security policy, business continuity policy, incident response policy, software development lifecycle (SDLC) policy, and change management policy.

## Change Management

Why security cares: most outages and many breaches arrive as "changes." The process: request, impact analysis, approval (change advisory board for the significant), testing, a **backout plan**, implementation in a maintenance window, documentation. **Change management** questions usually test the backout plan and the approval step — skipping either is the wrong answer.

## Risk Governance Artifacts

- **Risk register** — the master list of risks with owner, likelihood, impact, and response for each.
- **Risk matrix / heat map** — likelihood on one axis, impact on the other, colored cells (red/amber/green) to visualize which risks demand action first.
- **Risk assessment reports** — periodic formal analysis feeding the register; owners assigned per risk, never "IT" in the abstract.
- **Key risk indicators (KRIs)** — metrics watched to see a risk growing (patch latency, phishing click rate).

## Compliance and Privacy

- **Compliance** — meeting external obligations (law, regulation, contract) and internal policy. Compliance reports and audits verify; penalties for failure are fines, sanctions, and lost business.
- **GDPR** — the EU's privacy regulation: lawful basis for processing, data subject rights (access, erasure — the "right to be forgotten"), breach notification to the regulator within **72 hours**, and fines that scale with global turnover.
- **CCPA/CPRA** — California's privacy law: consumer rights to know, delete, and opt out of the *sale* of personal information.
- **PCI DSS** — a contract standard (not a law) for cardholder data, imposed by the card brands.
- Privacy vocabulary: **data subject** (the person), **controller** (decides why/how data is processed), **processor** (processes on the controller's behalf), **data minimization** (collect only what you need), **purpose limitation** (use it only for the stated purpose).
- **Privacy impact assessment** — analysis performed before a new use of personal data.
- Global reality: privacy law is jurisdictional — data crossing borders carries the rules of where it lives and whose it is.

## Data Roles and Handling

- **Data owner** — accountable executive for a data set; **data custodian/steward** — implements the owner's rules day to day; **data protection officer (DPO)** — the privacy role GDPR formally requires for many organizations.
- **Data lifecycle** — creation, storage, use, sharing, archiving, destruction. Destruction methods by sensitivity: clear (overwrite), purge (degauss, cryptographic erase), destroy (shred, incinerate) — with a **certificate of destruction** as the audit evidence.
- **Information classification and labeling** make handling rules enforceable: people can't protect what they can't identify.

## Third-Party and Supply-Chain Governance

- Vendor risk assessments and security questionnaires before onboarding; **right-to-audit clauses** in contracts.
- **MSA / SLA / MOU / MOA / BPA** — the agreement family: master service agreement, service-level agreement (measurable performance), memorandum of understanding/agreement (intent), business partners agreement.
- Supply-chain risk: a compromised vendor update is your incident too — monitor vendor security posture continuously, not once at signing.

## Acronym Glossary — High-Frequency Retrieval Targets

Quick-lookup expansions for the acronyms students search mid-study. Endpoint detection and response is EDR; security information and event management is SIEM; security orchestration, automation, and response is SOAR; extended detection and response is XDR.

- **AAA** — authentication, authorization, accounting
- **ABAC** — attribute-based access control
- **ACL** — access control list
- **AES** — Advanced Encryption Standard
- **AH** — Authentication Header (IPsec)
- **ALE** — annualized loss expectancy
- **APT** — advanced persistent threat
- **ARO** — annualized rate of occurrence
- **BCP** — business continuity plan
- **BEC** — business email compromise
- **BIA** — business impact analysis
- **BYOD** — bring your own device
- **CA** — certificate authority
- **CCPA** — California Consumer Privacy Act
- **CIA triad** — confidentiality, integrity, availability
- **CRL** — certificate revocation list
- **CSRF** — cross-site request forgery
- **CVE** — Common Vulnerabilities and Exposures
- **CVSS** — Common Vulnerability Scoring System
- **DAC** — discretionary access control
- **DDoS** — distributed denial of service
- **DHCP** — Dynamic Host Configuration Protocol
- **DLP** — data loss prevention
- **DMARC** — Domain-based Message Authentication, Reporting, and Conformance
- **DNSSEC** — Domain Name System Security Extensions
- **DPO** — data protection officer
- **DRP** — disaster recovery plan
- **EDR** — endpoint detection and response
- **ESP** — Encapsulating Security Payload (IPsec)
- **FAR** — false acceptance rate
- **FRR** — false rejection rate
- **GDPR** — General Data Protection Regulation
- **HMAC** — hash-based message authentication code
- **IaC** — infrastructure as code
- **ICS** — industrial control systems
- **IDS / IPS** — intrusion detection / prevention system
- **IoT** — Internet of Things
- **IPsec** — Internet Protocol Security
- **KDC** — Key Distribution Center (Kerberos)
- **MAC (access control)** — mandatory access control
- **MFA** — multifactor authentication
- **MTBF** — mean time between failures
- **MTTR** — mean time to repair
- **NAC** — network access control
- **NGFW** — next-generation firewall
- **OCSP** — Online Certificate Status Protocol
- **OIDC** — OpenID Connect
- **OSINT** — open-source intelligence
- **PAM** — privileged access management
- **PCI DSS** — Payment Card Industry Data Security Standard
- **PEP** — policy enforcement point (zero trust)
- **PFS** — perfect forward secrecy
- **PKI** — public key infrastructure
- **PUP** — potentially unwanted program
- **RADIUS** — Remote Authentication Dial-In User Service
- **RAT** — remote access trojan
- **RBAC** — role-based access control
- **RPO** — recovery point objective
- **RTO** — recovery time objective
- **SAML** — Security Assertion Markup Language
- **SCADA** — supervisory control and data acquisition
- **SIEM** — security information and event management
- **SLE** — single loss expectancy
- **SOAR** — security orchestration, automation, and response
- **SOC** — security operations center
- **SSO** — single sign-on
- **TACACS+** — Terminal Access Controller Access-Control System Plus
- **TOTP** — time-based one-time password
- **TTP** — tactics, techniques, and procedures
- **UTM** — unified threat management
- **VM escape** — breaking out of a guest VM to the host
- **WAF** — web application firewall
- **XDR** — extended detection and response
- **XSS** — cross-site scripting

If an acronym isn't here, check the doc for its topic — each expansion is introduced where it's taught.
