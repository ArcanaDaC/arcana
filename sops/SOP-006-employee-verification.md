# SOP-006: Employee Verification During a Security Incident

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | SOP-006: Employee Verification During a Security Incident | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
    Define how responders verify an employee's identity before taking high-impact security actions such as account recovery, device replacement, access restoration, or sensitive incident discussions.

- **Scope:**
    Applies when a user's identity must be confirmed during an incident. Verification may use live video over approved internal communication tools such as Zoom, Slack, Teams, or equivalent, even when an account may be compromised, because visual confirmation and contextual checks are used together.

## 2. Definitions

- **Employee Verification:** Confirming that the person requesting or approving an action is the legitimate employee.
- **Live Video Verification:** Real-time visual confirmation using an approved video platform.
- **Contextual Verification:** Confirming identity using known internal context such as manager, team, office location, asset assignment, ticket history, or HR/identity records.
- **High-Impact Action:** Any action that could restore, remove, or change access, device ownership, credentials, MFA, or sensitive incident information.

## 3. Roles & Responsibilities

- **Incident Commander:** Approves verification requirements for sensitive or high-risk actions.
- **Incident Responder / Service Desk Analyst:** Performs verification and records the outcome.
- **Identity & Access Team:** Supports verification before credential, MFA, or access restoration.
- **Manager / Business Owner:** Confirms employee identity or business need when required.
- **HR / People Team:** Supports identity confirmation when normal verification is inconclusive.

## 4. Procedure

### 4.1 Prerequisites

- Active incident ticket or service request
- Employee name, user ID, manager, team, and contact details from authoritative records
- Approved communication channel available for live verification
- Clear action requiring verification

### 4.2 Step-by-Step Instructions

1. **Confirm Verification Is Required**
    - Verify identity before:
        - Restoring account access
        - Resetting MFA
        - Provisioning a replacement device
        - Releasing sensitive incident details
        - Accepting user-provided recovery instructions

2. **Start a Live Verification Session**
    - Use an approved internal video platform where possible.
    - Confirm the employee appears on live video.
    - Do not rely only on a message from the potentially compromised account.

3. **Validate Identity Using Internal Context**
    - Compare the employee against authoritative records:
        - Name and user ID
        - Manager and team
        - Office or work location
        - Assigned device or asset
        - Recent ticket or incident context
    - Ask context-based questions that are not sensitive secrets.

4. **Confirm the Requested Action**
    - Ask the employee to confirm:
        - What happened
        - What device or account is involved
        - What action they are requesting
        - Whether they still possess any affected device

5. **Escalate Inconclusive Verification**
    - If identity cannot be confirmed, pause the requested action.
    - Escalate to the manager, HR/People Team, Identity & Access Team, or Incident Commander.
    - Do not restore access or release sensitive information until verification is resolved.

6. **Document Verification Outcome**
    - Record:
        - Verification method
        - Date and time
        - Verifier
        - Employee verified
        - Action approved or denied
        - Any escalation or exception

## 5. Compliance & Auditability

- Verification outcomes must be documented in the incident ticket or service request.
- Do not record video sessions unless organisational policy permits it.
- Do not ask for passwords, MFA codes, recovery codes, government IDs, or unnecessary personal data.
- Exceptions must be approved by the Incident Commander or Identity & Access owner.

## 6. Communication & Escalation

- **Internal Communication:**
    - Coordinate verification status with the Incident Commander, Identity & Access Team, Service Desk, and manager where required.

- **Escalation Criteria:**

    | Condition | Action |
    |-----------|--------|
    | Employee cannot join live verification | Use manager, HR, or approved alternate verification path |
    | Account compromise suspected | Do not rely solely on messages from the affected account |
    | Verification is inconclusive | Pause action and escalate to Incident Commander or Identity & Access owner |
    | High-risk access restoration requested | Require Incident Commander or Identity & Access approval |

## 7. References & Linked Resources

- **Playbooks:**
    - [PB-014: Lost & Stolen Device](../playbooks/PB-014-lost-stolen-device.md)

- **SOPs:**
    - [SOP-004: User Notification During a Security Incident](SOP-004-user-notification.md)

## 8. Appendices

### Appendix A: Approved Verification Signals

- Live video confirmation
- Manager confirmation
- HR/People record confirmation
- Asset assignment confirmation
- Recent ticket or incident context
- Corporate directory details
- Known team or role context

### Appendix B: Do Not Use as Sole Verification

- Passwords
- MFA push approval alone
- MFA code disclosure
- Email from the affected account alone
- Chat message from the affected account alone
- Personal documents unless required by approved HR process

## 9. Review & Maintenance

- **Review Cycle:**
    This SOP should be reviewed annually or after any incident where user verification delayed recovery, failed, or caused confusion.

- **Feedback Process:**
    Feedback is collected during the PIR from Incident Response, Service Desk, Identity & Access, and affected business teams.

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
