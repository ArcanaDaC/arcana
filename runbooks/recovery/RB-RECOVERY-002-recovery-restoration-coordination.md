# RB-002.8 Recovery & Restoration Coordination

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Recovery & Restoration Coordination | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Recovery prioritisation list
- Backup validation status
- Containment status
- Infrastructure dependency mapping
- Business impact assessment
- Access to backup platform
- Access to virtualisation platform
- Access to asset inventory
- Access to SIEM
- Access to EDR platform

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current containment status
   - Document current infrastructure state

5. **Preserve Evidence (if applicable)**
   - Document pre-recovery configuration

6. **Execute Task Steps**
   - **6.1 Validate Containment Status**
     - Confirm propagation stopped
     - Confirm persistence mechanisms addressed
     - Confirm privileged access reviewed
     - Confirm compromised systems isolated

   - **6.2 Prioritise Recovery Activities**
     - Restore based on business criticality
     - Restore based on dependency order
     - Restore based on infrastructure requirements
     - Restore based on recovery feasibility

   - **6.3 Restore Systems in Phases**
     - Use staged recovery approach
     - Restore core infrastructure first
     - Restore identity systems
     - Restore critical applications
     - Restore user endpoints

   - **6.4 Validate Restored Systems**
     - Check system functionality
     - Check malware absence
     - Check authentication integrity
     - Check network connectivity

   - **6.5 Monitor for Reinfection**
     - Monitor EDR telemetry
     - Monitor authentication anomalies
     - Monitor file modification spikes
     - Monitor suspicious outbound traffic

   - **6.6 Reintroduce Systems Carefully**
     - Gradually reconnect segmented systems
     - Gradually restore trust relationships
     - Gradually re-enable network pathways

7. **Verify Task Completion**
   - Confirm recovery status documented
   - Verify restored system inventory documented
   - Validate reinfection monitoring status
   - Verify business restoration progress assessed

8. **Update Incident Documentation**
   - Record restoration actions
   - Document systems restored
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if reinfection activity observed
   - Escalate if authentication instability detected
   - Escalate if backup corruption discovered

10. **Hand Off or Notify Next Responsible Party**
    - Notify infrastructure team of restoration status
    - Provide monitoring recommendations

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Reinfection activity observed | Halt restoration immediately |
| Authentication instability detected | Reassess identity integrity |
| Backup corruption discovered | Pause restoration planning |

---

## Output

- Recovery status
- Restored system inventory
- Reinfection monitoring status
- Business restoration progress

---

## Common Failure Modes

- Restoring too quickly
- Reconnecting infected systems
- Ignoring dependency order
- Failing to monitor for reinfection

---

## Automation Hooks

- Auto-monitor restoration health
- Auto-alert on reinfection indicators
- Auto-track restoration phases

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Previous: [RB-002.7 Escalation, Legal & Executive Communications](./RB-002.7-escalation-legal-executive-comms.md)
- Next: [RB-002.9 Threat Actor TTP Mapping](./RB-002.9-threat-actor-ttp-mapping.md)
