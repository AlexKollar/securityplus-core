# Security Architecture and Design (Security+ SY0-701)

## Architecture Models

- **Cloud shared responsibility** — the provider secures the cloud itself; the customer secures what they put *in* it. The dividing line moves by model: **IaaS** (customer owns OS, apps, data), **PaaS** (provider takes the OS/runtime), **SaaS** (provider runs nearly everything except data, accounts, and configuration). Misconfiguration by the customer is the most common cloud failure in every model.
- **Virtualization** — a hypervisor runs many guest VMs on one host. Type 1 (bare metal) vs Type 2 (hosted). Risks: **VM escape** (breaking out to the host/hypervisor), **VM sprawl** (unmanaged forgotten VMs), resource reuse between tenants.
- **Containers** — share the host kernel, isolated by namespaces/cgroups; lighter than VMs, but a kernel flaw is shared by all. Container image hygiene and orchestration (Kubernetes) security are the control points.
- **Infrastructure as Code (IaC)** — infrastructure declared in templates and built by automation: consistent, reviewable, repeatable. The risk is a flawed template replicated everywhere at machine speed.
- **Microservices and APIs** — many small services over network APIs; each service boundary is an authorization boundary.
- **Serverless** — functions run on demand; the provider owns the runtime, you own code, data, and permissions. Short-lived doesn't mean risk-free: over-privileged function roles are the classic flaw.
- **Air gap** — physical isolation from other networks; used for the most sensitive systems. Data crosses only by controlled media.
- **Centralized vs decentralized** — know the trade: central control and visibility vs single point of failure and blast radius.

## Secure Protocols by Use

Match the protocol to the job — a favorite exam format:

- **Email** — S/MIME (signing/encrypting messages), SPF, DKIM, DMARC (sender authentication, anti-spoofing).
- **Web** — HTTPS over TLS; HSTS forces it.
- **File transfer** — SFTP (over SSH) and FTPS (FTP over TLS) replace plaintext FTP.
- **Remote access** — SSH replaces Telnet; IPsec or TLS VPNs for network-level access.
- **Directory** — LDAPS (LDAP over TLS) instead of plaintext LDAP.
- **DNS** — DNSSEC signs records (authenticity); DoH/DoT encrypt queries (confidentiality) — different problems, both tested.
- **Time** — secure NTP matters because logs and certificates depend on trustworthy time.
- **Voice/media** — SRTP encrypts RTP streams.
- **Network management** — SNMPv3 adds authentication and encryption SNMPv1/v2c lacked.

## Embedded, IoT, and Specialized Systems

- **IoT constraints** — limited CPU/memory, no patch path, default credentials, long service life past vendor support. Controls: segmentation, disable unused services, change defaults, monitor.
- **Embedded systems and RTOS** — real-time operating systems prioritize deterministic timing; security tooling often can't run on them.
- **ICS / SCADA** — industrial control systems; availability and safety outrank confidentiality, patching windows are rare, and the Purdue-style segmentation model keeps control networks isolated from IT.
- **RTOS/PLC/HMI vocabulary** — the exam asks recognition, not engineering: know what a PLC controls and why these systems can't simply be patched like servers.

## Physical Security

- **Barriers and access** — fences, gates, bollards (stop vehicles), access badges, mantraps/access control vestibules (one person, verified, at a time).
- **Sensors** — motion, infrared, pressure, ultrasonic; cameras (with lighting as their partner control).
- **Deterrence and detection** — signage deters; alarms and video surveillance detect; Faraday cages block RF for sensitive spaces.
- **Secure areas** — server rooms and data centers layer controls: badge + PIN/biometric, visitor logs, locked racks/cages.
- **Environmental** — temperature/humidity monitoring, fire suppression appropriate to electronics, cable locks and screen privacy filters at the small end.
- **Secure disposal of media** — see governance doc: wiping, degaussing, destruction, certification of destruction.

## Resilience and Recovery Design

- **Backups** — full, incremental (since last backup of any type), differential (since last full). The **3-2-1 rule**: three copies, two media types, one offsite/offline — the offline copy is what survives ransomware. **Snapshots** are point-in-time images for fast rollback, not a full backup strategy alone.
- **Redundancy** — redundant power (UPS, generators), RAID for disks (RAID is availability, *not* backup), dual ISPs, geographic dispersion.
- **High availability** — **load balancers** spread work across servers; **clustering** makes nodes act as one service, failing over as a unit.
- **Failover and sites** — hot site (ready now), warm site (equipment present, needs data/config), cold site (space and power only). Cost and recovery speed trade directly.
- **Capacity planning** — people, technology, and infrastructure sized for growth and for surge (including attack) conditions.
- **Testing the plan** — tabletop exercises, simulations, and actual failover tests; an untested backup is a hope, not a control.
