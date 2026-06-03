# RB-003.2-Process Tree Analysis

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Process Tree Analysis | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- EDR telemetry access
- Process creation logs
- Command-line arguments data
- File execution telemetry
- User activity logs
- EDR platform access
- SIEM platform access
- Process analysis tools
- Threat intelligence platform access

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment** — Verify responsibility for malware execution analysis

2. **Notify Stakeholders** — Alert incident management of process analysis initiation

3. **Access Target System/Resource** — Prepare EDR and SIEM for process tree review

4. **Document Current State** — Record initial EDR alerts and suspicious process observations

5. **Preserve Evidence (if applicable)** — Capture process execution artifacts and memory images

6. **Execute Task Steps**

   6.1. **Identify Initial Execution Process**
   - Determine initial executable
   - Identify launch source
   - Document user context
   - Record execution timestamp

   6.2. **Review Parent-Child Relationships**
   - Identify suspicious ancestry
   - Flag office applications spawning scripts
   - Document LOLBin usage
   - Identify script interpreter execution

   6.3. **Analyse Command-Line Arguments**
   - Review for encoded commands
   - Identify PowerShell abuse
   - Identify download cradles
   - Document obfuscation techniques
   - Flag suspicious parameters

   6.4. **Identify Secondary Payload Execution**
   - Look for additional binaries
   - Identify script downloads
   - Document DLL execution
   - Identify injection behaviour

   6.5. **Review Network Activity**
   - Identify external connections
   - Document C2 behaviour
   - Review DNS activity
   - Determine beaconing intervals

   6.6. **Correlate with User Activity**
   - Determine if execution was user initiated
   - Identify phishing involvement
   - Determine if remote execution was involved

7. **Verify Task Completion** — Confirm process execution timeline and parent-child mapping complete

8. **Update Incident Documentation** — Record suspicious process chains and execution sources

9. **Escalate if Issues Arise** — Route to phishing or lateral movement playbooks as appropriate

10. **Hand Off or Notify Next Responsible Party** — Pass to persistence analysis or containment teams

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Phishing delivery identified | Escalate to PB-001 |
| Remote execution identified | Investigate lateral movement |
| Persistence identified | Proceed to RB-003.3 |

---

## Output

- Process execution timeline
- Parent-child process map
- Suspicious command-lines
- Execution source assessment

---

## Common Failure Modes

- Focusing only on final payload
- Ignoring script interpreter activity
- Missing LOLBin execution

---

## Automation Hooks

- Auto-process tree generation
- Auto-command-line decoding
- Auto-behaviour correlation

---

## Related

- Playbook: [PB-003 Endpoint Malware Infection](../../playbooks/PB-003-endpoint-malware.md)
- Previous: [RB-003.1 EDR Alert Triage](./RB-003.1-edr-alert-triage.md)
- Next: [RB-003.3 Persistence Mechanism Hunt](./RB-003.3-persistence-mechanism-hunt.md)
