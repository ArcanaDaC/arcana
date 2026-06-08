# RB-ANALYSIS-031 DDoS Attribution & Threat Assessment

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Document Name | DDoS Attribution & Threat Assessment | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- DDoS activity has been confirmed
- Incident ticket has been created
- DDoS traffic analysis has been completed
- Service impact assessment has been completed
- Network telemetry is available
- Threat intelligence sources are available
- Relevant logs and evidence have been preserved

---

# 2. Step-by-Step Instructions

### Step 1 – Review Attack Characteristics

Review:

- Attack type
- Attack duration
- Attack volume
- Targeted assets
- Traffic patterns
- Protocols involved
- Mitigation effectiveness

Identify characteristics that may assist attribution.

Document findings.

---

### Step 2 – Analyse Source Infrastructure

Review:

- Source IP addresses
- Autonomous System Numbers (ASNs)
- Hosting providers
- Cloud providers
- Geographic distribution
- Botnet indicators

Determine:

- Concentrated infrastructure
- Distributed infrastructure
- Recurring infrastructure

Document findings.

---

### Step 3 – Review Historical Activity

Determine whether:

- Similar attacks have occurred previously
- Similar infrastructure has been observed previously
- Similar targeting has been observed previously
- Similar attack patterns have been identified previously

Review:

- Historical incidents
- Threat intelligence reports
- Industry reporting

Document findings.

---

### Step 4 – Assess Threat Intelligence

Review:

- Internal threat intelligence
- Commercial intelligence feeds
- Industry sharing communities
- Government advisories
- Open-source intelligence

Identify:

- Known threat actors
- Known botnets
- Known campaigns
- Relevant indicators

Document findings.

---

### Step 5 – Assess Potential Motivation

Evaluate whether the attack is consistent with:

- Financial extortion
- Competitive disruption
- Hacktivism
- Opportunistic activity
- Criminal activity
- Geopolitical activity
- Distraction operations

Document assessment.

---

### Step 6 – Review Extortion Indicators

Review for:

- Extortion emails
- Threat communications
- Ransom demands
- Anonymous messages
- Customer-facing threats
- Social media threats

Determine whether financial demands are associated with the attack.

Document findings.

---

### Step 7 – Assess Secondary Attack Objectives

Review for evidence of:

- Account compromise
- Privilege escalation
- Lateral movement
- Cloud compromise
- Data access
- Data exfiltration
- Suspicious administrative activity

Determine whether the DDoS attack may be intended to:

- Distract defenders
- Conceal malicious activity
- Support a larger attack campaign

Document findings.

---

### Step 8 – Assess Targeting Significance

Determine whether targeting appears focused on:

- Specific applications
- Specific business units
- Specific customer groups
- Specific geographies
- Critical infrastructure
- Executive services
- Revenue-generating systems

Identify possible attacker objectives.

Document findings.

---

### Step 9 – Determine Escalation Requirements

If evidence supports additional attacker activity:

Activate:

- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

Escalate findings to:

- Incident Commander
- Security leadership
- Threat Intelligence team
- Executive leadership where appropriate

Document escalation decisions.

---

### Step 10 – Update Incident Record

Record:

- Attribution assessment
- Threat intelligence findings
- Potential motivations
- Extortion indicators
- Secondary attack indicators
- Escalation decisions
- Confidence assessment

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure attribution findings are documented
- Ensure threat intelligence findings are recorded
- Ensure extortion indicators have been assessed
- Ensure secondary attack objectives have been evaluated
- Ensure escalation decisions are documented
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
