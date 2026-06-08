# SOP-001-Paging an Engineering Team's On-Call for Security Incidents

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | SOP-001: Paging an Engineering Team's On-Call for Security Incidents | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
  Define the process for engaging an engineering team's on-call during a security incident.

- **Scope:**
  Applies to all Security Incidents.

## 2. Definitions

- **Security Incident:** An event that results in, or is reasonably suspected to result in, an impact on the confidentiality, availability, or integrity of information systems and the information they process.

## 3. Roles & Responsibilities

- **Role 1:** Incident Commander
  Responsibilities:
  - Decides when to page engineering on-call based on incident scope and severity
  - Initiates the page to the relevant engineering team's on-call
  - Provides context and a clear ask when engaging the on-call engineer
  - Coordinates communication between the incident response team and the paged engineer

- **Role 2:** Engineering Team On-Call
  Responsibilities:
  - Acknowledges the page within the defined SLA
  - Joins the War Room
  - Provides technical expertise and support for their team's systems or services
  - Executes containment or remediation actions as directed by the Incident Commander
  - Documents technical findings and actions taken during the incident

## 4. Procedure

### 4.1 Prerequisites

- An active security incident with a confirmed severity level
- Access to the on-call paging tool

### 4.2 Step-by-Step Instructions

1. **Identify the engineering team** whose systems or services are impacted or needed for the incident
2. **Raise a page** to the engineering team's on-call via the on-call paging tool, including the:
   - Incident ticket link
   - Severity level
   - Brief description of the issue and what support is needed
3. **Brief the on-call engineer** when they respond - share the War Room link, current findings, and the specific ask
4. **Coordinate actions** - the IC directs priorities while the on-call engineer executes technical tasks
5. **Document the engagement** - the ask, actions taken, and outcome within the incident ticket

## 5. Compliance & Auditability

- All pages are logged and documented within the on-call paging tool and within the incident ticket.
- Compliance with this SOP is reviewed during the Post-Incident Review (PIR).

## 6. Communication & Escalation

- **Internal Communication:**
  If no acknowledgement within SLA, re-page or escalate to the engineering team's manager.

- **Escalation Criteria:**
  No response within the defined SLA, or the on-call engineer is unable to provide the required support.

## 7. References & Linked Resources

- **Playbooks:**
  - [PB-002: Ransomware Incident Response](../playbooks/PB-002-ransomware.md)

## 8. Appendices

- **Contact List:**
  [Key personnel and escalation contacts]

- **Templates & Forms:**
  [Incident log, communication templates, evidence collection forms]

- **Process Flowchart:**
  [Visual diagram of the SOP workflow, if applicable]

## 9. Review & Maintenance

- **Review Cycle:**
  [Specify frequency and triggers for review]

- **Feedback Process:**
  Feedback is incorporated during the PIR review.


---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
