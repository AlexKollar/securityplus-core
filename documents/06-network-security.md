# Network Security (Security+ SY0-701)

## Segmentation

- **Network segmentation** — splitting a network into zones (user, server, guest, IoT, management) with controlled crossings. Limits lateral movement: a compromised printer should not reach the domain controller.
- **VLANs** — logical segmentation at Layer 2; a VLAN is a broadcast domain. Segmentation becomes security when ACLs/firewall rules govern traffic *between* VLANs.
- **Microsegmentation** — policy enforced per workload, even inside one segment (host firewalls, cloud security groups, zero-trust style identity rules).
- **Air gap and jump servers** — the most sensitive zones are reached through a single hardened **jump box/bastion host**, and the most sensitive of all are physically isolated.
- **East-west vs north-south** — traffic between internal systems (east-west) is where segmentation and monitoring earn their keep; north-south crosses the perimeter.

## VPNs and Tunneling

- **IPsec** — Layer-3 VPN suite. Two modes: **transport** (host-to-host, payload protected) and **tunnel** (whole packet wrapped; site-to-site VPNs). Protocols: **AH** (integrity/authentication, no encryption) and **ESP** (encryption + integrity — the one actually used). IKE negotiates the security associations.
- **TLS VPN / client portal** — remote access over HTTPS; easier through firewalls, per-app granularity.
- **Site-to-site vs remote-access vs clientless** — know which deployment the scenario describes.
- **Split tunnel vs full tunnel** — split sends only corporate traffic through the VPN (less load, more risk surface); full tunnel routes everything (more control, more bandwidth). The exam tests the trade-off, not a preference.
- **Always-on VPN** and **SD-WAN** (software-defined WAN with centrally managed encrypted overlays) round out the vocabulary.

## Port Security and 802.1X

- **802.1X** — port-based network access control: a supplicant (device) asks, an authenticator (switch/AP) relays, an authentication server (RADIUS) decides. No credentials, no network — the wired port behaves like a locked door.
- **EAP** — the authentication framework 802.1X carries; EAP-TLS (certificate both sides) is the strongest common flavor.
- **Switch port hygiene** — disable unused ports, **DHCP snooping** (only trusted ports may answer DHCP), **dynamic ARP inspection** (validates ARP against the snooping table), storm control, and BPDU guard against rogue switches. (navi-netkit's port tables and navi-recon's scanner view are the hands-on side of this doc.)

## Firewalls and Filtering

- **Stateless packet filter** — rules on headers only, no connection memory.
- **Stateful firewall** — tracks connection state; return traffic for allowed sessions passes automatically.
- **NGFW (next-generation firewall)** — stateful plus application awareness, user identity, and integrated IPS/threat intelligence.
- **WAF (web application firewall)** — Layer-7 protection for web apps: SQLi/XSS signatures and rules in front of HTTP traffic. A WAF does not replace a network firewall — different layer, different threats.
- **UTM (unified threat management)** — many functions in one appliance; common in small business.
- **ACL discipline** — rules evaluated in order, first match wins, implicit deny at the end; rule reviews remove stale allows. Content/URL filtering and DNS filtering are the policy cousins.

## IDS, IPS, and Detection Placement

- **IDS** — detects and alerts; passive, out-of-band. **IPS** — sits inline and can block in real time; inline placement means it can also become a failure point.
- **Detection methods** — **signature-based** (known patterns; blind to novel attacks), **anomaly/behavior-based** (deviation from baseline; catches novelty, risks false positives), **heuristic** (rule-of-thumb scoring between the two).
- **False positive vs false negative** — an alert on benign traffic vs a missed real attack; tuning trades one against the other.
- **NIDS/NIPS vs HIDS/HIPS** — network sensors watch segments; host agents watch one machine's calls, files, and logs.
- **Honeypots and honeynets** — decoy systems that attract and study attackers while alerting on any touch (no legitimate user should ever connect).

## Secure Remote Access and Administration

- SSH for device administration, never Telnet; management interfaces on a dedicated management network/VLAN.
- **Out-of-band management** — a separate path (console server, modem) that works when the network itself is the problem.
- Remote desktop (RDP/VNC) belongs behind VPN or a gateway, never exposed raw to the internet — a perennial exam scenario and a real-world breach headline.

## Monitoring the Network

- **NetFlow / flow data** — who talked to whom, how much, when: metadata without payload.
- **Packet capture** — full payload for deep analysis; storage-expensive, privacy-sensitive.
- **SNMPv3 traps and syslog** feed device events into the monitoring stack; **SIEM** correlation lives in the operations doc — network telemetry is its raw material.
- **Network access control (NAC)** — posture-checks devices at connection (patch level, AV present) and can quarantine the unhealthy into a remediation VLAN.
