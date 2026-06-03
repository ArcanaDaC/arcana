# RB-003.7 Recovery & Rebuild

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Recovery & Rebuild | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Malware analysis findings
- Persistence findings
- EDR telemetry
- Recovery requirements
- Business impact assessment
- Access to EDR platform
- Access to endpoint management platform
- Access to rebuild/imaging systems
- Access to SIEM
- Access to vulnerability management platform

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current infection status
   - Document affected systems

5. **Preserve Evidence (if applicable)**
   - Preserve malware analysis findings
   - Preserve EDR logs

6. **Execute Task Steps**
   - **6.1 Determine Recovery Approach**
     - Assess malware severity
     - Assess persistence mechanisms
     - Assess system criticality
     - Assess confidence in cleanup capability
     - Determine whether cleanup is sufficient or full rebuild required

   - **6.2 Remove Malware Artefacts**
     - Remove malicious binaries
     - Remove persistence mechanisms
     - Remove malicious services
     - Remove registry modifications
     - Remove scheduled tasks

   - **6.3 Rebuild Endpoint (If Required)**
     - Perform full system reimage
     - Perform operating system validation
     - Perform security tooling reinstallation
     - Perform patch validation

   - **6.4 Reset Credentials**
     - Reset user credentials
     - Reset privileged credentials (if exposed)
     - Reset service account credentials (if applicable)

   - **6.5 Validate Endpoint Integrity**
     - Confirm no active malware
     - Confirm no persistence remains
     - Confirm EDR operational
     - Confirm security controls healthy
     - Confirm network activity normal

   - **6.6 Return Endpoint to Service**
     - Gradually reconnect to network
     - Gradually restore user access
     - Monitor closely for reinfection

7. **Verify Task Completion**
   - Confirm recovery status documented
   - Verify rebuild status documented
   - Validate validation findings documented
   - Verify endpoint restoration timeline documented

8. **Update Incident Documentation**
   - Record recovery actions
   - Document rebuild status
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if reinfection observed
   - Escalate if persistence remains
   - Escalate if credential theft confirmed

10. **Hand Off or Notify Next Responsible Party**
    - Notify endpoint team of recovery status
    - Provide validation findings

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Reinfection observed | Re-isolate immediately |
| Persistence remains | Repeat eradication |
| Credential theft confirmed | Expand credential resets |

---

## Output

- Recovery status
- Rebuild status
- Validation findings
- Endpoint restoration timeline

---

## Common Failure Modes

- Cleaning instead of rebuilding high-risk systems
- Returning systems to service too early
- Ignoring credential exposure

---

## Automation Hooks

- Auto-reimage workflows
- Auto-validation checks
- Auto-reinfection monitoring

---

## Related

- Playbook: [PB-003 Endpoint Malware Infection](../../playbooks/PB-003-endpoint-malware.md)
- Previous: [RB-003.6 Memory Acquisition & Analysis](./RB-003.6-memory-acquisition-analysis.md)
