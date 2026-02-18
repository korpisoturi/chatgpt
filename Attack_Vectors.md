# Attack Vector Catalogue (for custom ChatGPT knowledge)

> Purpose: Provide a planning-ready, non-operational catalogue of common foothold vectors across technical, physical, human, and organizational domains. Aligned with the “footholds” workshop concept. :contentReference[oaicite:0]{index=0}

## How to read each vector (recommended fields)
- **What it is:** one-sentence definition  
- **Typical prerequisites:** access, trust, proximity, credentials, vendor link  
- **Foothold outcome:** initial access / persistence / lateral movement / data access  
- **Detectability:** low / medium / high (conceptual)  
- **Common mitigations:** 1–3 defensive phrases  

---

# Cyber / Technical

## Malware delivery
### Email attachment / link-borne payload
- **What it is:** Malicious content delivered through email to trigger execution or install a loader.
- **Typical prerequisites:** reachable inboxes, user interaction, weak filtering or user training gaps.
- **Foothold outcome:** execution on endpoint; potential persistence and credential access.
- **Detectability:** medium (depends on controls and user reporting).
- **Common mitigations:** secure email gateway, attachment sandboxing, user training, least privilege.

### Mobile malware delivery
- **What it is:** Compromising phones/tablets to steal tokens, intercept MFA, or access corporate apps.
- **Typical prerequisites:** mobile app exposure, sideloading/social tricks, weak mobile management.
- **Foothold outcome:** identity/token access; pivot to SaaS and internal systems.
- **Detectability:** medium.
- **Common mitigations:** MDM, app allowlisting, phishing-resistant MFA, device compliance checks.

### Removable media infection (USB/media drops)
- **What it is:** Introducing malware via removable media into restricted or segmented environments.
- **Typical prerequisites:** physical proximity or access; autorun-like user behavior; weak device control.
- **Foothold outcome:** execution inside a more trusted zone; potential lateral movement.
- **Detectability:** medium to high (if endpoint controls are strong).
- **Common mitigations:** device control, endpoint protection, restricted USB policies, awareness.

---

## Phishing & identity attacks
### Credential phishing
- **What it is:** Tricking users into revealing passwords, tokens, or approving sign-ins.
- **Typical prerequisites:** reachable targets; believable pretext; weak user verification habits.
- **Foothold outcome:** account takeover; access to email/SaaS/VPN.
- **Detectability:** low to medium (varies by monitoring).
- **Common mitigations:** phishing-resistant MFA, email security, user training, conditional access.

### MFA manipulation (fatigue/recovery abuse)
- **What it is:** Pushing users into approving sign-ins or abusing account recovery processes.
- **Typical prerequisites:** target reachable; weak recovery verification; approval-style MFA in use.
- **Foothold outcome:** account takeover that bypasses password-only defenses.
- **Detectability:** medium (anomalous auth patterns).
- **Common mitigations:** FIDO2/WebAuthn, tighter recovery, number matching, anomaly detection.

### Session / token theft
- **What it is:** Stealing session cookies or API tokens to bypass password prompts.
- **Typical prerequisites:** endpoint compromise or insecure storage/sharing of tokens.
- **Foothold outcome:** access as a legitimate session; stealthy lateral movement in SaaS.
- **Detectability:** low to medium.
- **Common mitigations:** device-bound tokens, short session lifetimes, continuous access evaluation.

---

## Exposed services & remote access
### Internet-exposed remote access (VPN/RDP/SSH/admin panels)
- **What it is:** Gaining access via exposed management or remote access services.
- **Typical prerequisites:** exposed surface; weak credentials/misconfig; limited monitoring.
- **Foothold outcome:** initial access; potential admin-level control.
- **Detectability:** medium (logs exist; not always reviewed).
- **Common mitigations:** reduce exposure, MFA, allowlisting, patching, monitoring.

