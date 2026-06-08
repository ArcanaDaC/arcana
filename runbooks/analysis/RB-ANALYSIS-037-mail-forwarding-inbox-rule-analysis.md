# RB-ANALYSIS-037: Mail Forwarding & Inbox Rule Analysis

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Mail Forwarding & Inbox Rule Analysis | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Suspected or confirmed mailbox compromise
- Access to email administration platform
- Access to audit logs
- Access to affected mailbox

## 2. Step-by-Step Instructions

1. **Identify Mailbox in Scope**
   - Confirm affected mailbox.

2. **Review Inbox Rules**
   - Identify:
     - Auto-delete rules
     - Move rules
     - Forwarding rules
     - Hidden rules

3. **Review Mail Forwarding Configuration**
   - Review:
     - Internal forwarding
     - External forwarding
     - Forwarding destinations

4. **Review Delegated Access**
   - Identify:
     - Delegates
     - Shared mailbox access
     - Administrative assignments

5. **Review Mail Flow Configuration**
   - Review:
     - Transport rules
     - Routing changes
     - Forwarding policies

6. **Review Rule Creation Activity**
   - Determine:
     - Creation time
     - Creator account
     - Modification history

7. **Identify Suspicious Destinations**
   - Assess:
     - External addresses
     - Unknown domains
     - Attacker-controlled infrastructure

8. **Assess Data Exposure**
   - Determine:
     - Data potentially forwarded
     - Duration of forwarding
     - Impacted communications

9. **Document Findings**
   - Record all identified rules and forwarding activity.

10. **Escalate and Hand Off**
    - Escalate findings for containment and recovery.
    - Update the incident record.

## 3. Post-Action

- Preserve mailbox configuration artifacts.
- Document findings and exposure assessment.
- Attach evidence to the incident record.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
