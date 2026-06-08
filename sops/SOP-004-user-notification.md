# SOP-004: User Notification During a Security Incident

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | SOP-004: User Notification During a Security Incident | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
  Define the process for providing timely and accurate communication to affected users and stakeholders during a security incident, including what to communicate, who to notify, and how to handle follow-up responses.

- **Scope:**
  Applies to all security incidents where users need to be informed of impact, required actions, or organisational advisories. This includes single-user notifications, department-wide alerts, and organisation-wide advisories.

## 2. Definitions

- **Affected User:** A user whose account, device, or data has been directly impacted by the incident.
- **Advisory:** A broader communication issued to warn users about an active threat (e.g. phishing campaign) even if they are not yet confirmed as impacted.
- **Communication Scope:** The reach of the notification — single user, multiple users, department, or organisation-wide.

## 3. Roles & Responsibilities

- **Incident Commander:**
  Approves communication scope and content before distribution.

- **Communications Lead:**
  Drafts notification content, coordinates distribution, and monitors responses.

- **Management / Leadership:**
  Notified when executives are targeted or when the incident requires organisation-wide communication.

## 4. Procedure

### 4.1 Prerequisites

- Incident summary and current status
- Confirmed list of impacted users
- Containment actions completed (or in progress)
- Required user actions identified
- Approved communication templates
- Access to email platform, internal messaging platform, and incident management platform

### 4.2 Step-by-Step Instructions

1. **Determine Communication Scope**
   - Single user
   - Multiple users
   - Department-wide
   - Organisation-wide

2. **Prepare Notification Content**
   - Include:
     - What happened 
     - What actions were taken by the security team
     - What the user needs to do 
     - What to avoid 
     - How to report further suspicious activity
   - Avoid:
     - Excessive technical detail
     - Unverified assumptions
     - Sensitive investigation details
     - Blame-focused language

3. **Obtain Approval**
   - Have the Incident Commander and Communication Lead review and approve the notification content before sending.

4. **Notify Affected Users**
   - Send communication to:
     - Directly impacted users
     - Managers (if required)
     - Leadership (if required, e.g. executives targeted)

5. **Provide Required User Actions**
   - Clearly list what each user must do, e.g.:
     - Reset password
     - Re-register MFA
     - Reboot device
     - Report suspicious follow-on emails

6. **Publish Broader Advisory (if required)**
   - Recommended if the campaign is widespread

7. **Monitor User Responses**
   - Track:
     - Additional user reports
     - Questions or concerns raised
     - Newly identified impacted users
   - Feed any new reports back to the investigation team to expand scope if needed.

## 5. Compliance & Auditability

- All user notifications must be logged in the incident ticket, including content sent, recipients, and timestamp.
- Broader advisories must be retained as part of the incident record.
- Communication approval by the Incident Commander and Communication Lead must be documented.

## 6. Communication & Escalation

- **Internal Communication:**
  - Use the organisation's primary communication platform (e.g. Slack, Teams) to coordinate notification creation and approval before distribution.

- **Escalation Criteria:**

  | Condition | Action |
  |-----------|--------|
  | Large-scale campaign confirmed | Issue organisation-wide advisory |
  | Executives or VIPs targeted | Notify leadership directly |
  | Additional user reports received after notification | Expand incident scope and update investigation team |

## 7. References & Linked Resources

- **Playbooks:**
  - [PB-001: Phishing & Credential Theft](../playbooks/PB-001-phishing.md)

## 8. Appendices


## 9. Review & Maintenance

- **Review Cycle:**
  This SOP should be reviewed annually, or following any incident where user communication was delayed, inaccurate, or caused confusion.

- **Feedback Process:**
  Feedback is collected during the Post-Incident Review. The Communications Lead is asked to comment on whether notifications were timely, clear, and effective.

---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