### Misconfigured cloud services (public storage/APIs/IAM)
- **What it is:** Access through insecure cloud configuration rather than “classic exploits.”
- **Typical prerequisites:** misconfigurations, excessive permissions, exposed endpoints.
- **Foothold outcome:** data access; privilege escalation in cloud environment.
- **Detectability:** low to medium.
- **Common mitigations:** CSPM, least privilege IAM, secure defaults, logging and alerting.

---

## Vulnerabilities & misconfigurations
### Web application weaknesses
- **What it is:** Web/API flaws that enable unauthorized actions or data access.
- **Typical prerequisites:** reachable web surface; weak secure development practices.
- **Foothold outcome:** app-level access; potential data exposure or pivot to internal systems.
- **Detectability:** medium.
- **Common mitigations:** secure SDLC, WAF, code review, testing, patching.

### Enterprise software weaknesses (servers/appliances/identity platforms)
- **What it is:** Vulnerabilities in infrastructure software enabling unauthorized access.
- **Typical prerequisites:** vulnerable version; reachable service; weak segmentation.
- **Foothold outcome:** system-level foothold; lateral movement.
- **Detectability:** medium.
- **Common mitigations:** patch management, segmentation, asset inventory, monitoring.

### Configuration abuse (insecure defaults/open shares/excessive privilege)
- **What it is:** Using weak configurations to access systems without exploiting software bugs.
- **Typical prerequisites:** misconfigured services; permissive access controls.
- **Foothold outcome:** rapid initial access and privilege gains.
- **Detectability:** low to medium.
- **Common mitigations:** hardening baselines, least privilege, regular configuration audits.

---

## Credential attacks
### Password spraying
- **What it is:** Trying common passwords across many accounts to avoid lockouts.
- **Typical prerequisites:** known usernames; weak password policy; limited detection.
- **Foothold outcome:** account compromise; access to email/VPN/SaaS.
- **Detectability:** medium (if alerting exists).
- **Common mitigations:** strong passwords, lockout/monitoring, MFA, rate limiting.

### Brute force
- **What it is:** Repeated attempts against specific accounts or services.
- **Typical prerequisites:** exposed auth endpoint; weak rate limiting.
- **Foothold outcome:** account compromise.
- **Detectability:** high (if monitored).
- **Common mitigations:** rate limiting, lockouts, MFA, geo/IP controls.

### Default / known credentials
- **What it is:** Using vendor defaults or shared credentials that were never changed.
- **Typical prerequisites:** unmanaged assets; poor onboarding/hardening.
- **Foothold outcome:** fast access, often elevated.
- **Detectability:** low to medium.
- **Common mitigations:** credential rotation, asset discovery, hardening checks.

### Credential stuffing (reuse from other breaches)
- **What it is:** Trying leaked username/password pairs across services.
- **Typical prerequisites:** exposed auth; users reusing passwords.
- **Foothold outcome:** account takeover.
- **Detectability:** medium.
- **Common mitigations:** MFA, breached-password protection, rate limiting, user education.

---

## Supply chain & third-party
### Software supply chain (updates/dependencies/installers)
- **What it is:** Compromising delivered software so it arrives “trusted.”
- **Typical prerequisites:** influence over vendor/dependency ecosystem.
- **Foothold outcome:** widespread, stealthy initial access.
- **Detectability:** low to medium.
- **Common mitigations:** SBOM, code signing verification, vendor risk management, monitoring.

### CI/CD pipeline compromise
- **What it is:** Accessing build/sign/release systems to ship malicious artifacts.
- **Typical prerequisites:** access to developer tools, secrets, or build infrastructure.
- **Foothold outcome:** trusted distribution channel; persistence at scale.
- **Detectability:** low to medium.
- **Common mitigations:** segregated build systems, secret management, MFA, audit logs.

### Service provider / MSP access
- **What it is:** Abusing trusted remote tooling and vendor relationships.
- **Typical prerequisites:** shared access paths; weak vendor controls.
- **Foothold outcome:** privileged entry through legitimate channels.
- **Detectability:** medium (often looks “normal”).
- **Common mitigations:** vendor least privilege, monitored access, segmentation, contract controls.

