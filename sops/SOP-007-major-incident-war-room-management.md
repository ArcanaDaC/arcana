# SOP-007: Major Incident War Room Management

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | SOP-007: Major Incident War Room Management | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
    Define how to run the command channel, meeting cadence, action tracker, decision log, and status updates for a major security incident.

- **Scope:**
    Applies to Sev 0 or major security incidents requiring cross-functional coordination, executive visibility, multiple technical workstreams, or extended response across teams and geographies.

## 2. Definitions

- **War Room:** Dedicated communication channel and meeting bridge used for real-time incident coordination.
- **Action Tracker:** Authoritative list of open actions, owners, priorities, due times, and status.
- **Decision Log:** Record of material decisions, approvers, rationale, timestamps, and follow-up actions.
- **Operating Cadence:** Agreed schedule for technical syncs, leadership updates, handoffs, and stakeholder briefings.

## 3. Roles & Responsibilities

- **Incident Commander:** Owns war room structure, cadence, priority setting, decision logging, and command transitions.
- **Deputy Incident Commander:** Maintains action tracker, follows up on blockers, and supports continuity during long-running incidents.
- **Technical Lead:** Coordinates technical workstreams and reports investigation, containment, and recovery status.
- **Communications Lead:** Coordinates approved stakeholder updates and ensures messaging aligns with Legal/Compliance.
- **Scribe:** Captures timeline, decisions, actions, owners, status updates, and evidence locations.

## 4. Procedure

### 4.1 Prerequisites

- Major incident declared or likely to be declared
- Incident Commander assigned
- Incident ticket created
- War room channel and meeting bridge available
- Initial severity, scope, and active workstreams identified

### 4.2 Step-by-Step Instructions

1. **Open the War Room**
    - Create or activate the incident channel and meeting bridge.
    - Pin links to the incident ticket, action tracker, decision log, evidence repository, and active playbooks.
    - State the current Incident Commander, Technical Lead, Communications Lead, and Scribe.

2. **Establish Operating Cadence**
    - Define cadence for:
        - Technical syncs
        - Executive updates
        - Legal/communications reviews
        - Geo handoffs
        - Recovery checkpoints
    - Publish the cadence in the war room.

3. **Create the Action Tracker**
    - Track each action with:
        - Owner
        - Priority
        - Due time
        - Status
        - Blockers
        - Link to evidence or ticket
    - Review open actions at each technical sync.

4. **Maintain the Decision Log**
    - Record material decisions including:
        - Decision made
        - Approver
        - Rationale
        - Timestamp
        - Risks accepted
        - Follow-up actions

5. **Coordinate Workstreams**
    - Track workstreams such as investigation, containment, recovery, communications, legal, vendor, and customer support.
    - Ensure each workstream has an owner and next update time.
    - Escalate blockers to the Incident Commander.

6. **Publish Status Updates**
    - Use concise updates covering:
        - Current status
        - Impact
        - Actions completed
        - Open risks
        - Next milestones
        - Decisions needed
    - Do not include unapproved external messaging or sensitive details outside approved channels.

7. **Execute Command Handoffs**
    - Use the geo handoff SOP when command changes across shifts or regions.
    - Confirm the incoming Incident Commander accepts command in the war room and incident ticket.

8. **Close or Downgrade the War Room**
    - Confirm containment, recovery status, communications status, and open follow-up items.
    - Downgrade or close the war room only with Incident Commander approval.
    - Preserve the action tracker, decision log, and timeline in the incident record.

## 5. Compliance & Auditability

- War room actions, decisions, command changes, and status updates must be retained in the incident record.
- Decision logs must include approver, rationale, timestamp, and follow-up owner.
- External communications must follow approved legal and communications processes.
- This SOP's execution is reviewed during the Post-Incident Review.

## 6. Communication & Escalation

- **Internal Communication:**
    - War room is the primary coordination channel for the major incident.
    - Executive and stakeholder updates follow the cadence approved by the Incident Commander and Communications Lead.

- **Escalation Criteria:**

    | Condition | Action |
    |-----------|--------|
    | Workstream blocked | Escalate to Incident Commander and workstream owner |
    | Decision required from leadership | Add to decision log and escalate to executive sponsor |
    | Legal or external communication required | Engage SOP-003 process |
    | Vendor support required | Engage SOP-005 process |
    | Shift or geo transition required | Engage SOP-002 process |

## 7. References & Linked Resources

- **Playbooks:**
    - [PB-019: Major Security Incident Management](../playbooks/PB-019-major-security-incident-management.md)

- **SOPs:**
    - [SOP-002: Incident Handoff Between Geos](SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](SOP-003-escalation-legal-executive-comms.md)
    - [SOP-005: Vendor Communication During a Security Incident](SOP-005-vendor-communication.md)

## 8. Appendices

### Appendix A: Status Update Template

```text
Status: [Investigating / Containing / Recovering / Monitoring]
Severity: [Sev]
Impact: [business/customer/service/data impact]
Current hypothesis: [brief]
Completed actions: [top 3]
Open actions: [top 3 with owners]
Risks/blockers: [brief]
Decisions needed: [owner + deadline]
Next update: [time/timezone]
```

### Appendix B: Decision Log Fields

- Timestamp
- Decision
- Approver
- Rationale
- Risk accepted
- Follow-up owner
- Review time

## 9. Review & Maintenance

- **Review Cycle:**
    This SOP should be reviewed annually or after any major incident where coordination, handoff, action tracking, or decision logging caused delay or confusion.

- **Feedback Process:**
    Feedback is collected during the PIR from the Incident Commander, Deputy Incident Commander, Technical Lead, Communications Lead, and Scribe.

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
