# RB-002.9-Threat Actor TTP Mapping

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Threat Actor TTP Mapping | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- IOC list from investigation
- Payload analysis results
- Authentication telemetry
- EDR telemetry
- Threat intelligence reporting access
- Threat intelligence platforms access
- MITRE ATT&CK framework
- SIEM platform access
- EDR platform access
- Malware analysis reports

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment** — Verify responsibility for TTP analysis and threat actor assessment

2. **Notify Stakeholders** — Alert threat intelligence and security teams of analysis initiation

3. **Access Target System/Resource** — Prepare threat intel platforms and MITRE ATT&CK references

4. **Document Current State** — Record initial IOCs and observed techniques

5. **Preserve Evidence (if applicable)** — Capture analysis artifacts for threat intel records

6. **Execute Task Steps**

   6.1. **Review Observed Techniques**
   - Identify initial access methods
   - Document credential access techniques
   - Document lateral movement methods
   - Identify persistence mechanisms
   - Document exfiltration behaviour

   6.2. **Map TTPs to MITRE ATT&CK**
   - Document technique IDs
   - Record sub-techniques
   - Describe observed behaviours
   - Identify detection opportunities

   6.3. **Correlate with Known Ransomware Groups**
   - Compare against public reporting
   - Cross-reference threat intel feeds
   - Identify known infrastructure overlaps
   - Review ransom note patterns

   6.4. **Identify Detection Gaps**
   - Determine missed detections
   - Document delayed alerts
   - Identify visibility gaps
   - Assess logging deficiencies

   6.5. **Update Defensive Content**
   - Create or update detection rules
   - Create hunt queries
   - Update block lists
   - Document threat intel references

7. **Verify Task Completion** — Confirm TTP mapping complete and detection gaps identified

8. **Update Incident Documentation** — Record TTP assessment and recommended hardening activities

9. **Escalate if Issues Arise** — Route novel threats to appropriate analysis teams

10. **Hand Off or Notify Next Responsible Party** — Pass to detection engineering and hardening teams

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Known threat actor identified | Prioritise actor-specific detections |
| Novel behaviour observed | Escalate for deeper analysis |
| Detection gaps identified | Prioritise hardening activities |

---

## Output

- TTP mapping report
- MITRE ATT&CK coverage
- Threat actor assessment
- Detection improvement recommendations

---

## Common Failure Modes

- Focusing only on malware hashes
- Ignoring attacker operational behaviour
- Missing pre-encryption activity

---

## Automation Hooks

- Auto-map ATT&CK techniques
- Auto-correlate threat intel
- Auto-generate IOC feeds

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Previous: [RB-002.8 Recovery & Restoration Coordination](./RB-002.8-recovery-restoration-coordination.md)
- Next: [RB-002.10 Post-Incident Hardening](./RB-002.10-post-incident-hardening.md)
