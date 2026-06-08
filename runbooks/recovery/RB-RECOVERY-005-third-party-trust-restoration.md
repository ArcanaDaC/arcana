# RB-RECOVERY-005 Third-Party Trust Restoration

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |
| Runbook ID | RB-RECOVERY-005 | 2026-06-04 |
| Runbook Name | Third-Party Trust Restoration | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Incident containment activities have been completed
- Third-party access restrictions have been validated
- Exposure assessment has been completed
- Supply chain impact analysis has been completed
- Vendor remediation activities have been completed
- Risk assessment has been completed
- Business owner approval has been obtained
- Incident ticket remains active

---

# 2. Step-by-Step Instructions

### Step 1 – Verify Third-Party Remediation

Obtain evidence that the third party has:

- Completed investigation activities
- Contained the incident
- Removed attacker access
- Eliminated persistence mechanisms
- Implemented corrective actions
- Completed recovery activities

Review:

- Vendor incident reports
- Security advisories
- Remediation statements
- Attestation documents
- Executive communications

Document findings.

---

### Step 2 – Validate Residual Risk

Review:

- Exposure assessment
- Impact assessment
- Vendor remediation activities
- Business requirements
- Compensating controls

Determine:

- Residual risk level
- Additional safeguards required
- Monitoring requirements

Document risk acceptance decisions where applicable.

---

### Step 3 – Review Previously Restricted Access

Identify all access that was disabled or restricted during containment:

- User accounts
- Service accounts
- Administrative accounts
- API integrations
- OAuth applications
- SaaS integrations
- SAML trust relationships
- OIDC trust relationships
- Cloud cross-account access
- Vendor remote access solutions

Create a restoration inventory.

---

### Step 4 – Rotate Credentials and Secrets

Where applicable:

- Rotate passwords
- Rotate service account credentials
- Rotate API keys
- Rotate OAuth secrets
- Rotate certificates
- Rotate access tokens
- Reissue authentication secrets

Validate successful rotation.

Document actions performed.

---

### Step 5 – Restore Access in Phases

Restore access using a phased approach.

Phase 1:

- Low-risk integrations
- Read-only access
- Non-privileged access

Phase 2:

- Operational services
- Standard business access
- Application integrations

Phase 3:

- Administrative access
- Privileged functionality
- High-impact integrations

Validate each phase before proceeding.

---

### Step 6 – Re-Establish Trust Relationships

Restore approved trust relationships including:

- SAML federation
- OIDC federation
- OAuth applications
- API integrations
- SaaS integrations
- Cloud trust relationships
- Vendor remote access connectivity

Verify:

- Authentication functionality
- Authorisation controls
- Least privilege configuration
- Logging coverage

Document validation results.

---

### Step 7 – Validate Security Controls

Confirm:

- Audit logging is enabled
- Monitoring is operational
- Alerting is operational
- Detection rules are functioning
- Access controls are functioning
- Conditional access policies are enforced

Review:

- Authentication logs
- Audit logs
- Administrative activity logs

Document findings.

---

### Step 8 – Monitor Restored Access

Monitor for:

- Unusual authentication activity
- Excessive privilege usage
- Unexpected API activity
- Unauthorised access attempts
- Suspicious administrative actions
- Unexpected configuration changes

Investigate anomalies immediately.

Document monitoring outcomes.

---

### Step 9 – Obtain Stakeholder Approval

Obtain approval from:

- Business owner
- Vendor management team
- Security leadership
- Service owner
- Identity team where applicable

Document:

- Approval decisions
- Remaining risks
- Monitoring requirements
- Outstanding actions

Record sign-off.

---

### Step 10 – Update Incident Record

Record:

- Restored services
- Restored integrations
- Restored trust relationships
- Credential rotations completed
- Validation results
- Monitoring requirements
- Stakeholder approvals
- Residual risks

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure all restored access has been documented
- Ensure trust relationships have been validated
- Ensure monitoring is operational
- Ensure stakeholder approvals are recorded
- Ensure residual risks are documented
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
