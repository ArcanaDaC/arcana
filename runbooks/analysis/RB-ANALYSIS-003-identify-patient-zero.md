# RB-002.2-Identify Patient Zero

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Identify Patient Zero | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- EDR telemetry access
- Authentication logs access
- SIEM timeline data
- Endpoint timeline information
- Ransomware execution timestamps
- SIEM platform access
- EDR platform access
- Active Directory logs access
- Email telemetry access
- VPN logs access

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment** — Verify responsibility for identifying initial compromise point

2. **Notify Stakeholders** — Alert incident management of timeline analysis initiation

3. **Access Target System/Resource** — Prepare SIEM and EDR for historical timeline review

4. **Document Current State** — Record known encryption events and timeline markers

5. **Preserve Evidence (if applicable)** — Capture forensic snapshots of affected systems

6. **Execute Task Steps**

   6.1. **Build Initial Timeline**
   - Determine earliest encryption event
   - Identify first ransomware execution
   - Flag first suspicious authentication event

   6.2. **Identify Earliest Impacted Host**
   - Review file modification timestamps
   - Examine EDR detections
   - Document user reports
   - Review network telemetry

   6.3. **Review Initial Access Indicators**
   - Check for phishing activity
   - Investigate VPN compromise indicators
   - Assess exposed RDP exposure
   - Review credential theft indicators
   - Identify malware download activity

   6.4. **Analyse User Activity**
   - Review privileged account usage
   - Identify unusual login locations
   - Document service account activity
   - Flag MFA anomalies

   6.5. **Identify Propagation Path**
   - Determine lateral movement techniques
   - Track shared credential usage
   - Identify administrative tool usage
   - Document remote execution methods

7. **Verify Task Completion** — Confirm patient zero identified and propagation path documented

8. **Update Incident Documentation** — Record timeline and initial access vector in incident record

9. **Escalate if Issues Arise** — Route to appropriate escalation playbooks based on findings

10. **Hand Off or Notify Next Responsible Party** — Pass to encryption scope assessment team

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Phishing identified | Escalate to PB-001 |
| Privileged account abuse | Escalate to RB-002.6 |
| Internet-facing exposure identified | Emergency exposure review |

---

## Output

- Suspected patient zero
- Initial access vector
- Timeline of compromise
- Propagation path summary

---

## Common Failure Modes

- Assuming first detected host is patient zero
- Ignoring authentication telemetry
- Missing dormant attacker activity prior to encryption

---

## Automation Hooks

- Auto-build event timeline
- Auto-correlate authentication events
- Auto-identify earliest detections

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Previous: [RB-002.1 Rapid Containment & Network Segmentation](./RB-002.1-rapid-containment-network-segmentation.md)
- Next: [RB-002.3 Encryption Scope Assessment](./RB-002.3-encryption-scope-assessment.md)
