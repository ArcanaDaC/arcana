# SOP-002: Incident Handoff Between Geos

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | SOP-002: Incident Handoff Between Geos | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
  Define the process for handing off an active security incident from one geographic region's IR team to another, ensuring continuity of response, no loss of context, and clear transfer of command and accountability.

- **Scope:**
  Applies to all active security incidents that span or transition across geographic regions (geos) and their respective IR teams (e.g. APAC → EMEA → Americas). This SOP applies regardless of incident severity

## 2. Definitions

- **Geo:** A geographic region with a dedicated IR team operating in a specific time zone (e.g. APAC, EMEA, Americas).
- **Handing-Off Team:** The IR team whose shift is ending and who is transferring ownership of the incident.
- **Receiving Team:** The IR team whose shift is beginning and who is accepting ownership of the incident.
- **Incident Commander (IC):** The individual with overall command of the incident response at any given time. Command transfers as part of this handoff.
- **Handoff Brief:** A structured verbal or written summary of the incident delivered by the Handing-Off Team to the Receiving Team.
- **Handoff Window:** The scheduled overlap period between two geo shifts during which the handoff occurs.
- **War Room:** The dedicated communication channel (e.g. Slack channel, video bridge) used for real-time incident coordination.
- **Incident Ticket:** The authoritative record of the incident, including all actions, findings, and decisions.

## 3. Roles & Responsibilities

- **Outgoing Incident Commander (Handing-Off IC):**
  - Prepares the Handoff Brief ahead of the Handoff Window
  - Updates the incident ticket with the current state before the handoff
  - Delivers the Handoff Brief to the Receiving Team
  - Formally transfers command to the Incoming IC
  - Remains available for questions during the Handoff Window

- **Incoming Incident Commander (Receiving IC):**
  - Reviews the incident ticket prior to the Handoff Brief
  - Participates in the Handoff Brief and asks clarifying questions
  - Formally accepts command of the incident
  - Confirms understanding of all open actions and outstanding tasks

- **Outgoing IR Team Members:**
  - Update their individual task notes and action items in the incident ticket before handoff
  - Are available during the Handoff Window to answer questions from the Receiving Team

- **Receiving IR Team Members:**
  - Review the incident ticket and assigned tasks prior to or during the Handoff Window
  - Confirm acceptance of assigned tasks after the handoff

- **IR Team Leads / Managers (both geos):**
  - Ensure the Handoff Window is observed and staffed
  - Escalate if a handoff cannot be completed within the defined window

## 4. Procedure

### 4.1 Prerequisites

- An active incident ticket exists and is up to date
- Both the Handing-Off and Receiving Teams have access to the incident ticket and War Room
- A scheduled Handoff Window is defined (ideally a 30-minute overlap between geo shifts)
- The Receiving Team's IC has been identified prior to the handoff

### 4.2 Step-by-Step Instructions

1. **Prepare the incident ticket (Handing-Off IC - 30 mins before Handoff Window)**
   - Ensure the incident ticket reflects the current state of the incident, including:
     - Current severity level
     - A concise incident summary (what happened, what is known, what is unknown)
     - All actions taken to date, with timestamps
     - Open action items and who is responsible
     - Hypotheses under investigation
     - Any containment measures currently in place
     - Key evidence collected and its location
     - Decisions made and their rationale
     - Any pending escalations or notifications

2. **Prepare the Handoff Brief (Handing-Off IC - 15 mins before Handoff Window)**
   - Write or structure a verbal brief using the following format:
     - **Situation:** What happened and what is the current state?
     - **Background:** How did we get here? Key timeline of events.
     - **Assessment:** What do we believe is happening? Current hypotheses.
     - **Open Actions:** What tasks are outstanding and who owns them?
     - **Risks & Watch Points:** What are we worried about? What should the Receiving Team watch for?
     - **Immediate Priorities:** What should the Receiving Team focus on first?

3. **Notify the Receiving Team (Handing-Off IC)**
   - Post in the War Room that the handoff is commencing and tag the Receiving IC
   - Share the Handoff Brief in the incident ticket or War Room

4. **Conduct the Handoff Brief (both teams - during Handoff Window)**
   - Deliver the Handoff Brief verbally or in writing
   - Allow the Receiving Team to ask clarifying questions
   - Walk through all open action items and confirm ownership transfer

5. **Update the War Room (Receiving IC)**
   - Post in the War Room confirming the handoff is complete, who the new IC is, and the immediate priorities for the new shift

6. **Handing-Off Team stands down**
   - The Handing-Off IC and team members are released from active duty on this incident

## 5. Compliance & Auditability

- The command transfer must be logged in the incident ticket and/or war room with timestamps and the names of both ICs.
- The Handoff Brief must be retained in the incident ticket or War Room as a permanent record.
- Compliance with this SOP is reviewed during the Post-Incident Review (PIR), with specific attention to whether any context was lost during handoff.
- IR Team Leads from both geos are responsible for confirming the handoff was completed within the defined Handoff Window.

## 6. Communication & Escalation

- **Internal Communication:**
  - All handoff activity is documented in the War Room and the incident ticket.
  - Both geo IR Team Leads should be notified if a handoff is delayed or cannot be completed on schedule.

- **Escalation Criteria:**
  - The Receiving Team cannot staff an IC for the incoming shift → escalate to the Receiving Geo's IR Team Lead and IR Manager immediately.
  - The Handing-Off Team cannot complete the Handoff Brief due to ongoing time-critical actions → the Receiving IC shadows the active response and a deferred brief is delivered as soon as practicable, no later than 30 minutes into the new shift.
  - Context loss is identified after the handoff → the Receiving IC pages the Outgoing IC for an async clarification call.

## 7. References & Linked Resources

- **Playbooks:**
  - [PB-002: Ransomware Incident Response](../playbooks/PB-002-ransomware.md)

## 8. Appendices

### Appendix A: Handoff Brief Template

Use this template to structure the written Handoff Brief in the incident ticket or War Room:

```
## Incident Handoff Brief - [Date/Time] [Timezone]

**Outgoing IC:** [Name]
**Incoming IC:** [Name]

### Situation
[Current state of the incident in 2–3 sentences]

### Background
[How did we get here? Key events and timeline]

### Assessment
[Current working hypothesis / what we believe is happening]

### Open Actions
| Action | Owner | Priority | Notes |
|--------|-------|----------|-------|
| [Task] | [Name] | [High/Med/Low] | [Any relevant context] |

### Risks & Watch Points
[What should the Receiving Team monitor or be cautious about?]

### Immediate Priorities
1. [First priority]
2. [Second priority]
3. [Third priority]

### Command Transfer
- Command transferred by: [Outgoing IC Name] at [Timestamp]
- Command accepted by: [Incoming IC Name] at [Timestamp]
```

### Appendix B: Contact List

| Role | Name | Contact |
|------|------|---------|
| APAC IR Team Lead | [Name] | [Contact] |
| EMEA IR Team Lead | [Name] | [Contact] |
| Americas IR Team Lead | [Name] | [Contact] |
| IR Manager | [Name] | [Contact] |

## 9. Review & Maintenance

- **Review Cycle:**
  This SOP should be reviewed annually, or following any incident where a handoff failure or context loss contributed to a degraded response.

- **Feedback Process:**
  Feedback is collected during the PIR. The outgoing and incoming ICs are both asked to comment on whether the handoff was effective. Improvements are incorporated into the next version of this SOP.

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
