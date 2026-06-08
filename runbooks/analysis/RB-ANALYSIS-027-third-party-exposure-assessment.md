# RB-ANALYSIS-027 Third-Party Exposure Assessment

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |
| Runbook ID | RB-ANALYSIS-027 | 2026-06-04 |
| Runbook Name | Third-Party Exposure Assessment | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Third-party compromise notification received
- Vendor or supplier identified
- Incident ticket created
- Access to vendor inventory
- Access to identity and access management systems
- Access to cloud and SaaS audit logs
- Access to asset inventory

---

# 2. Step-by-Step Instructions

### Step 1 – Validate Third-Party Relationship

Identify:

- Vendor name
- Service provided
- Business owner
- Criticality rating
- Contractual relationship
- Data handling responsibilities

Determine:

- Whether the organisation actively uses the vendor
- Whether services remain operational
- Whether the relationship is current

Document findings.

---

### Step 2 – Identify Organisational Dependencies

Review:

- SaaS platforms
- Cloud services
- Managed service providers
- Software suppliers
- Development dependencies
- Security tooling
- Infrastructure providers

Determine:

- Which systems rely on the third party
- Which business processes are affected

Document impacted services.

---

### Step 3 – Assess Third-Party Access

Review:

- User accounts
- Service accounts
- API integrations
- OAuth applications
- Federated identity relationships
- Privileged access
- Administrative access

Identify:

- Active access paths
- High-risk access
- Excessive permissions

Document findings.

---

### Step 4 – Assess Data Exposure

Determine whether the third party has access to:

- Customer data
- Employee data
- Financial data
- Intellectual property
- Source code
- Security telemetry
- Authentication systems

Document:

- Data types
- Data classification levels
- Exposure risk

---

### Step 5 – Review Authentication Activity

Review:

- Recent authentications
- Failed authentication attempts
- Administrative logins
- API activity
- Federated access activity
- Unusual login patterns

Identify suspicious activity associated with the third party.

---

### Step 6 – Review Audit Logs

Review:

- Cloud audit logs
- SaaS audit logs
- Administrative activity logs
- Configuration changes
- Permission changes
- Service account activity

Identify evidence of:

- Unauthorised access
- Suspicious changes
- Unexpected activity

---

### Step 7 – Assess Organisational Impact

Determine:

- Systems impacted
- Users impacted
- Business functions impacted
- Regulatory implications
- Operational risk
- Recovery complexity

Assign an impact rating.

---

### Step 8 – Determine Containment Requirements

Assess whether:

- Third-party access should be suspended
- Service accounts should be disabled
- Tokens should be revoked
- API keys should be rotated
- Integrations should be disabled

Document recommendations.

---

### Step 9 – Identify Escalation Requirements

If evidence supports another incident type:

Activate:

- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

Continue executing current playbook concurrently.

---

### Step 10 – Update Incident Record

Record:

- Third-party details
- Exposure assessment
- Access review findings
- Impact assessment
- Containment recommendations
- Escalation decisions

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure exposure assessment has been documented
- Ensure impacted systems have been identified
- Ensure access relationships have been reviewed
- Ensure containment recommendations are recorded
- Ensure escalation decisions are documented
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
