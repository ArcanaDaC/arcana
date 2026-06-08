# RB-ANALYSIS-036: Mailbox Compromise Investigation

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Mailbox Compromise Investigation | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Confirmed or suspected mailbox compromise
- Access to email platform audit logs
- Access to SIEM
- Access to IdP logs
- Access to mailbox administration tools

## 2. Step-by-Step Instructions

1. **Identify Affected Mailbox**
   - Confirm mailbox ownership and account details.

2. **Establish Timeline**
   - Determine:
     - Initial compromise
     - First suspicious activity
     - Most recent suspicious activity

3. **Review Authentication Activity**
   - Review:
     - Login events
     - MFA events
     - Geographic anomalies
     - Device information

4. **Review Mailbox Access Activity**
   - Identify:
     - Mailbox logins
     - Delegate access
     - Administrative access

5. **Review Email Activity**
   - Review:
     - Sent messages
     - Deleted messages
     - Drafts
     - Message searches

6. **Review Configuration Changes**
   - Review:
     - Inbox rules
     - Mail forwarding
     - Delegates
     - OAuth grants

7. **Identify Attacker Objectives**
   - Determine:
     - Fraud attempts
     - Data collection
     - Lateral movement
     - Persistence

8. **Assess Scope**
   - Determine affected:
     - Mailboxes
     - Users
     - Business units

9. **Document Findings**
   - Prepare investigation summary.

10. **Escalate and Hand Off**
    - Provide findings to containment teams.
    - Update the incident record.

## 3. Post-Action

- Preserve mailbox artifacts.
- Document timeline and findings.
- Attach evidence to the incident record.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
