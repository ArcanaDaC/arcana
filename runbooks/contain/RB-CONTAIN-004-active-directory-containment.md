# RB-002.6 Active Directory Containment

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Active Directory Containment | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Domain Controller logs
- Authentication telemetry
- Privileged account activity
- EDR alerts
- SIEM detections
- Access to Active Directory
- Access to EDR platform
- Access to SIEM
- Access to identity provider
- Access to PowerShell
- Access to AD auditing tools

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current AD configuration
   - Document current account status

5. **Preserve Evidence (if applicable)**
   - Document current AD integrity status

6. **Execute Task Steps**
   - **6.1 Review Privileged Account Activity**
     - Identify domain admin usage
     - Identify enterprise admin activity
     - Identify service account anomalies
     - Identify newly created privileged accounts

   - **6.2 Disable Suspected Compromised Accounts**
     - Immediately disable compromised privileged accounts
     - Rotate privileged credentials
     - Reset KRBTGT if required

   - **6.3 Identify Persistence Mechanisms**
     - Review for scheduled tasks
     - Review for startup scripts
     - Review for GPO modifications
     - Review for malicious services
     - Review for shadow admin accounts

   - **6.4 Protect Domain Controllers**
     - Restrict administrative access
     - Isolate DCs if required
     - Review replication anomalies
     - Monitor authentication spikes

   - **6.5 Review Lateral Movement Techniques**
     - Look for PsExec usage
     - Look for WMI usage
     - Look for WinRM usage
     - Look for RDP usage
     - Look for pass-the-hash activity

   - **6.6 Validate Identity Infrastructure Integrity**
     - Confirm GPO integrity
     - Confirm replication health
     - Confirm authentication stability
     - Confirm administrative group integrity

7. **Verify Task Completion**
   - Confirm identity containment status
   - Verify compromised accounts list
   - Verify persistence findings
   - Validate AD integrity assessment

8. **Update Incident Documentation**
   - Record AD containment actions
   - Document account disablement
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if domain admin compromise detected
   - Escalate if persistence identified
   - Escalate if DC compromise suspected
   - Escalate if widespread privilege abuse detected

10. **Hand Off or Notify Next Responsible Party**
    - Notify AD team of changes
    - Provide compromised account list

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Domain Admin compromise | Immediate escalation |
| Persistence identified | Expand containment |
| DC compromise suspected | Crisis escalation |
| Widespread privilege abuse | Enterprise-wide credential reset review |

---

## Output

- Identity containment status
- Compromised accounts list
- Persistence findings
- AD integrity assessment

---

## Common Failure Modes

- Leaving privileged sessions active
- Failing to rotate service account credentials
- Ignoring shadow admin persistence
- Restoring systems before AD validation

---

## Automation Hooks

- Auto-disable accounts
- Auto-reset credentials
- Auto-identify privileged anomalies
- Auto-monitor replication integrity

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Previous: [RB-002.3 Encryption Scope Assessment](./RB-002.3-encryption-scope-assessment.md)
