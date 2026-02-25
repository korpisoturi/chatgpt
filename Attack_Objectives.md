```markdown
# Attack Objectives Catalogue (for custom ChatGPT knowledge)

> Purpose: Provide a clear, planning-ready catalogue of **attacker objectives** to support scenario design and “foothold” decision-making. Objectives describe **why** an attacker acts and **what outcomes** they seek, without specifying operational steps. 

---

## Core (Strategic) Objectives

### 1) Espionage
- **Intent:** Secretly obtain information, insight, or long-term access without being detected.
- **Typical outcomes:**
  - Confidential information exfiltration (documents, emails, designs, customer data)
  - Competitive/strategic intelligence (roadmaps, bids, negotiations)
  - Surveillance and monitoring (who talks to whom, when, and about what)
  - Long-term persistence for repeat collection
- **Common characteristics:**
  - Prefers stealth, patience, low disruption
  - Often combines technical + human + third-party access
  - May accept partial access if it enables continuous collection

### 2) Sabotage
- **Intent:** Degrade, disrupt, or destroy capability, trust, or safety—often to impose cost or change behavior.
- **Typical outcomes:**
  - Service disruption or outage
  - Data destruction or corruption
  - Operational impairment (production, logistics, safety systems)
  - Reputation damage and loss of trust
- **Common characteristics:**
  - Speed and impact may matter more than stealth
  - Often timed to maximize harm (events, deadlines, peak business periods)
  - Can be paired with coercion/extortion or political signaling

---

## Information Security Target Objectives (CIA Mapping)

> These objectives map to **Confidentiality, Integrity, Availability (CIA)**.  
> They can support either espionage or sabotage depending on intent.

### A) Data leak (Confidentiality)
- **Goal:** Unauthorized disclosure of information to an attacker or the public.
- **What attackers may seek to leak:**
  - Credentials and secrets (passwords, tokens, keys, certificates)
  - Sensitive business data (contracts, bids, strategies, financials)
  - Personal data (PII), customer lists, communications
  - Intellectual property (designs, code, research)
- **Why it matters:**
  - Enables deeper access (credential leak)
  - Enables long-term intelligence advantage (strategic leak)
  - Enables coercion, reputational harm, regulatory exposure (public leak)

**Typical impact indicators (conceptual):**
- Unapproved disclosure, unexpected sharing links, unusual data transfers, unauthorized repository access.

---

### B) Data encryption or manipulation (Integrity)
> Note: Encryption can be used for sabotage (locking you out) or as part of extortion/coercion. Manipulation targets trust in systems and decisions.

#### B1) Data encryption (loss of control over data)
- **Goal:** Prevent legitimate access to data by encrypting it or making it unavailable without a key.
- **Typical outcomes:**
  - Business interruption
  - Recovery cost, downtime, incident response burden
  - Potential secondary effects: forced process changes, safety risks in operational environments

#### B2) Data manipulation (tampering/corruption)
- **Goal:** Alter data or systems so outcomes cannot be trusted.
- **Typical outcomes:**
  - Silent corruption of records (finance, logs, audits)
  - Manipulated configurations (security controls weakened, backdoors maintained)
  - Modified operational parameters (manufacturing, logistics, scheduling)
- **Why it’s dangerous:**
  - Integrity attacks can stay hidden longer than outages
  - Decision-making becomes unreliable (business and safety consequences)

**Typical impact indicators (conceptual):**
- Unexpected configuration drift, unexplained record changes, mismatched checksums, audit/log inconsistencies, anomalies in business outputs.

---

### C) Denial of service (Availability)
- **Goal:** Prevent legitimate users from accessing services, systems, or data.
- **Common forms (high level):**
  - Network/service overload
  - Exhaustion of application resources
  - Disruption of dependencies (DNS, identity providers, upstream services)
- **Typical outcomes:**
  - Downtime, lost revenue, operational disruption
  - Customer harm and reputational damage
  - Diversion as cover for other objectives (e.g., espionage during chaos)

**Typical impact indicators (conceptual):**
- Elevated latency, error spikes, capacity exhaustion, upstream dependency failures, widespread user access issues.

---

## How objectives combine (common patterns)

### Espionage-driven combinations
- **Confidentiality** is primary: data leak, credential theft, long-term access for repeat collection.
- **Integrity/Availability** may be secondary: avoid disruption to remain hidden.

### Sabotage-driven combinations
- **Availability** and **Integrity** are primary: DoS, encryption (lockout), manipulation/corruption.
- **Confidentiality** may be used as leverage: threaten to leak to amplify impact.

---

## Practical mapping for workshop scenario design

When defining an attack objective, specify:
- **Strategic objective:** Espionage or Sabotage (or both)
- **CIA target:** Confidentiality / Integrity / Availability
- **Primary target assets:** e.g., identity systems, customer data, OT operations, backups, executive comms
- **Success condition:** what “done” looks like (outcome-based, not step-based)

---

## Notes
- This catalogue describes **intent and outcomes**, not operational methods.  
- Use it to align vectors/resources/footholds with measurable scenario goals. 
```
