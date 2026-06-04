# RB-RECOVERY-005 Third-Party Trust Restoration

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Runbook ID | RB-RECOVERY-005 | 2026-06-04 |
| Runbook Name | Third-Party Trust Restoration | 2026-06-04 |
| Owner | Arcana Framework | 2026-06-04 |
| Version | 1.0 | 2026-06-04 |
| Status | Live | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Incident containment completed
- Third-party access restrictions validated
- Exposure assessment completed
- Vendor remediation completed
- Business owner approval obtained
- Risk acceptance completed where required
- Incident ticket remains active

---

# 2. Step-by-Step Instructions

### Step 1 – Verify Third-Party Remediation

Obtain evidence that the third party has:

- Completed investigation activities
- Contained the incident
- Removed attacker access
- Implemented corrective actions
- Completed recovery activities

Review:

- Incident reports
- Security advisories
- Vendor communications
- Attestation documents

Document findings.

---

### Step 2 – Validate Organisational Risk Assessment

Review:

- Exposure assessment
- Impact assessment
- Residual risk
- Business requirements
- Operational dependencies

Determine:

- Whether restoration is appropriate
- Whether additional controls are required

Document decisions.

---

### Step 3 – Review Previously Restricted Access

Identify:

- User accounts
- Service accounts
- API integrations
- OAuth applications
- Federation relationships
- Remote access solutions
- Administrative access

Create a restoration inventory.

---

### Step 4 – Restore Access Incrementally

Restore access using a phased approach:

Phase 1:

- Low-risk integrations
- Read-only access
- Limited functionality

Phase 2:

- Operational integrations
- Standard business access

Phase 3:

- Administrative access
- Privileged functionality

Validate each phase before proceeding.

---

### Step 5 – Rotate Credentials & Secrets

Where applicable:

- Rotate passwords
- Rotate service account credentials
- Rotate API keys
- Rotate certificates
- Reissue authentication secrets

Confirm successful implementation.

---

### Step 6 – Re-Establish Trust Relationships

Restore as approved:

- SAML trust relationships
- OIDC integrations
- OAuth applications
- Federation relationships
- Cross-tenant trust

Verify:

- Authentication functionality
- Authorisation controls
- Least privilege configuration

Document results.

---

### Step 7 – Validate Security Controls

Confirm:

- Logging enabled
- Monitoring operational
- Alerting operational
- Access controls functioning
- Conditional access policies applied

Review:

- Authentication logs
- Audit logs
- Access logs

Document validation.

---

### Step 8 – Monitor Restored Access

Monitor for:

- Unusual authentication activity
- Excessive privilege usage
- Suspicious API activity
- Unauthorised access attempts
- Unexpected configuration changes

Investigate anomalies immediately.

---

### Step 9 – Obtain Business Sign-Off

Confirm with:

- Business owner
- Vendor management
- Security leadership
- Service owner

Document:

- Restoration approval
- Remaining risks
- Monitoring requirements

Record sign-off.

---

### Step 10 – Update Incident Record

Record:

- Restored services
- Restored trust relationships
- Credential rotations completed
- Validation results
- Stakeholder approvals
- Residual risks

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure restored access has been documented
- Ensure trust relationships have been validated
- Ensure monitoring is operational
- Ensure stakeholder approvals are recorded
- Ensure residual risks are documented
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
