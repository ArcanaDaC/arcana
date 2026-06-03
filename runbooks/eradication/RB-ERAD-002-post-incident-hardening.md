# RB-002.10 Post-Incident Hardening

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Post-Incident Hardening | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- PIR findings
- Detection gaps
- TTP mapping report
- Recovery lessons learned
- Executive recommendations
- Access to SIEM
- Access to EDR platform
- Access to vulnerability management platform
- Access to identity management platform
- Access to network security tooling

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current security posture
   - Document existing controls

5. **Preserve Evidence (if applicable)**
   - Document pre-hardening configuration

6. **Execute Task Steps**
   - **6.1 Review Root Cause & Control Failures**
     - Identify initial access failures
     - Identify detection failures
     - Identify containment weaknesses
     - Identify recovery bottlenecks

   - **6.2 Improve Detection Coverage**
     - Implement new detection logic
     - Enhance telemetry collection
     - Improve alert tuning
     - Add hunt content

   - **6.3 Harden Identity Infrastructure**
     - Review privileged access
     - Review MFA coverage
     - Review service accounts
     - Review administrative segmentation

   - **6.4 Improve Network Segmentation**
     - Enhance east-west restrictions
     - Enhance administrative isolation
     - Enhance backup network isolation
     - Enhance critical infrastructure separation

   - **6.5 Strengthen Backup Security**
     - Implement immutable backups
     - Implement offline recovery capability
     - Implement backup monitoring
     - Implement backup access restrictions

   - **6.6 Conduct Lessons Learned Review**
     - Document what worked well
     - Document what failed
     - Document process improvements
     - Document tooling improvements

7. **Verify Task Completion**
   - Confirm hardening recommendations documented
   - Verify detection improvement plan created
   - Validate updated controls deployed
   - Verify lessons learned report complete

8. **Update Incident Documentation**
   - Record hardening actions
   - Document improvements made
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if critical detection gaps remain
   - Escalate if identity weaknesses identified
   - Escalate if recovery delays excessive

10. **Hand Off or Notify Next Responsible Party**
    - Notify security leadership of hardening plan
    - Provide lessons learned report

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Critical detection gaps remain | Prioritise remediation |
| Identity weaknesses identified | Accelerate IAM hardening |
| Recovery delays excessive | Review BCP/DR processes |

---

## Output

- Hardening recommendations
- Detection improvement plan
- Updated controls
- Lessons learned report

---

## Common Failure Modes

- Treating recovery as incident closure
- Ignoring identity weaknesses
- Failing to operationalise lessons learned

---

## Automation Hooks

- Auto-deploy detections
- Auto-validate segmentation changes
- Auto-track remediation tasks

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Previous: [RB-002.9 Threat Actor TTP Mapping](./RB-002.9-threat-actor-ttp-mapping.md)
