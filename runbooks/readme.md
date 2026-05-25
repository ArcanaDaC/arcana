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

Runbooks are organised by incident category.

### Current Categories

| Category | Description |
|---|---|
| phishing | Phishing and credential theft response |
| ransomware | Ransomware containment and recovery |
| endpoint-malware | Endpoint malware investigation and recovery |
| account-takeover | Identity and account compromise |
| data-exfiltration | Data theft and exfiltration response |
| insider-threat | Insider threat investigations |
| cloud-compromise | Cloud infrastructure compromise |
| web-application-attack | Web application attack response |
| privilege-escalation | Privilege escalation investigations |
| lateral-movement | Lateral movement investigations |
| suspicious-execution | Suspicious process execution |
| third-party-compromise | Vendor and supply-chain incidents |
| ddos | Availability and DDoS incidents |
| lost-stolen-device | Lost or stolen corporate devices |
| active-exploitation | Active exploitation response |
| business-email-compromise | Business email compromise investigations |
| vulnerability-response | Vulnerability and patch response |
| zero-day-response | Zero-day exploitation response |
| cloud-identity-compromise | Cloud identity compromise |
| major-incident-management | Enterprise incident coordination |

---

## Naming Convention

### Runbooks

```text
RB-<playbook>.<runbook>-<slug>.md
```

### Example

```text
RB-001.1-email-triage-header-analysis.md
RB-002.1-rapid-containment-network-segmentation.md
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
