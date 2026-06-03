# RB-002.4 Ransomware Payload Analysis

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Ransomware Payload Analysis | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Ransomware binary/sample
- File hashes
- EDR telemetry
- Sandbox results
- Memory captures
- Ransom notes
- Access to sandbox environment
- Access to reverse engineering tools
- Access to EDR platform
- Access to threat intelligence platforms
- Access to memory analysis tools

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current encryption status
   - Document affected file extensions

5. **Preserve Evidence (if applicable)**
   - Preserve ransomware samples
   - Preserve memory captures
   - Preserve ransom notes

6. **Execute Task Steps**
   - **6.1 Identify Ransomware Family**
     - Determine known ransomware family
     - Determine variant/version
     - Identify associated threat actor
     - Locate public reporting references

   - **6.2 Analyse Encryption Behaviour**
     - Review file extensions targeted
     - Review encryption speed
     - Review file targeting behaviour
     - Review network share interaction
     - Review hypervisor targeting

   - **6.3 Review Persistence Mechanisms**
     - Identify scheduled tasks
     - Identify services
     - Identify registry modifications
     - Identify startup mechanisms
     - Identify GPO abuse

   - **6.4 Assess Lateral Movement Capability**
     - Determine use of PsExec
     - Determine use of WMI
     - Determine use of RDP
     - Determine use of SMB propagation
     - Determine use of credential dumping

   - **6.5 Identify Exfiltration Behaviour**
     - Look for archive creation
     - Look for compression activity
     - Look for data staging
     - Look for outbound transfers
     - Look for cloud storage abuse

   - **6.6 Collect Indicators**
     - Document file hashes
     - Document domains/IPs
     - Document mutexes
     - Document file paths
     - Document registry keys
     - Document services

7. **Verify Task Completion**
   - Confirm ransomware family identification
   - Verify behaviour analysis summary
   - Validate persistence findings
   - Verify IOC list created
   - Verify TTP mapping inputs documented

8. **Update Incident Documentation**
   - Record analysis findings
   - Document IOCs identified
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if data exfiltration identified
   - Escalate if worming behaviour observed
   - Escalate if hypervisor targeting identified

10. **Hand Off or Notify Next Responsible Party**
    - Notify threat intelligence team
    - Provide IOC list

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Data exfiltration identified | Escalate to PB-005 |
| Worming behaviour observed | Expand containment |
| Hypervisor targeting identified | Prioritise infrastructure isolation |

---

## Output

- Ransomware family identification
- Behaviour analysis summary
- Persistence findings
- IOC list
- TTP mapping inputs

---

## Common Failure Modes

- Analysing samples outside isolated environments
- Ignoring persistence mechanisms
- Missing staged exfiltration activity

---

## Automation Hooks

- Auto-hash enrichment
- Auto-sandbox submission
- Auto-IOC extraction
- Auto-TTP mapping

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Previous: [RB-002.3 Encryption Scope Assessment](./RB-002.3-encryption-scope-assessment.md)
- Next: [RB-002.5 Backup Integrity Validation](./RB-002.5-backup-integrity-validation.md)
