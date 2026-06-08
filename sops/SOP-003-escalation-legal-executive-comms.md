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
| Change Summary | Expanded to include regulatory and legal coordination process | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
  Define the process for executive escalation, legal engagement, crisis communications, regulatory coordination, and external notification decisions during a security incident.

- **Scope:**
  Applies to incidents requiring executive notification, Legal/Compliance engagement, customer or partner communications, regulatory assessment, cyber insurance notification, or external statements. This SOP is incident-type-agnostic and may be invoked by any playbook.

## 2. Definitions

- **Crisis Communication Cadence:** Defined schedule for stakeholder updates, including audience, frequency, owner, and approval flow.
- **Regulatory Notification:** A legally required disclosure to a regulator or government body following a reportable security event or data breach.
- **External Communication:** Any message sent outside the organisation, including customers, partners, vendors, regulators, insurers, media, or law enforcement.
- **Stakeholder:** Any group with a decision-making, operational, legal, customer, or business interest in the incident.

## 3. Roles & Responsibilities

- **Incident Commander:**
  Triggers this SOP, approves communications, owns executive escalation, and ensures decisions are documented.

- **Communications Lead:**
  Drafts internal and external messaging, manages communication cadence, and coordinates approvals.

- **Legal / Compliance:**
  Assesses legal obligations, regulatory thresholds, contractual obligations, cyber insurance requirements, and notification deadlines.

- **Executive Leadership:**
  Receives briefings, approves high-impact external communications and recovery decisions, and provides strategic direction.

- **Business / Data Owners:**
  Confirm operational impact, affected datasets, customer or partner impact, and business context needed for notifications.

## 4. Procedure

### 4.1 Prerequisites

- Incident summary, timeline, scope, containment status, and recovery status
- Business impact and sensitive data impact assessment, where applicable
- Impacted datasets, systems, customers, partners, vendors, or jurisdictions identified
- Legal, Compliance, Communications, and executive stakeholders identified
- Crisis communication channel and incident ticket established

### 4.2 Step-by-Step Instructions

1. **Notify Executive Leadership**
   - Provide an initial briefing covering:
     - What happened, what is known, and what is unknown
     - Business impact and affected systems/users/data
     - Containment and recovery status
     - Key risks, deadlines, and decisions needed

2. **Engage Legal & Compliance**
   - Provide Legal/Compliance with:
     - Incident timeline
     - Investigation findings
     - Impact and data assessment
     - Containment and recovery status
     - Known customer, partner, vendor, or regulatory impact
   - Document legal guidance and decision owners.

3. **Assess Notification Obligations**
   - Determine applicable obligations based on:
     - Jurisdiction and industry
     - Data classification and likelihood of harm
     - Contractual commitments
     - Customer, partner, vendor, or cyber insurance requirements
   - Track notification deadlines, thresholds, and required approvers.

4. **Identify Impacted External Parties**
   - Identify whether the incident affects:
     - Customers
     - Partners
     - Vendors
     - Regulators or government agencies
     - Insurers
     - Law enforcement
   - Maintain a list of parties, notification owners, status, and deadlines.

5. **Establish Communication Cadence**
   - Define:
     - Update frequency
     - Stakeholder groups
     - Message owner
     - Approval flow
     - Escalation path for delayed approvals

6. **Prepare and Approve Communications**
   - Coordinate with Legal and Communications Lead on:
     - Executive updates
     - Customer or partner notices
     - Regulatory submissions
     - Media statements or holding statements
     - Third-party/vendor notifications
   - Do not issue external communications without Incident Commander and Legal approval.

7. **Track Regulatory and Legal Actions**
   - Record:
     - Notifications submitted
     - Submission dates
     - Case/reference numbers
     - Regulator or insurer responses
     - Follow-up requests
     - Legal guidance and risk decisions
   - Attach supporting documentation to the incident record.

8. **Document Executive and Legal Decisions**
   - Record all decisions with owner and timestamp, including:
     - Notification decisions
     - Recovery approvals
     - External communication approvals
     - Risk acceptance decisions
     - Legal or compliance determinations

## 5. Compliance & Auditability

- All executive briefings, legal guidance, external communications, notification decisions, and approvals must be logged in the incident ticket.
- Regulatory deadlines, submissions, case numbers, and follow-up requests must be tracked to completion.
- External communications must have documented Incident Commander and Legal approval before release.
- Legal and compliance communications must be retained according to organisational policy.
- This SOP's execution is reviewed during the Post-Incident Review.

## 6. Communication & Escalation

- **Internal Communication:**
  - The Communications Lead maintains a single source of truth for messaging.
  - Executive, Legal, Compliance, Communications, and business stakeholders receive updates according to the agreed cadence.

- **Escalation Criteria:**

  | Condition | Action |
  |-----------|--------|
  | Sensitive data exposure suspected or confirmed | Initiate legal and regulatory notification assessment |
  | Regulatory notification threshold may be met | Legal/Compliance owns notification deadline tracking |
  | Customer, partner, or vendor impact identified | Prepare external communication plan with Legal approval |
  | Critical outage or major business impact ongoing | Escalate to executive leadership and crisis management |
  | Approval delay risks missing a deadline | Escalate to Incident Commander, Legal leadership, and executive sponsor |
  | Unapproved external communication issued | Notify Incident Commander and Legal immediately |

## 7. References & Linked Resources

- **Playbooks:**
  - [PB-002: Ransomware Incident Response](../playbooks/PB-002-ransomware.md)
  - [PB-005: Data Exfiltration](../playbooks/PB-005-data-exfiltration.md)
  - [PB-012: Third-Party Compromise](../playbooks/PB-012-third-party-compromise.md)

- **SOPs:**
  - [SOP-005: Vendor Communication During a Security Incident](SOP-005-vendor-communication.md)

## 8. Appendices

### Appendix A: Legal / Regulatory Tracking Checklist

- Incident summary and timeline
- Impacted data, systems, customers, partners, vendors, and jurisdictions
- Applicable legal, regulatory, contractual, and insurance obligations
- Notification thresholds and deadlines
- Required approvers
- Notifications sent and timestamps
- Case numbers or regulator references
- Follow-up requests and owners
- Final legal guidance and risk decisions

## 9. Review & Maintenance

- **Review Cycle:**
  This SOP should be reviewed annually, or after any incident where executive escalation, legal engagement, regulatory coordination, or external communications were delayed, inconsistent, incomplete, or non-compliant.

- **Feedback Process:**
  Feedback is collected during the PIR from the Incident Commander, Communications Lead, Legal/Compliance, and relevant business owners.

---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
