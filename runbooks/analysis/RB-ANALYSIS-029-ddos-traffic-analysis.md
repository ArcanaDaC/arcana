# RB-ANALYSIS-029 DDoS Traffic Analysis

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Document Name | DDoS Traffic Analysis | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- DDoS activity has been validated
- Incident ticket has been created
- Network telemetry is available
- Firewall logs are available
- CDN telemetry is available where applicable
- WAF logs are available where applicable
- Cloud provider telemetry is available where applicable
- NetFlow or equivalent telemetry is available where applicable

---

# 2. Step-by-Step Instructions

### Step 1 – Establish Attack Timeline

Determine:

- Attack start time
- Detection time
- Peak activity period
- Current attack status
- Attack duration

Build a timeline of observed activity.

Document findings.

---

### Step 2 – Identify Targeted Assets

Determine:

- Targeted IP addresses
- Targeted domains
- Targeted applications
- Targeted APIs
- Targeted services
- Targeted network infrastructure

Identify primary and secondary targets.

Document findings.

---

### Step 3 – Analyse Traffic Volume

Review:

- Total bandwidth utilisation
- Packets per second (PPS)
- Requests per second (RPS)
- Concurrent connections
- Peak traffic volume
- Historical baselines

Determine the scale of the attack.

Document findings.

---

### Step 4 – Identify Attack Type

Determine whether the activity represents:

- Volumetric DDoS
- Protocol DDoS
- Application-layer DDoS
- HTTP flood
- HTTPS flood
- DNS flood
- SYN flood
- UDP flood
- Amplification attack
- Reflection attack
- Multi-vector attack

Document attack classification.

---

### Step 5 – Analyse Source Distribution

Review:

- Source IP addresses
- Autonomous System Numbers (ASNs)
- Geographic distribution
- Hosting providers
- Cloud providers
- Botnet indicators

Determine:

- Concentrated attack sources
- Distributed attack sources
- Spoofing indicators

Document findings.

---

### Step 6 – Identify Amplification or Reflection Activity

Review for:

- DNS amplification
- NTP amplification
- SSDP amplification
- CLDAP amplification
- Memcached amplification
- Reflection behaviour

Identify:

- Amplifiers involved
- Reflection infrastructure
- Potential abuse vectors

Document findings.

---

### Step 7 – Analyse Traffic Characteristics

Review:

- Request methods
- User agents
- Headers
- Protocols
- URI patterns
- Connection behaviour
- Session behaviour

Identify:

- Repetitive requests
- Automated behaviour
- Bot activity
- Attack signatures

Document findings.

---

### Step 8 – Assess Mitigation Effectiveness

Review:

- CDN performance
- WAF effectiveness
- Rate limiting effectiveness
- Filtering effectiveness
- Upstream mitigation effectiveness

Determine:

- Current mitigation status
- Remaining attack impact
- Additional controls required

Document findings.

---

### Step 9 – Assess Secondary Indicators

Review for:

- Concurrent authentication anomalies
- Privilege escalation attempts
- Cloud activity anomalies
- Data access anomalies
- Suspicious administrative activity

Determine whether DDoS activity may be supporting another attack objective.

Escalate where appropriate.

---

### Step 10 – Update Incident Record

Record:

- Attack timeline
- Targeted assets
- Traffic volumes
- Attack classification
- Source analysis
- Mitigation effectiveness
- Secondary observations

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure attack classification is documented
- Ensure targeted assets are identified
- Ensure source analysis is completed
- Ensure mitigation effectiveness is assessed
- Ensure secondary attack indicators are reviewed
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
