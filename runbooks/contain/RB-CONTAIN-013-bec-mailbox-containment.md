# RB-CONTAIN-013: BEC Mailbox Containment

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | BEC Mailbox Containment | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial creation | |

## 1. Prerequisites

- Confirmed mailbox compromise
- Completion of BEC investigation activities
- Access to email administration platform
- Access to Identity Provider
- Access to affected mailbox

## 2. Step-by-Step Instructions

1. **Confirm Affected Mailbox**
   - Verify affected account details.

2. **Disable Attacker Access**
   - Revoke:
     - Sessions
     - Tokens
     - Active authentication

3. **Reset Credentials**
   - Force password reset.
   - Require MFA re-registration where appropriate.

4. **Remove Malicious Inbox Rules**
   - Remove:
     - Forwarding rules
     - Auto-delete rules
     - Hidden rules

5. **Remove Mail Forwarding**
   - Disable:
     - External forwarding
     - Suspicious forwarding destinations

6. **Remove Unauthorised Access**
   - Remove:
     - Delegates
     - Shared access
     - OAuth grants

7. **Review Mailbox Configuration**
   - Validate:
     - Security settings
     - Mail flow settings
     - Access controls

8. **Monitor for Continued Activity**
   - Review:
     - Authentication attempts
     - Mailbox changes
     - New rules

9. **Validate Containment**
   - Confirm:
     - Attacker access removed
     - Mailbox secured
     - No malicious configuration remains

10. **Escalate and Hand Off**
    - Coordinate with recovery activities.
    - Update the incident record.

## 3. Post-Action

- Document all containment actions.
- Preserve evidence of malicious configuration.
- Record validation results.
- Participate in recovery activities.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
