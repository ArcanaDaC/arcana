# PB-019: Major Security Incident Management

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-019: Major Security Incident Management | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    Provide a command-and-coordination playbook for Sev 0 or major security incidents. Use this playbook to establish incident command, run the war room, coordinate multiple technical playbooks, manage executive/legal communications, prioritise recovery, and track decisions until the incident is downgraded or closed.

- **Scope:**

    Applies to security incidents with major business, customer, regulatory, operational, or executive impact. This playbook does not replace technical playbooks; it coordinates them when the incident exceeds a single-team or single-scenario response.

## 2. Incident Identification & Criteria

**Incident Type:** Major Security Incident Management

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- Incident is declared Sev 0 or equivalent major incident
- Multiple technical playbooks must run concurrently under one command structure
- Critical business services, customer-facing systems, identity infrastructure, cloud tenant, backups, or security tooling are materially impacted
- Executive, legal, regulatory, customer, public, vendor, or law enforcement coordination is required
- Response will span multiple teams, geographies, shifts, or recovery phases

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | N/A |
| Sev 2 | Cross-team incident with material risk, limited business impact, or executive awareness required |
| Sev 1 | Major incident with confirmed business, customer, data, production, identity, cloud, or recovery impact |
| Sev 0 | Enterprise-wide, critical-service, regulated-data, public, extortion, destructive, or crisis-level impact |

## 3. Roles & Responsibilities

- **Incident Commander:** Owns command, severity, priorities, operating cadence, decision log, escalation, and downgrade/closure decisions.
- **Deputy Incident Commander:** Maintains action tracker, follows up on blockers, and supports continuity during extended response.
- **Technical Lead:** Coordinates technical workstreams and ensures relevant playbooks/runbooks are executed.
- **Communications Lead:** Coordinates stakeholder updates, executive briefings, internal messaging, and approved external communications.
- **Scribe:** Maintains incident timeline, action tracker, decision log, and evidence references.
- **Other Roles:**
    - **Legal / Compliance:** Assesses regulatory, contractual, legal, insurance, and disclosure obligations.
    - **Business / Service Owners:** Confirm business impact, recovery priority, customer impact, and operational constraints.
    - **Vendor Owner / Procurement:** Coordinates third-party support where vendor action is required.
    - **Customer Support / Success:** Coordinates customer-impact handling and support readiness.
    - **Recovery Lead:** Coordinates service restoration priorities, dependencies, and validation.

## 4. Initial Actions

- **Immediate Steps:**
    - Confirm the major incident declaration, severity, Incident Commander, Technical Lead, Communications Lead, Scribe, and executive sponsor.
    - Open the major incident war room, action tracker, decision log, and operating cadence.
        - 📘 [SOP-007: Major Incident War Room Management](../sops/SOP-007-major-incident-war-room-management.md)
    - Page required engineering, security, platform, application, identity, cloud, network, legal, communications, support, and vendor-owner teams.
        - 📘 [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - Identify active technical playbooks and assign owners for each workstream.
    - Start executive/legal communication process if major impact, customer impact, regulated data, or external communication is possible.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)

    > **Decision Point:**
    > - If the incident does not require major incident coordination → continue under the relevant technical playbook only.
    > - If major coordination is required → continue this playbook alongside all relevant technical playbooks.
    > - If external communications may be required → engage Legal/Compliance and Communications Lead before any external statement.

## 5. Investigation & Analysis

- **Evidence Collection:**
    - Confirm each technical workstream is preserving evidence through its linked playbook and runbooks.
    - Track evidence locations, owners, collection status, and gaps in the major incident action tracker.
    - Preserve command decisions, timelines, status updates, customer-impact assessments, and legal guidance as part of the incident record.

