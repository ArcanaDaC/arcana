# RB-003.3 Persistence Mechanism Hunt

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Persistence Mechanism Hunt | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- EDR telemetry
- Registry activity
- Scheduled task logs
- Service creation logs
- Startup artefacts
- Access to EDR platform
- Access to Autoruns
- Access to PowerShell
- Access to registry analysis tools
- Access to SIEM

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current startup configuration
   - Document current services and tasks

5. **Preserve Evidence (if applicable)**
   - Document current registry state

6. **Execute Task Steps**
   - **6.1 Review Startup Persistence**
     - Check startup folders
     - Check registry run keys
     - Check startup scripts
     - Check login items

   - **6.2 Identify Scheduled Tasks**
     - Review newly created tasks
     - Review suspicious execution paths
     - Review obfuscated task names
     - Review hidden tasks

   - **6.3 Review Services**
     - Identify newly installed services
     - Identify suspicious service binaries
     - Identify unsigned service executables
     - Identify unusual service descriptions

   - **6.4 Review WMI Persistence**
     - Check for WMI event subscriptions
     - Check for suspicious consumers
     - Check for malicious filters

   - **6.5 Identify Registry Persistence**
     - Review run keys
     - Review shell modifications
     - Review file association hijacking
     - Review defender exclusions

   - **6.6 Assess Enterprise Scope**
     - Determine single-host persistence
     - Determine shared persistence patterns
     - Determine GPO-based persistence
     - Determine multi-host compromise

7. **Verify Task Completion**
   - Confirm persistence mechanism inventory documented
   - Verify scope assessment completed
   - Validate removal recommendations provided
   - Verify IOC updates documented

8. **Update Incident Documentation**
   - Record persistence findings
   - Document remediation actions
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if enterprise-wide persistence identified
   - Escalate if GPO abuse identified
   - Escalate if persistence survives reboot

10. **Hand Off or Notify Next Responsible Party**
    - Notify endpoint team of findings
    - Provide removal recommendations

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Enterprise-wide persistence identified | Expand scope immediately |
| GPO abuse identified | Escalate to PB-009 |
| Persistence survives reboot | Maintain containment |

---

## Output

- Persistence mechanism inventory
- Scope assessment
- Removal recommendations
- IOC updates

---

## Common Failure Modes

- Removing malware but leaving persistence
- Ignoring WMI persistence
- Missing scheduled task abuse

---

## Automation Hooks

- Auto-persistence scanning
- Auto-registry anomaly detection
- Auto-task enumeration

---

## Related

- Playbook: [PB-003 Endpoint Malware Infection](../../playbooks/PB-003-endpoint-malware.md)
- Previous: [RB-003.2 Process Tree Analysis](./RB-003.2-process-tree-analysis.md)
- Next: [RB-003.4 Host Isolation](./RB-003.4-host-isolation.md)