### Partner / federation abuse
- **What it is:** Pivoting via connected organizations, identity federation, or B2B links.
- **Typical prerequisites:** trust relationships; weak conditional access.
- **Foothold outcome:** access that bypasses perimeter controls.
- **Detectability:** low to medium.
- **Common mitigations:** zero trust, conditional access, federation governance, monitoring.

---

## Management plane compromise
### EDR / MDM / RMM compromise
- **What it is:** Taking control of fleet management tools to deploy actions at scale.
- **Typical prerequisites:** access to admin consoles or API keys; weak segregation.
- **Foothold outcome:** high-impact control over many endpoints.
- **Detectability:** medium.
- **Common mitigations:** admin MFA, role separation, strict logging, break-glass controls.

### Backup / DR system access
- **What it is:** Controlling restore points or disabling recovery to lock in impact.
- **Typical prerequisites:** privileged access; weak isolation of backups.
- **Foothold outcome:** persistence and resilience against incident response.
- **Detectability:** medium.
- **Common mitigations:** immutable backups, separate admin domains, monitoring, restore drills.

---

## Crypto, keys & secrets (chain enablers)
### Key / certificate / token compromise
- **What it is:** Stealing encryption keys, certs, signing keys, or API tokens.
- **Typical prerequisites:** access to key storage, endpoints, or secret management gaps.
- **Foothold outcome:** impersonation, decryption in some contexts, trusted signing.
- **Detectability:** low to medium.
- **Common mitigations:** HSM/secure enclaves, rotation, least privilege, secret scanning.

### Offline cracking of stolen material
- **What it is:** Attempting to recover secrets from captured hashes/archives (where feasible).
- **Typical prerequisites:** stolen hashes/archives; weak password choices.
- **Foothold outcome:** credential recovery enabling further access.
- **Detectability:** low (happens off-network).
- **Common mitigations:** strong passwords, modern hashing, MFA, credential hygiene.

---

# Physical

## Facility access
### Tailgating / impersonation
- **What it is:** Gaining entry to restricted spaces by blending in or being escorted.
- **Typical prerequisites:** on-site presence; weak access control culture.
- **Foothold outcome:** access to endpoints, ports, documents, badges.
- **Detectability:** low to medium.
- **Common mitigations:** badge checks, training, visitor policies, security presence.

### Badge theft / cloning
- **What it is:** Obtaining or duplicating physical access credentials.
- **Typical prerequisites:** proximity; weak badge tech or procedures.
- **Foothold outcome:** repeated access to facilities.
- **Detectability:** medium (if access logs are reviewed).
- **Common mitigations:** modern badge tech, anti-passback, monitoring, rapid revocation.

### Device theft / loss exploitation
- **What it is:** Using lost/stolen laptops or phones as access paths.
- **Typical prerequisites:** opportunity; weak disk encryption or session hygiene.
- **Foothold outcome:** credential/session access; internal access if trusted.
- **Detectability:** medium.
- **Common mitigations:** full-disk encryption, remote wipe, device compliance, short sessions.

---

## Hardware & signals
### TEMPEST / emissions capture
- **What it is:** Extracting information from electromagnetic emanations (specialized).
- **Typical prerequisites:** proximity and specialized capability.
- **Foothold outcome:** information capture rather than classic system access.
- **Detectability:** low.
- **Common mitigations:** shielding, zoning, policy controls.

### Hardware implant / rogue accessory
- **What it is:** Introducing modified peripherals/devices into the environment.
- **Typical prerequisites:** physical access; weak hardware controls.
- **Foothold outcome:** covert access channel or data capture.
- **Detectability:** low to medium.
- **Common mitigations:** port control, device inventory, inspections, procurement controls.

---

## Network proximity
### Ethernet port access
- **What it is:** Plugging into internal networks via exposed wall ports/switches.
- **Typical prerequisites:** physical access to network ports.
- **Foothold outcome:** internal network presence.
- **Detectability:** medium.
- **Common mitigations:** 802.1X/NAC, port security, segmentation, monitoring.