- **Analysis Steps:**
    - Maintain a consolidated incident timeline covering detection, impact, containment, eradication, recovery, communications, and decisions.
    - Track active technical workstreams and linked playbooks.
    - Confirm each workstream has a current hypothesis, scope, owner, next action, blocker, and next update time.
    - Maintain a business impact assessment covering services, customers, data, regions, revenue, operations, and recovery dependencies.


    > **Decision Point:**
    > Run the relevant technical playbooks concurrently based on the incident drivers:
    > - Ransomware or destructive activity → [PB-002: Ransomware](PB-002-ransomware.md)
    > - Malware or suspicious execution → [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) / [PB-011: Suspicious Execution](PB-011-suspicious-execution.md)
    > - Account, token, credential, or cloud identity compromise → [PB-004: Account Takeover](PB-004-account-takeover.md)
    > - Data exposure, staging, or exfiltration → [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    > - Cloud environment compromise → [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    > - Web application compromise → [PB-008: Web Application Attack](PB-008-web-application-attack.md)
    > - Privilege escalation → [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
    > - Lateral movement → [PB-010: Lateral Movement](PB-010-lateral-movement.md)
    > - Third-party compromise → [PB-012: Third-Party Compromise](PB-012-third-party-compromise.md)
    > - DDoS or availability attack → [PB-013: Distributed Denial of Service](PB-013-ddos.md)
    > - Lost/stolen device with major impact → [PB-014: Lost & Stolen Device](PB-014-lost-stolen-device.md)
    > - Active exploitation → [PB-015: Active Exploitation](PB-015-active-exploitation.md)
    > - Vulnerability or zero-day emergency → [PB-017: Vulnerability Response](PB-017-vulnerability-response.md) / [PB-018: Zero-Day Response](PB-018-zero-day-response.md)

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Confirm each technical workstream has an owner, containment objective, current action, risk, and rollback plan.
    - Prioritise containment actions that reduce active attacker access, customer impact, data exposure, destructive risk, and business-critical service impact.
    - Record containment decisions, risk acceptances, and business tradeoffs in the decision log.

- **Eradication Steps:**
    - Confirm each technical playbook owns eradication of incident-specific root cause, persistence, malicious access, and vulnerable exposure.
    - Track cross-workstream dependencies such as identity resets, network segmentation, rebuilds, vendor support, legal holds, and business approvals.
    - Ensure eradication is not declared complete until technical leads confirm root cause and persistence have been addressed.

- **Recovery Steps:**
    - Establish recovery priority based on business criticality, dependency order, customer impact, safety, and residual risk.
        - 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
    - Gate service restoration on containment status, integrity validation, monitoring readiness, and business owner approval.
    - Downgrade the major incident only after the Incident Commander confirms stable containment, recovery path, communications status, and remaining risk.

## 7. Communication & Escalation

- **Internal Communication:**
    - Run major incident cadence, action tracking, decision logging, and status updates through the war room SOP.
        - 📘 [SOP-007: Major Incident War Room Management](../sops/SOP-007-major-incident-war-room-management.md)
    - Use geo handoff when command or workstreams transition across shifts or regions.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - Notify affected users or broader employee groups when user action is required.
        - 📘 [SOP-004: User Notification During a Security Incident](../sops/SOP-004-user-notification.md)

- **External Communication:**
    - Coordinate executive, legal, regulatory, customer, partner, insurer, media, or law enforcement communications through approved processes.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - Coordinate vendor communications through the vendor communication SOP.
        - 📘 [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Major incident cadence, action tracking, or decision logging required | [SOP-007: Major Incident War Room Management](../sops/SOP-007-major-incident-war-room-management.md) |
    | Executive, legal, regulatory, customer, media, or insurer coordination required | [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md) |
    | Vendor or provider support required | [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md) |
    | Multi-geo or long-running response requires command transfer | [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md) |
    | Affected-user action or advisory required | [SOP-004: User Notification During a Security Incident](../sops/SOP-004-user-notification.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a PIR covering command structure, severity decisions, communication cadence, decision quality, handoffs, technical workstream coordination, recovery prioritisation, and stakeholder outcomes.
    - Review whether the major incident was declared early enough and whether it was downgraded at the right time.
    - Identify coordination gaps, unclear ownership, delayed decisions, missing evidence, or communication failures.

- **Documentation Updates:**
    - Update technical playbooks, SOPs, escalation paths, contact lists, status templates, decision log templates, and recovery priority guidance based on PIR findings.
    - Track all follow-up actions with owners, due dates, and validation criteria.

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-002: Ransomware](PB-002-ransomware.md)
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    - [PB-008: Web Application Attack](PB-008-web-application-attack.md)
    - [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
    - [PB-010: Lateral Movement](PB-010-lateral-movement.md)
    - [PB-011: Suspicious Execution](PB-011-suspicious-execution.md)
    - [PB-012: Third-Party Compromise](PB-012-third-party-compromise.md)
    - [PB-013: Distributed Denial of Service](PB-013-ddos.md)
    - [PB-014: Lost & Stolen Device](PB-014-lost-stolen-device.md)
    - [PB-015: Active Exploitation](PB-015-active-exploitation.md)
    - [PB-017: Vulnerability Response](PB-017-vulnerability-response.md)
    - [PB-018: Zero-Day Response](PB-018-zero-day-response.md)

- **Runbooks:**
    - [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)

- **SOPs:**
    - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-004: User Notification During a Security Incident](../sops/SOP-004-user-notification.md)
    - [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)
    - [SOP-007: Major Incident War Room Management](../sops/SOP-007-major-incident-war-room-management.md)

## 10. Appendices

- **Expected Outputs:**
    - Major incident declaration and severity record
    - Active workstream list and owners
    - War room link, action tracker, and decision log
    - Consolidated incident timeline
    - Executive/legal/customer/vendor communication records
    - Recovery priority and dependency plan
    - Downgrade or closure decision record
    - PIR action items and owners

- **Common Failure Modes:**
    - Declaring a major incident too late
    - Running multiple technical playbooks without a single command structure
    - Missing decision logs or action owners
    - Allowing recovery work to start before containment and integrity validation
    - Sending external communications before legal and communications approval
    - Losing context during long-running or multi-geo handoffs

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
