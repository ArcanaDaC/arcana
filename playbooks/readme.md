# Arcana Playbooks

## Overview

Arcana Playbooks provide structured, operational incident response workflows for common and high-impact security incidents.

Each playbook is designed to support responders during active incidents by providing:

- Clear response objectives
- Escalation guidance
- Decision points
- Linked runbooks
- Containment workflows
- Recovery coordination
- Post-incident actions

Playbooks are intentionally Markdown-first to allow teams to:
- Clone and deploy quickly
- Integrate into existing tooling
- Adapt workflows to their environment
- Contribute improvements easily

---

## Structure

Each playbook follows a standard operational structure so responders can move through an incident consistently:

1. **Purpose & Scope** - defines when the playbook applies and what is out of scope.
2. **Incident Identification & Criteria** - lists trigger conditions and severity guidance.
3. **Roles & Responsibilities** - identifies response roles and supporting teams.
4. **Initial Actions** - validates the incident, starts documentation, and links triage runbooks.
5. **Investigation & Analysis** - collects evidence, performs analysis, and links analysis/evidence runbooks.
6. **Containment, Eradication & Recovery** - links containment, eradication, and recovery runbooks.
7. **Communication & Escalation** - defines internal/external communication paths and sibling-playbook escalation criteria.
8. **Post-Incident Activities** - captures lessons learned, hardening, and follow-up work.
9. **References & Linked Resources** - lists every linked playbook, runbook, and SOP used by the workflow.
10. **Appendices** - captures expected outputs, common failure modes, contacts, or supporting notes.

### Relationship to Runbooks and SOPs

Playbooks provide the scenario-level workflow. They should not duplicate detailed task instructions when an existing runbook or SOP can be referenced.

- **Runbooks** are linked for technical tasks such as evidence acquisition, alert triage, analysis, containment, recovery, and post-incident hardening.
- **SOPs** are linked for repeatable cross-team processes such as paging, geo handoff, executive/legal communications, vendor communication, user notification, and employee verification.

### Example

```text
PB-014-lost-stolen-device.md
├── SOP-006-employee-verification.md
├── RB-TRIAGE-006-lost-stolen-device-validation.md
├── RB-EVIDENCE-002-host-log-acquisition.md
├── RB-ANALYSIS-032-device-security-posture-assessment.md
├── RB-CONTAIN-011-remote-device-lock-wipe.md
└── RB-RECOVERY-003-user-recovery-access-restoration.md
```

---

## Current Playbooks

| ID | Playbook | Status |
|----|-----------|--------|
| PB-001 | Phishing | Operational |
| PB-002 | Ransomware | Operational |
| PB-003 | Endpoint Malware | Operational |
| PB-004 | Account Takeover | Operational |
| PB-005 | Data Exfiltration | Operational |
| PB-006 | Insider Threat | Placeholder |
| PB-007 | Cloud Compromise | Operational |
| PB-008 | Web Application Attack | Operational |
| PB-009 | Privilege Escalation | Operational |
| PB-010 | Lateral Movement | Operational |
| PB-011 | Suspicious Execution | Operational |
| PB-012 | Third-Party Compromise | Operational |
| PB-013 | DDoS | Operational |
| PB-014 | Lost / Stolen Device | Operational |
| PB-015 | Active Exploitation | Operational |
| PB-016 | Business Email Compromise | Operational |
| PB-017 | Vulnerability Response | Operational |
| PB-018 | Zero-Day Response | Operational |
| PB-019 | Major Security Incident Management | Operational |

---

## Design Principles

Arcana playbooks are designed around the following principles:

### Operational First

Playbooks are written for responders operating during active incidents — not for compliance documentation.

### Markdown Native

All content is plain Markdown for:
- portability
- version control
- offline access
- automation compatibility

### Execution-Focused

Playbooks answer:

> “What do we do right now?”

rather than providing high-level theory alone.

### Extensible

Teams are encouraged to:
- modify workflows
- adapt tooling references
- contribute improvements
- build automation integrations

---

## Recommended Workflow

During an incident:

1. Identify the appropriate playbook
2. Follow linked runbooks in sequence
3. Escalate based on decision points
4. Document actions and findings
5. Complete post-incident activities

---

## Related Components

Arcana is structured around several interconnected components:

| Component | Purpose |
|---|---|
| Playbooks | High-level response workflows |
| Runbooks | Detailed operational procedures |
| SOPs | Standard operational processes |
| KB Articles | Technical reference material |
| PIRs | Post-incident reviews |
| Templates | Reporting and communication templates |

---

## Planned Future Enhancements

- Notebook-based operational workflows
- Response-as-code integrations
- SOAR automation mappings
- ATT&CK mappings
- PR3TACK proactive response mappings
- Detection engineering integration
- Static documentation site generation

---

## Contribution Guidance

Contributions should prioritise:

- Operational clarity
- Real-world applicability
- Vendor-neutral guidance where possible
- Consistent formatting
- Actionable workflows

Avoid:
- Excessive theory
- Compliance-heavy language
- Tool-specific lock-in unless necessary

---

## Status Definitions

| Status | Meaning |
|---|---|
| Operational | Playbook considered production-ready |
| Placeholder | Structure defined, content in development |
| Experimental | Under active testing/refinement |

---

## License

Refer to the root repository license for usage and contribution terms.