### Rogue device on network (drop box / rogue AP)
- **What it is:** Connecting covert devices to create persistent internal access.
- **Typical prerequisites:** physical access; lack of NAC/port monitoring.
- **Foothold outcome:** persistent internal foothold.
- **Detectability:** low to medium.
- **Common mitigations:** NAC, rogue device detection, network baselining, physical checks.

---

## Wireless
### Wi-Fi proximity attacks (rogue AP / evil twin / weak auth)
- **What it is:** Abusing wireless trust or misconfigurations from nearby.
- **Typical prerequisites:** proximity; weak Wi-Fi security; user trust.
- **Foothold outcome:** credential capture or network access (depending on setup).
- **Detectability:** medium.
- **Common mitigations:** WPA2/3-Enterprise, certificate-based auth, WIDS/WIPS, training.

### Bluetooth / NFC proximity
- **What it is:** Short-range abuse to gain access or data (high level).
- **Typical prerequisites:** proximity; discoverable devices; weak pairing controls.
- **Foothold outcome:** device access or data leakage.
- **Detectability:** low to medium.
- **Common mitigations:** disable when not needed, device policies, monitoring.

---

# Human

## Social engineering
### For credentials (incl. helpdesk resets)
- **What it is:** Pretexting users/support to obtain access or reset accounts.
- **Typical prerequisites:** target reachability; weak verification processes.
- **Foothold outcome:** account takeover; access to internal services.
- **Detectability:** low to medium.
- **Common mitigations:** strong identity verification, least privilege, training, audit trails.

### For data leakage
- **What it is:** Eliciting sensitive information through conversation or “harmless” requests.
- **Typical prerequisites:** access to staff; weak data-handling discipline.
- **Foothold outcome:** intelligence gathering; data exposure enabling later access.
- **Detectability:** low.
- **Common mitigations:** data classification, training, approval workflows, DLP.

### For physical entry
- **What it is:** Convincing staff to grant physical access or escort.
- **Typical prerequisites:** on-site presence; weak visitor control.
- **Foothold outcome:** access to restricted spaces and assets.
- **Detectability:** low to medium.
- **Common mitigations:** visitor policies, badge enforcement, security awareness.

---

## Insiders
### Recruited / ideological insider
- **What it is:** Insider intentionally assisting due to alignment or motivation.
- **Typical prerequisites:** recruitment path; access role.
- **Foothold outcome:** privileged access, long-term persistence.
- **Detectability:** low to medium.
- **Common mitigations:** monitoring, separation of duties, access reviews, culture.

### Coerced / blackmailed insider
- **What it is:** Insider pressured into harmful actions.
- **Typical prerequisites:** leverage over individual; access role.
- **Foothold outcome:** privileged access with high reliability.
- **Detectability:** low.
- **Common mitigations:** support channels, monitoring, least privilege, awareness.

### Bribed insider
- **What it is:** Insider paid to provide access or perform actions.
- **Typical prerequisites:** approach path; financial incentive; access role.
- **Foothold outcome:** privileged access, data theft.
- **Detectability:** low to medium.
- **Common mitigations:** audits, monitoring, access controls, whistleblowing mechanisms.

### Unwitting insider
- **What it is:** Insider manipulated into risky actions without malicious intent.
- **Typical prerequisites:** social pressure or confusion; weak process controls.
- **Foothold outcome:** account compromise or unintended exposure.
- **Detectability:** medium.
- **Common mitigations:** training, clear procedures, approvals, verification.

---

# Organizational / Business

## Supply chain & procurement
### Malicious hardware in procurement
- **What it is:** Compromised devices introduced through procurement channels.
- **Typical prerequisites:** supply influence; weak acceptance testing.
- **Foothold outcome:** stealth access or data capture.
- **Detectability:** low.
- **Common mitigations:** trusted suppliers, acceptance testing, device inventory.

### Malicious software/services (vendors, SaaS, outsourced dev)
- **What it is:** Compromise introduced via a service or software provider.
- **Typical prerequisites:** vendor compromise or weak vendor security.
- **Foothold outcome:** trusted-path access; broad reach.
- **Detectability:** low to medium.
- **Common mitigations:** vendor risk management, contracts, monitoring, segmentation.

