# RB-CONTAIN-008 Third-Party Access Restriction

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |
| Runbook ID | RB-CONTAIN-008 | 2026-06-04 |
| Runbook Name | Third-Party Access Restriction | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Third-party compromise or exposure has been identified
- Incident ticket has been created
- Third-party exposure assessment has been completed
- Impacted vendor has been identified
- Business owner has been identified
- Vendor access inventory is available
- IAM administration access is available
- Change management approvals have been obtained where required

---

# 2. Step-by-Step Instructions

### Step 1 – Identify Third-Party Access Paths

Review and document all active third-party access mechanisms, including:

- User accounts
- Privileged accounts
- Service accounts
- API integrations
- OAuth applications
- Federated identity relationships
- VPN access
- Remote administration platforms
- Cloud cross-account access
- Managed service provider access
- Shared credentials

Create a complete inventory of active access paths.

---

### Step 2 – Assess Business Impact

Determine:

- Business dependency on the third party
- Operational impact of access removal
- Critical systems affected
- Potential service disruption
- Alternative support arrangements

Document impact and obtain approval where required.

---

### Step 3 – Restrict Third-Party User Accounts

Review all third-party user accounts.

Perform one or more of the following:

- Disable accounts
- Suspend accounts
- Remove privileged roles
- Restrict authentication methods
- Restrict access locations
- Restrict access times

Document all actions taken.

---

### Step 4 – Revoke Active Sessions

Identify and revoke:

- Active cloud sessions
- SaaS sessions
- VPN sessions
- Federated identity sessions
- Administrative sessions

Verify successful session termination.

Document findings.

---

### Step 5 – Restrict Service Accounts

Review all service accounts associated with the third party.

Where appropriate:

- Disable service accounts
- Remove permissions
- Rotate credentials
- Restrict scope of access
- Remove privileged roles

Validate that access has been removed successfully.

---

### Step 6 – Disable Integrations

Review and restrict:

- API keys
- OAuth applications
- Service integrations
- SaaS integrations
- Webhooks
- Automation platforms
- Synchronisation services

Where appropriate:

- Disable integrations
- Revoke API keys
- Remove OAuth consent
- Remove delegated access

Document all actions.

---

### Step 7 – Restrict Trust Relationships

Review and restrict:

- SAML trust relationships
- OIDC trust relationships
- Federation configurations
- Cross-tenant trust
- Cross-account cloud access
- Partner connectivity

Validate removal or restriction of access.

Document findings.

---

### Step 8 – Validate Containment

Confirm:

- Accounts are disabled
- Sessions are revoked
- Tokens are invalidated
- Integrations are disabled
- Trust relationships are restricted

Review logs to ensure access is no longer active.

Investigate any continued activity.

---

### Step 9 – Notify Stakeholders

Notify:

- Business owner
- Vendor management team
- Identity team
- Cloud team
- Security leadership
- Incident commander

Communicate:

- Restrictions implemented
- Business impact
- Expected duration
- Recovery requirements

Document notifications.

---

### Step 10 – Update Incident Record

Record:

- Access paths reviewed
- Accounts disabled
- Sessions revoked
- Service accounts restricted
- Integrations disabled
- Trust relationships restricted
- Business impacts
- Stakeholder notifications

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure all third-party access restrictions are documented
- Ensure containment effectiveness has been validated
- Ensure business impacts have been recorded
- Ensure stakeholder notifications are documented
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
