# Arcana Runbooks

## Overview

Arcana Runbooks provide detailed operational procedures that support incident response playbooks.

Runbooks are execution-focused and designed to guide responders through:
- containment
- investigation
- analysis
- eradication
- recovery
- post-incident activities

Each runbook is linked from a parent playbook and focuses on a specific operational task or response phase.

---

## Structure

Runbooks are organised by response phase.

### Current Categories

| Category | Description |
|---|---|
| triage | Initial triage task |
| analysis | Investigation and analysis tasks |
| contain | Containment actions |
| eradication | Eradication and removal tasks |
| evidence | Evidence acquisition and preservation |
| recovery | Recovery and restoration tasks |
| post-incident | Post-incident tasks |

---

## Naming Convention

### Runbooks

```text
RB-<CATEGORY>-###-<slug>.md
```

Where:
- `<CATEGORY>` is the response phase (e.g. `TRIAGE`, `ANALYSIS`, `CONTAIN`, `ERAD`, `EVIDENCE`, `RECOVERY`, `POST`)
- `###` is a zero-padded sequential number within the category
- `<slug>` is a short, human-readable description using hyphens

### Examples

```text
RB-TRIAGE-001-email-triage-header-analysis.md
RB-CONTAIN-002-rapid-containment-network-segmentation.md
RB-RECOVERY-003-user-recovery-access-restoration.md
```

---

## Design Principles

Runbooks should be:

- Operationally focused
- Clear and actionable
- Vendor-neutral where possible
- Automation-friendly
- Markdown-native
- Easy to adapt and extend

---

## Related Components

| Component | Purpose |
|---|---|
| Playbooks | High-level response workflows |
| Runbooks | Detailed operational procedures |
| SOPs | Standard operational processes |
| KB Articles | Technical reference material |
| PIRs | Post-incident reviews |
| Templates | Reporting and communication templates |

---

## Contribution Guidance

When creating or updating runbooks:

- Focus on real-world operational workflows
- Keep procedures actionable
- Avoid excessive theory
- Include escalation paths and decision points
- Consider automation opportunities
- Maintain consistent formatting

---

## Status Definitions

| Status | Meaning |
|---|---|
| Operational | Runbook considered production-ready |
| Placeholder | Structure defined, content in development |
| Experimental | Under active testing or refinement |

---

## License

Refer to the root repository license for usage and contribution terms.
