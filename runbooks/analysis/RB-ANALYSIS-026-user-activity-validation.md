# RB-ANALYSIS-026 User Activity Validation

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |
| Runbook ID | RB-ANALYSIS-026 | 2026-06-04 |
| Runbook Name | User Activity Validation | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Access to EDR telemetry
- Access to SIEM telemetry
- User identity confirmed
- Endpoint hostname identified
- Relevant alerts collected
- Incident ticket created

---

# 2. Step-by-Step Instructions

### Step 1 – Identify User Context

Collect:

- Username
- Department
- Manager
- Privilege level
- Endpoint ownership
- Normal job responsibilities

Determine:

- Whether the user is technical or non-technical
- Whether elevated privileges exist
- Whether administrative activity is expected

---

### Step 2 – Review Alerted Activity

Identify:

- Process execution activity
- Command-line activity
- Script execution
- Network activity
- Authentication activity
- File access activity

Determine:

- What actions triggered the alert
- When activity occurred
- Which systems were involved

---

### Step 3 – Review Historical User Behaviour

Assess:

- Normal login patterns
- Normal working hours
- Normal application usage
- Administrative tooling usage
- Historical alerts

Identify deviations from established behaviour.

---

### Step 4 – Validate Business Purpose

Determine whether activity aligns with:

- Approved change requests
- Software deployment activities
- Administrative operations
- Security testing activities
- Development activities
- Scheduled maintenance

Review available documentation.

---

### Step 5 – Validate with Relevant Stakeholders

Where required:

- Contact user
- Contact manager
- Contact system owner
- Contact IT operations team
- Contact development team

Confirm:

- Whether activity was expected
- Whether activity was authorised
- Whether activity was approved

Document all responses.

---

### Step 6 – Review Related Activity

Assess:

- Authentication activity
- Endpoint activity
- Network activity
- Cloud activity
- File access activity

Determine whether activity was isolated or part of broader behaviour.

---

### Step 7 – Assess Risk

Determine whether activity is:

- Authorised and expected
- Authorised but risky
- Unauthorised but benign
- Suspicious
- Malicious

Document justification.

---

### Step 8 – Identify Additional Indicators

Review for:

- Persistence mechanisms
- Credential access
- Data staging
- Data exfiltration
- Privilege escalation
- Lateral movement

If identified, expand investigation scope.

---

### Step 9 – Escalate if Required

If evidence supports another incident type:

Activate:

- PB-003 Endpoint Malware
- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-006 Insider Threat
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

Continue executing current playbook concurrently.

---

### Step 10 – Update Incident Record

Record:

- User validation findings
- Stakeholder responses
- Behaviour assessment
- Risk assessment
- Escalation decisions

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure all stakeholder responses are documented
- Ensure activity legitimacy determination is recorded
- Ensure escalation decisions are documented
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