### Third-party software risk (inherited vulnerabilities)
- **What it is:** Using weaknesses present in dependencies and packaged software.
- **Typical prerequisites:** dependency use; slow patch cycles.
- **Foothold outcome:** access via a commonly deployed component.
- **Detectability:** medium.
- **Common mitigations:** patching, SBOM, vulnerability management, exposure reduction.

---

## Customer & user channels
### Support portal abuse
- **What it is:** Manipulating ticketing/chat/verification flows to gain access or changes.
- **Typical prerequisites:** reachable support; weak verification.
- **Foothold outcome:** account changes, credential resets, data access.
- **Detectability:** medium.
- **Common mitigations:** strong verification, audit logs, staff training.

### Customer integration pivot (B2B links, shared API keys, multi-tenant)
- **What it is:** Entering through customer/partner integrations and shared trust.
- **Typical prerequisites:** integration exists; weak key handling or isolation.
- **Foothold outcome:** lateral access across connected environments.
- **Detectability:** low to medium.
- **Common mitigations:** tenant isolation, key rotation, scoped permissions, monitoring.

### Fraudulent customer behavior (abuse of legitimate services)
- **What it is:** Using valid service features in unintended ways to reach restricted outcomes.
- **Typical prerequisites:** service access; insufficient abuse controls.
- **Foothold outcome:** data exposure or privilege misuse.
- **Detectability:** medium.
- **Common mitigations:** abuse detection, rate limits, business logic controls.

---

## Legal / administrative pressure (scenario-safe)
### Coerced disclosure / compelled access
- **What it is:** Leveraging legal/administrative processes to obtain data or access.
- **Typical prerequisites:** jurisdictional leverage; process weaknesses.
- **Foothold outcome:** data access without technical compromise.
- **Detectability:** high internally if tracked; low if mishandled.
- **Common mitigations:** legal review, documented processes, transparency logs.

### Contractual leverage / dispute-driven operational pressure
- **What it is:** Using business conflict to force risky changes or access grants.
- **Typical prerequisites:** contractual dependence; weak governance.
- **Foothold outcome:** exceptions that create new access paths.
- **Detectability:** medium.
- **Common mitigations:** governance, change control, risk acceptance processes.

---

# Emerging / Future Vectors

## AI-enabled social engineering
- **What it is:** More convincing and scalable pretexting, impersonation, and targeting.
- **Typical prerequisites:** target info and reachability; weak verification culture.
- **Foothold outcome:** faster credential theft and access grants.
- **Detectability:** low to medium.
- **Common mitigations:** verification procedures, phishing-resistant MFA, training.

## AI-assisted vulnerability discovery
- **What it is:** Faster identification of weak points (conceptual, non-operational).
- **Typical prerequisites:** accessible attack surface; poor hardening.
- **Foothold outcome:** increased likelihood of finding a workable entry path.
- **Detectability:** medium (scanning patterns) to low (targeted recon).
- **Common mitigations:** exposure reduction, patching, monitoring.

## Autonomous systems exposure
- **What it is:** Robots/vehicles/drones as networked endpoints and safety-critical surfaces.
- **Typical prerequisites:** connectivity and maintenance/update paths.
- **Foothold outcome:** operational disruption and safety impact potential.
- **Detectability:** medium.
- **Common mitigations:** segmentation, secure update pipelines, monitoring.

## Quantum risk to cryptography
- **What it is:** Long-term impact to certain public-key schemes; near-term “harvest now, decrypt later” risk framing.
- **Typical prerequisites:** captured encrypted data; long retention value.
- **Foothold outcome:** future decryption risk rather than immediate entry.
- **Detectability:** low.
- **Common mitigations:** crypto agility planning, migration to quantum-resistant options over time.

---

# Notes
- “Decryption” is treated as **key/token compromise and crypto weaknesses** (a chain enabler, not usually an entry vector).
- All items are phrased for **planning and defensive awareness**, not for step-by-step exploitation. :contentReference[oaicite:1]{index=1}
