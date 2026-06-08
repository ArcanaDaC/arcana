# SOP-005: Vendor Communication During a Security Incident

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | SOP-005: Vendor Communication During a Security Incident | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
  Define the process for contacting vendors during a security incident through approved channels such as Technical Account Managers (TAMs), support tickets, emergency support lines, security contacts, and email.

- **Scope:**
  Applies when incident responders need information, support, escalation, remediation evidence, outage status, log access, forensic artifacts, or containment assistance from a vendor, supplier, SaaS provider, cloud provider, MSP, software provider, or partner.

## 2. Definitions

- **Vendor:** Any third party that provides software, infrastructure, SaaS, support, managed services, integrations, or business-critical services.
- **TAM / Account Team:** Vendor-provided technical or account contact responsible for support coordination and escalation.
- **Support Ticket:** A tracked request submitted through the vendor's support portal or helpdesk.
- **Vendor Security Contact:** A security-specific contact such as a security operations mailbox, vulnerability disclosure contact, trust portal contact, or incident response contact.
- **Emergency Vendor Escalation:** A high-priority vendor engagement path used for active incidents, production impact, suspected compromise, or urgent containment support.

## 3. Roles & Responsibilities

- **Incident Commander:**
  Approves vendor engagement, sets priority, and decides when to escalate vendor response delays.

- **Communications Lead:**
  Coordinates external wording when vendor communication may create legal, customer, or reputational impact.

- **Vendor Owner / Business Owner:**
  Provides vendor contact details, relationship context, contract/SLA information, and account team contacts.

- **Technical Lead / Incident Responder:**
  Defines the technical ask, evidence required, urgency, affected systems, and required response timeline.

- **Legal / Compliance:**
  Reviews communication where contractual obligations, breach notification, customer impact, or regulated data may be involved.

## 4. Procedure

### 4.1 Prerequisites

- Active incident ticket or investigation record
- Vendor name, affected product/service, and business owner
- Incident summary approved for vendor sharing
- Clear technical ask and urgency level
- Available vendor contacts, support portal access, TAM/account team contacts, or security contact
- Legal review completed if sensitive data, contractual notification, or external disclosure risk exists

### 4.2 Step-by-Step Instructions

1. **Confirm the Need to Contact the Vendor**
   - Determine why vendor engagement is required:
     - Confirm compromise or service impact
     - Request logs, artifacts, or audit data
     - Request containment or remediation support
     - Escalate outage or security support
     - Validate advisory, patch, mitigation, or exposure
   - Confirm the ask with the Incident Commander.

2. **Identify the Correct Vendor Channel**
   - Use the fastest appropriate approved channel:
     - TAM or account team for urgent coordination and escalation
     - Support ticket for tracked technical support
     - Emergency support phone line for production or active security impact
     - Vendor security contact for compromise, vulnerability, or abuse reporting
     - Email only when no higher-priority channel exists or for follow-up documentation

3. **Prepare the Vendor Brief**
   - Include only information required for the vendor to act:
     - Incident ticket/reference ID
     - Affected product, service, tenant, account, subscription, or environment
     - Impact summary and urgency
     - Timeline and relevant timestamps with timezone
     - Specific request and required response time
     - Relevant IOCs, error IDs, logs, or screenshots
   - Do not share sensitive internal details, credentials, customer data, or regulated data unless approved by Legal.

4. **Open the Vendor Engagement**
   - Create a support ticket or contact the TAM/account team.
   - Use emergency phone support if active compromise, production impact, or urgent containment support is required.
   - Copy or notify the vendor owner and Incident Commander.
   - Record the ticket number, contact method, timestamp, vendor contact, and requested action in the incident ticket.

5. **Escalate if Vendor Response Is Insufficient**
   - Escalate when:
     - No acknowledgement within required response time
     - Vendor response does not address the security impact
     - Containment, log access, or remediation is blocked
     - Business-critical service impact continues
   - Escalation options:
     - Call TAM or account team
     - Raise ticket priority
     - Use emergency support line
     - Engage vendor management/procurement
     - Escalate through executive or contractual contacts

6. **Track Vendor Responses and Evidence**
   - Record all vendor responses in the incident ticket.
   - Save vendor advisories, timelines, remediation statements, support responses, call notes, and ticket updates.
   - Track open vendor actions, owners, due times, and blockers.

7. **Close Vendor Engagement**
   - Confirm the vendor has answered the original ask or provided a documented next step.
   - Confirm all requested evidence, mitigations, or remediation statements are captured.
   - Document closure status, remaining risks, and follow-up actions in the incident ticket.

## 5. Compliance & Auditability

- All vendor communications must be logged in the incident ticket, including timestamps, contacts, channel used, ticket numbers, and decisions.
- Security-sensitive or legally sensitive vendor communications must be reviewed by the Incident Commander and Legal/Compliance before sending.
- Vendor-provided evidence and remediation statements must be retained with the incident record.
- Any missed SLA, delayed response, or communication issue should be reviewed during the Post-Incident Review.

## 6. Communication & Escalation

- **Internal Communication:**
  - Keep the Incident Commander, vendor owner, and Technical Lead informed of vendor status and blockers.
  - Summarise vendor updates in the incident ticket or War Room.

- **Escalation Criteria:**

  | Condition | Action |
  |-----------|--------|
  | Active compromise or production impact requires vendor support | Use emergency support path and notify TAM/account team |
  | Vendor does not respond within required timeframe | Raise ticket priority and escalate to TAM/account team |
  | Vendor response is incomplete or blocks containment | Escalate through vendor owner, procurement, or executive contacts |
  | Sensitive data, customer impact, or contractual notification is involved | Engage Legal/Compliance before external communication |
  | Vendor communication may become public or customer-facing | Coordinate with Communications Lead and Legal |

## 7. References & Linked Resources

- **Playbooks:**
  - [PB-012: Third-Party Compromise](../playbooks/PB-012-third-party-compromise.md)

- **Other SOPs:**
  - [SOP-003: Escalation, Legal & Executive Communications](SOP-003-escalation-legal-executive-comms.md)

## 8. Appendices

### Appendix A: Vendor Contact Checklist

- Vendor name
- Product/service name
- Business owner
- TAM/account team contact
- Emergency support phone number
- Support portal URL
- Vendor security contact
- Contract/SLA reference
- Customer/account/subscription/tenant ID
- Internal escalation owner

### Appendix B: Vendor Support Request Template

```text
Subject: Security Incident Support Request - [Vendor/Product] - [Severity/Urgency]

Hello [Vendor Contact],

We are investigating a security incident involving [product/service/environment].

Summary:
- Impact: [brief impact summary]
- Affected environment/account/tenant: [identifier]
- Time window: [start/end with timezone]
- Urgency: [reason for urgency]

Request:
- [specific action or information requested]
- Required response time: [timeframe]

Relevant details:
- [IOCs, logs, error IDs, ticket references, screenshots, timestamps]

Please confirm receipt and provide the next update by [time/timezone].

Regards,
[Name / Team]
```

## 9. Review & Maintenance

- **Review Cycle:**
  This SOP should be reviewed annually or after any incident where vendor engagement was delayed, unclear, incomplete, or ineffective.

- **Feedback Process:**
  Feedback is collected during the PIR from the Incident Commander, Technical Lead, vendor owner, and Legal/Compliance when applicable.

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
