# RB-RECOVERY-004: Exposure Mitigation

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Exposure Mitigation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial creation | |

## 1. Prerequisites

- Completion of Sensitive Data Impact Assessment
- Completion of containment activities
- Identified exposed datasets and systems
- Access to cloud administration platforms
- Access to SaaS administration platforms
- Access to Identity Provider (IdP)
- Access to secrets management platforms
- Access to affected systems and applications
- Approval from Incident Commander and relevant stakeholders (if required)

## 2. Step-by-Step Instructions

1. **Review Exposure Assessment**
   - Review:
     - Impacted datasets
     - Impacted systems
     - Impacted users
     - Exposure paths
     - Regulatory considerations
   - Confirm recovery priorities.

2. **Remove Public Access**
   - Identify and remove:
     - Public sharing links
     - Anonymous access links
     - Public repositories
     - Public cloud storage objects
   - Validate removal of external access.

3. **Remove External Sharing**
   - Review and remove:
     - External collaborators
     - Guest accounts
     - Third-party access
     - Unauthorised sharing permissions
   - Document all access changes.

4. **Rotate Exposed Credentials**
   - Rotate:
     - User credentials
     - Service account credentials
     - Administrative credentials
     - Shared credentials
   - Validate successful credential changes.

5. **Rotate Exposed Secrets**
   - Rotate:
     - API keys
     - Access tokens
     - Certificates
     - Application secrets
     - Cloud access keys
   - Confirm replacement secrets are functioning correctly.

6. **Remove Unauthorised Integrations**
   - Identify and remove:
     - OAuth applications
     - Third-party integrations
     - Service accounts
     - Unapproved automation workflows
   - Validate removal and access revocation.

7. **Review and Restore Access Controls**
   - Review:
     - Permissions
     - Role assignments
     - Sharing policies
     - Security groups
   - Restore access controls to approved configurations.

8. **Validate Exposure Remediation**
   - Confirm:
     - Exposure paths are closed
     - External access has been removed
     - Credentials have been rotated
     - Secrets have been replaced
     - Access controls are functioning as intended
   - Document validation results.

9. **Monitor for Residual Risk**
   - Monitor for:
     - Reuse of exposed credentials
     - Continued access attempts
     - Unauthorised sharing activity
     - Suspicious authentication activity
   - Escalate any new findings.

10. **Escalate and Hand Off**
    - Provide recovery status to the Incident Commander.
    - Coordinate with:
      - Business stakeholders
      - Data owners
      - Legal & Compliance
    - Update the incident record with all actions performed.

## 3. Post-Action

- Ensure all exposure mitigation actions are documented.
- Record all credentials, secrets, and integrations that were remediated.
- Preserve evidence supporting remediation activities.
- Confirm all identified exposure paths have been addressed.
- Attach validation results to the incident record.
- Participate in post-incident review and hardening activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
