```markdown
# Target System Components Catalogue (for custom ChatGPT knowledge)

> Purpose: Provide a planning-ready breakdown of **target system components** so participants can map footholds, attack vectors, attacker resources, and objectives to concrete parts of the system. This is a component inventory view, not a technical design. 

---

## 1) Network

### Network segments / zones
- **What it is:** Logical separation of environments (e.g., internet edge, corporate IT, production/OT, guest, management, backups).
- **Why it matters:** Determines blast radius, visibility, and lateral movement difficulty.

### Network services
- **Examples:** DNS, DHCP, NTP, routing, VPN, proxies, Wi-Fi controllers.
- **Why it matters:** Often foundational; failure or compromise cascades broadly.

### Connectivity and trust links
- **Examples:** Site-to-site VPNs, partner connections, cloud peering, remote access, federated identity connections.
- **Why it matters:** Bridges between organizations and zones are high-value pathways.

### Monitoring and control plane
- **Examples:** firewalls, IDS/IPS, NAC/802.1X, SIEM logging pipelines.
- **Why it matters:** Changes here affect detection, containment, and attribution.

---

## 2) Computers (Endpoints)

### User workstations
- **Examples:** desktops, laptops, VDI thin clients.
- **Why it matters:** Common starting point for phishing, credential theft, and internal access.

### Mobile endpoints
- **Examples:** smartphones, tablets.
- **Why it matters:** Often hold tokens/MFA apps and access to corporate SaaS.

### Specialized endpoints
- **Examples:** engineering workstations, operator consoles, kiosk systems.
- **Why it matters:** High-privilege use cases; often less frequently patched or tightly controlled.

---

## 3) Servers and Core Platforms

### Identity and access management
- **Examples:** Active Directory, Entra ID/SSO, MFA systems, directory sync.
- **Why it matters:** Identity is the “keys to the kingdom.”

### Application servers
- **Examples:** line-of-business apps, web apps, API gateways, middleware.
- **Why it matters:** Directly expose business processes and data.

### Data platforms
- **Examples:** databases, file servers, document management, email systems.
- **Why it matters:** Primary confidentiality targets; integrity attacks can be subtle.

### Infrastructure services
- **Examples:** virtualization (hypervisors, management), containers, orchestration, configuration management.
- **Why it matters:** Management planes can control entire fleets.

### Backup and recovery systems
- **Examples:** backup servers, backup storage, DR orchestration.
- **Why it matters:** Determines recovery capability during sabotage/extortion.

### Cloud services (if applicable)
- **Examples:** IaaS, PaaS, SaaS, storage buckets, IAM roles, cloud networking.
- **Why it matters:** Misconfigurations and identity links frequently create large exposure.

---

## 4) Devices (Non-traditional IT)

### Network devices
- **Examples:** routers, switches, firewalls, wireless APs.
- **Why it matters:** Shape traffic, segmentation, and visibility.

### IoT and smart building systems
- **Examples:** cameras, access control, HVAC controllers, printers, meeting room systems.
- **Why it matters:** Often weaker security; can provide persistence or physical advantage.

### Operational / industrial devices (if applicable)
- **Examples:** PLCs, SCADA components, sensors/actuators, maintenance ports.
- **Why it matters:** High availability/safety impact; different constraints than IT.

### Removable media and peripherals
- **Examples:** USB drives, external disks, programmable peripherals.
- **Why it matters:** Bridges air gaps and bypasses some network controls.

---

## 5) People

### Users
- **Who:** employees, contractors, interns, temporary staff.
- **Why it matters:** Common targets for social engineering; hold business context and access.

### Administrators / privileged roles
- **Who:** IT admins, cloud admins, security admins, DBAs, OT engineers, helpdesk.
- **Why it matters:** Privileged access can change security posture and enable broad impact.

### Executives and high-value roles
- **Who:** leadership, finance, legal, procurement, HR, R&D leaders.
- **Why it matters:** Authority and sensitive information; targeted for espionage and fraud-style sabotage.

### Security and operations teams
- **Who:** SOC, incident response, network ops, platform engineering.
- **Why it matters:** Their tools and accounts are high-value for stealth and control.

---

## 6) Facilities (Physical Environment)

### Office spaces and work areas
- **Examples:** open office, secured rooms, executive areas, meeting rooms.
- **Why it matters:** Physical access enables device placement and direct endpoint access.

### Data centers / server rooms
- **Examples:** racks, console access, cabling, power systems.
- **Why it matters:** Physical compromise can bypass many digital controls.

### Reception and visitor processes
- **Examples:** visitor badges, escorts, deliveries, contractor access.
- **Why it matters:** Common entry point for impersonation and social engineering.

### Warehouses / production sites (if applicable)
- **Examples:** logistics hubs, plants, shipping/receiving.
- **Why it matters:** High availability and supply chain sensitivity.

---

## 7) Suppliers & Logistics (Third Parties)

### Suppliers (hardware/software/services)
- **Examples:** device vendors, software vendors, SaaS providers, managed service providers (MSP), consultants.
- **Why it matters:** Third-party compromise or trust abuse can bypass perimeter defenses.

### Logistics and delivery channels
- **Examples:** shipping providers, storage facilities, device provisioning and imaging, returns/repair processes.
- **Why it matters:** Opportunities for tampering, credential leakage, or device substitution.

### Outsourced operations
- **Examples:** payroll, customer support, IT helpdesk, manufacturing partners.
- **Why it matters:** Creates additional identities, integrations, and process-based access paths.

### Integrations and trust relationships
- **Examples:** B2B VPNs, federated identity, API keys, shared ticketing, shared monitoring tools.
- **Why it matters:** Bridges can become pivot points.

---

## 8) Cross-cutting Assets (apply across components)

### Credentials, tokens, and secrets
- **Examples:** passwords, API keys, certificates, signing keys.
- **Why it matters:** Enable impersonation and stealth access.

### Data classifications
- **Examples:** public, internal, confidential, regulated, safety-critical.
- **Why it matters:** Defines impact of confidentiality/integrity/availability objectives.

### Policies and processes
- **Examples:** change control, onboarding/offboarding, incident response, procurement.
- **Why it matters:** Process weaknesses can be exploited without “technical hacking.”

---

## Notes
- This catalogue is meant for **mapping**: components ↔ attack vectors ↔ attacker resources ↔ objectives.
- Keep descriptions **outcome-focused** so it stays safe and usable for workshop planning. 
```
