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

Each playbook links to one or more runbooks that contain detailed operational procedures.

### Example

```text
PB-001-phishing.md
└── RB-001.1-email-triage-header-analysis.md
└── RB-001.2-url-detonation-analysis.md
└── RB-001.3-credential-exposure-validation.md
```

---

## Current Playbooks

| ID | Playbook | Status |
|----|-----------|--------|
| PB-001 | Phishing | Operational |
| PB-002 | Ransomware | Operational |
| PB-003 | Endpoint Malware | Placeholder |
| PB-004 | Account Takeover | Placeholder |
| PB-005 | Data Exfiltration | Placeholder |
| PB-006 | Insider Threat | Placeholder |
| PB-007 | Cloud Compromise | Placeholder |
| PB-008 | Web Application Attack | Placeholder |
| PB-009 | Privilege Escalation | Placeholder |
| PB-010 | Lateral Movement | Placeholder |
| PB-011 | Suspicious Execution | Placeholder |
| PB-012 | Third-Party Compromise | Placeholder |
| PB-013 | DDoS | Placeholder |
| PB-014 | Lost / Stolen Device | Placeholder |
| PB-015 | Active Exploitation | Placeholder |
| PB-016 | Business Email Compromise | Placeholder |
| PB-017 | Vulnerability Response | Placeholder |
| PB-018 | Zero-Day Response | Placeholder |
| PB-019 | Cloud Identity Compromise | Placeholder |
| PB-020 | Major Security Incident Management | Placeholder |

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
