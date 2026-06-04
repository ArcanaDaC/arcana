# RB-TRIAGE-005 DDoS Alert Validation

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Runbook ID | RB-TRIAGE-005 | 2026-06-04 |
| Runbook Name | DDoS Alert Validation | 2026-06-04 |
| Owner | Arcana Framework | 2026-06-04 |
| Version | 1.0 | 2026-06-04 |
| Status | Live | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- DDoS alert or service degradation has been reported
- Incident ticket has been created
- Access to network telemetry is available
- Access to monitoring dashboards is available
- Access to cloud provider telemetry is available where applicable
- Access to CDN and WAF telemetry is available where applicable
- Impacted service has been identified

---

# 2. Step-by-Step Instructions

### Step 1 – Identify Alert Source

Determine the source of the alert.

Examples include:

- SIEM alert
- IDS/IPS alert
- DDoS protection platform alert
- CDN alert
- Cloud provider alert
- Network monitoring alert
- Service availability monitoring
- Customer report
- Internal operations team
- External service provider

Document the source.

---

### Step 2 – Validate Service Impact

Determine whether a genuine service impact exists.

Review:

- Service availability
- Application health
- Customer reports
- Error rates
- Response times
- Infrastructure health

Document observed impact.

---

### Step 3 – Identify Affected Assets

Determine:

- Affected applications
- Affected websites
- Affected APIs
- Affected network segments
- Affected cloud resources
- Affected customer services

Create an impacted asset inventory.

---

### Step 4 – Review Traffic Trends

Review:

- Inbound traffic volume
- Connection rates
- Request rates
- Bandwidth utilisation
- Packet rates
- Historical baselines

Identify significant deviations from normal behaviour.

Document findings.

---

### Step 5 – Determine Attack Characteristics

Identify indicators including:

- Traffic spikes
- Large numbers of unique source IPs
- Excessive requests
- Protocol abuse
- Amplification behaviour
- Reflection activity
- Geographic concentration

Determine whether observed activity is consistent with DDoS behaviour.

---

### Step 6 – Rule Out Alternative Causes

Review for:

- Infrastructure failures
- Service outages
- Cloud platform issues
- Application defects
- Deployment failures
- Configuration changes
- Network routing issues

Determine whether the outage is operational rather than malicious.

Document findings.

---

### Step 7 – Assess Initial Severity

Determine:

- Number of affected users
- Number of affected services
- Duration of impact
- Business impact
- Customer impact
- Operational impact

Assign an initial severity level.

Document rationale.

---

### Step 8 – Identify Existing Mitigations

Determine whether the following are already active:

- CDN protection
- DDoS protection service
- WAF protections
- Rate limiting
- Traffic filtering
- Auto-scaling controls
- Cloud-native protections

Document existing defensive controls.

---

### Step 9 – Determine Escalation Requirements

If DDoS activity is confirmed:

Activate:

- PB-013 Distributed Denial of Service (DDoS)

Escalate to:

- Network Operations
- Infrastructure Teams
- Cloud Teams
- Incident Commander

If suspicious concurrent activity is observed:

Consider activating:

- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

Document escalation decisions.

---

### Step 10 – Update Incident Record

Record:

- Alert source
- Impacted assets
- Traffic observations
- Service impact
- Severity assessment
- Existing mitigations
- Escalation decisions

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure DDoS validation has been completed
- Ensure impacted assets have been identified
- Ensure alternative causes have been assessed
- Ensure severity has been assigned
- Ensure escalation decisions are documented
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
