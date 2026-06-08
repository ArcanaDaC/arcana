# SOP-003: Escalation, Legal & Executive Communications

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | SOP-003: Escalation, Legal & Executive Communications | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
  Define the process for coordinating executive escalation, legal engagement, crisis communications, and regulatory response during a security incident.

- **Scope:**
  Applies to all security incidents where executive notification, legal engagement, or external communications are required. This SOP is incident-type-agnostic and may be invoked by any playbook.

## 2. Definitions

- **Crisis Communication Cadence:** A defined schedule for stakeholder updates during an active incident, including frequency, audience, and approval process.
- **Regulatory Notification:** A legally required disclosure to a regulatory body (e.g. ICO, CISA, SEC) following a confirmed data breach or reportable security event.
- **Stakeholder:** Any individual or group with a vested interest in the incident - includes executive leadership, legal, compliance, business continuity, customers, regulators, and partners.

## 3. Roles & Responsibilities

- **Incident Commander:**
  Determines when this SOP is triggered, approves all communications, and owns executive escalation.

- **Communications Lead:**
  Drafts internal and external communications, manages the crisis communication cadence, and coordinates messaging approval.

- **Legal / Compliance:**
  Assesses regulatory notification obligations, data breach requirements, contractual obligations, and cyber insurance requirements.

- **Executive Leadership:**
  Receives briefings, approves external communications and recovery decisions, and provides strategic direction.

## 4. Procedure

### 4.1 Prerequisites

- Incident scope and business impact assessment
- Legal and regulatory obligations identified
- Recovery status and estimates
- Executive stakeholder list and contact details
- Crisis communication channel established
- Executive briefing and communication templates

### 4.2 Step-by-Step Instructions

1. **Notify Executive Leadership**
   - Provide an initial executive briefing covering:
     - Incident summary (what happened, what is known, what is unknown)
     - Business impact (systems affected, users impacted, data at risk)
     - Current containment status
     - Recovery estimates
     - Key risks and outstanding decisions

2. **Engage Legal & Compliance**
   - Assess:
     - Regulatory notification obligations (e.g. GDPR, NDB, SEC)
     - Data breach disclosure requirements
     - Contractual notification obligations (customers, partners, vendors)
     - Cyber insurance notification and claim requirements
   - Document legal guidance and any deadlines for required notifications.

3. **Establish Crisis Communication Cadence**
   - Define:
     - Update frequency (e.g. every 2 hours, twice daily)
     - Stakeholder groups and distribution lists
     - Communication approval process (who approves before sending)
     - Escalation pathways if approvals are delayed

4. **Coordinate Internal Communications**
   - Notify:
     - Leadership teams
     - IT operations
     - Security teams
     - Business continuity teams
   - Use the organisation's standard communication platform (e.g. Slack, Teams) to coordinate messaging.

5. **Prepare External Communication Strategy**
   - Coordinate with Legal and Communications Lead on:
     - Customer communications
     - Media responses (hold statements, press releases)
     - Regulatory engagement and filings
     - Third-party and partner notifications
   - No external communication is issued without Incident Commander and Legal approval.

6. **Document Executive Decisions**
   - Track all decisions in the incident ticket, including:
     - Recovery approvals
     - External communications approvals
     - Legal guidance received
     - Risk acceptance decisions
   - Record who made each decision and when.

## 5. Compliance & Auditability

- All executive briefings, legal guidance, and communications must be logged in the incident ticket with timestamps.
- External communications must be approved in writing (or recorded in the incident ticket) before distribution.
- Regulatory notification deadlines must be tracked and documented to demonstrate compliance.
- This SOP's execution is reviewed during the Post-Incident Review.

## 6. Communication & Escalation

- **Internal Communication:**
  - The Communications Lead maintains a single source of truth for all messaging - all drafts and approvals flow through the incident ticket or designated crisis channel.
  - Executive updates follow the cadence established in Step 3.

- **Escalation Criteria:**

  | Condition | Action |
  |-----------|--------|
  | Data exfiltration confirmed | Initiate breach notification review with Legal |
  | Regulatory impact identified | Legal escalation and notification timeline established |
  | Critical outage ongoing | Escalate to crisis management and business continuity |
  | Unapproved external communication issued | Immediately notify Incident Commander and Legal |

## 7. References & Linked Resources

- **Playbooks:**
  - [PB-002: Ransomware Incident Response](../playbooks/PB-002-ransomware.md)

## 8. Appendices


## 9. Review & Maintenance

- **Review Cycle:**
  This SOP should be reviewed annually, or following any incident where executive escalation, legal engagement, or external communications were delayed, inconsistent, or non-compliant.

- **Feedback Process:**
  Feedback is collected during the Post-Incident Review. The Communications Lead and Legal are asked to comment on whether the escalation and communication process was timely and effective.

---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
