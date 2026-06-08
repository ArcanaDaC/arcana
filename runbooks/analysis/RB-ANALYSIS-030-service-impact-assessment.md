# RB-ANALYSIS-030 Service Impact Assessment

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Document Name | Service Impact Assessment | |
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
- Impacted service has been identified
- Service ownership information is available
- Service health telemetry is available
- Monitoring dashboards are available
- Business stakeholders have been identified

---

# 2. Step-by-Step Instructions

### Step 1 – Identify Impacted Services

Determine:

- Impacted applications
- Impacted websites
- Impacted APIs
- Impacted network services
- Impacted cloud services
- Impacted customer-facing services
- Impacted internal services

Create a service inventory.

Document findings.

---

### Step 2 – Assess Service Availability

Review:

- Service uptime
- Service availability metrics
- Error rates
- Request success rates
- Application health
- Infrastructure health

Determine:

- Fully unavailable services
- Degraded services
- Intermittent services

Document findings.

---

### Step 3 – Assess Customer Impact

Determine:

- Number of affected customers
- Geographic impact
- Product impact
- Transaction impact
- Customer support volume
- Customer complaints

Estimate customer impact severity.

Document findings.

---

### Step 4 – Assess Business Impact

Determine:

- Revenue impact
- Operational disruption
- Regulatory impact
- Contractual obligations
- Service level agreement (SLA) impact
- Reputational impact

Document business consequences.

---

### Step 5 – Assess Infrastructure Impact

Review:

- Network utilisation
- Load balancer health
- CDN performance
- WAF performance
- Server utilisation
- Cloud resource utilisation
- Database performance

Identify bottlenecks and failures.

Document findings.

---

### Step 6 – Identify Critical Dependencies

Review:

- Authentication services
- DNS services
- CDN services
- Cloud infrastructure
- Third-party providers
- Payment platforms
- Backend services

Determine whether dependencies contribute to the outage.

Document findings.

---

### Step 7 – Prioritise Recovery Targets

Identify:

- Critical services
- High-priority services
- Customer-facing services
- Revenue-generating services
- Regulatory-sensitive services

Assign restoration priorities.

Document decisions.

---

### Step 8 – Assess Recovery Complexity

Determine:

- Existing mitigations
- Required resources
- Required vendors
- Required infrastructure changes
- Estimated recovery timelines

Document recovery considerations.

---

### Step 9 – Identify Escalation Requirements

Escalate where appropriate:

- Infrastructure teams
- Network teams
- Cloud teams
- Executive leadership
- Business continuity teams

If additional malicious activity is identified:

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

- Impacted services
- Customer impact
- Business impact
- Infrastructure impact
- Recovery priorities
- Escalation decisions

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure impacted services have been identified
- Ensure customer impact has been assessed
- Ensure business impact has been documented
- Ensure recovery priorities have been established
- Ensure escalation decisions are recorded
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
