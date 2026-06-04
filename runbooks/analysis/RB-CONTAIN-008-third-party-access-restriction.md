# RB-CONTAIN-008 Third-Party Access Restriction

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Runbook ID | RB-CONTAIN-008 | 2026-06-04 |
| Runbook Name | Third-Party Access Restriction | 2026-06-04 |
| Owner | Arcana Framework | 2026-06-04 |
| Version | 1.0 | 2026-06-04 |
| Status | Live | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Third-party exposure assessment completed
- Incident ticket created
- Impacted vendor identified
- Business owner identified
- Vendor access inventory available
- IAM access available
- Change management process followed where required

---

# 2. Step-by-Step Instructions

### Step 1 – Identify Third-Party Access Paths

Review:

- Vendor user accounts
- Service accounts
- API integrations
- OAuth applications
- Federated identity relationships
- Remote access solutions
- Managed service provider access
- Shared administrative accounts

Document all active access paths.

---

### Step 2 – Assess Access Criticality

Determine:

- Business dependency
- Operational impact
- Availability requirements
- Privilege level
- Data access level

Classify access as:

- Critical
- High
- Medium
- Low

Document findings.

---

### Step 3 – Restrict High-Risk User Accounts

Review:

- Vendor administrative accounts
- Shared accounts
- Privileged accounts
- Support accounts

Perform where appropriate:

- Disable accounts
- Suspend accounts
- Restrict permissions
- Restrict login locations
- Restrict authentication methods

Document all actions taken.

---

### Step 4 – Revoke Active Sessions

Review:

- Cloud sessions
- SaaS sessions
- VPN sessions
- Remote access sessions
- Federated sessions

Perform:

- Session revocation
- Forced logout
- Token invalidation

Confirm session termination.

---

### Step 5 – Restrict Service Accounts

Review:

- Integration accounts
- Automation accounts
- Synchronisation accounts
- Monitoring accounts

Perform where appropriate:

- Disable accounts
- Remove permissions
- Rotate credentials
- Restrict scope

Document actions.

---

### Step 6 – Restrict API & Integration Access

Review:

- API keys
- OAuth applications
- Webhooks
- Service integrations
- SaaS integrations

Perform:

- Disable integrations
- Revoke API keys
- Remove OAuth consent
- Restrict permissions

Confirm successful revocation.

---

### Step 7 – Restrict Federated Trust Relationships

Review:

- SAML trust relationships
- OIDC integrations
- Cross-tenant trust
- Identity federation

Determine whether temporary restriction or removal is required.

Implement approved changes.

---

### Step 8 – Validate Containment Effectiveness

Confirm:

- Accounts disabled
- Sessions revoked
- Tokens revoked
- Integrations disabled
- Vendor access removed

Review logs for continued activity.

Investigate any access that persists.

---

### Step 9 – Coordinate Stakeholder Communication

Notify:

- Business owner
- Vendor management team
- Security leadership
- Identity team
- Cloud team

Provide:

- Scope of restrictions
- Operational impact
- Expected duration
- Recovery requirements

Document communications.

---

### Step 10 – Update Incident Record

Record:

- Access paths reviewed
- Accounts disabled
- Sessions revoked
- Integrations disabled
- Trust relationships restricted
- Operational impacts

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure all third-party access restrictions are documented
- Ensure containment actions have been validated
- Ensure affected stakeholders have been notified
- Ensure operational impacts have been recorded
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
