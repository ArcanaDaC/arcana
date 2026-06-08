# RB-ANALYSIS-025: Script Execution Analysis

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |
| Runbook ID | RB-ANALYSIS-025 | 2026-06-04 |
| Runbook Name | Script Execution Analysis | 2026-06-04 |


## 1. Prerequisites

Before starting this runbook, ensure the following:

- Access to EDR telemetry
- Access to SIEM telemetry
- Script execution logs available
- PowerShell logging enabled where applicable
- Endpoint hostname identified
- User context identified
- Incident ticket created


## 2. Step-by-Step Instructions

1. **Identify Script Execution Activity**

Determine whether execution involved:

- PowerShell
- Python
- Batch files
- VBScript
- JavaScript
- HTA files
- Windows Script Host
- Bash
- Shell scripts
- Other interpreted code

Document:

- Script type
- Execution method
- Execution timestamp
- User context


2. **Collect Script Artefacts**

Gather:

- Script file
- Script path
- Command line
- Parent process
- Child processes
- Execution logs
- Associated files

Preserve artefacts before modification or removal.


3. **Determine Script Origin**

Identify source of execution:

- User-created script
- Downloaded script
- Email attachment
- Browser download
- Network share
- Cloud storage
- Administrative tooling
- Software deployment system

Document origin and acquisition method.


4. **Review Script Contents**

Analyse for:

- File creation
- Registry modification
- Scheduled task creation
- Service creation
- Credential access
- Network communications
- Download functionality
- Process creation

Review for suspicious or malicious behaviour.


5. **Assess Obfuscation**

Review for:

- Base64 encoding
- String concatenation
- Variable substitution
- Compression
- Encryption
- Reflection
- Dynamic code generation

If obfuscation exists:

- Decode safely
- Preserve decoded content
- Document findings


6. **Review Network Activity**

Identify:

- Download activity
- Upload activity
- External connections
- Cloud storage access
- Command-and-control communication

Correlate network activity with script execution.


7. **Assess Execution Intent**

Determine whether script was used for:

- Administration
- Automation
- Malware delivery
- Persistence
- Credential theft
- Discovery
- Data staging
- Data exfiltration
- Lateral movement

Document rationale.


8. **Identify Additional Activity**

Review:

- Related scripts
- Similar executions
- Same user activity
- Same endpoint activity
- Associated persistence mechanisms

Expand investigation scope where required.


9. **Escalate if Required**

If evidence supports another incident type:

Activate:

- PB-003 Endpoint Malware
- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

Continue executing current playbook concurrently.


10. **Update Incident Record**

Record:

- Script type
- Script origin
- Script functionality
- Decoded content
- Associated activity
- Escalation decisions

Attach supporting evidence.


## 3. Post-Action

Upon completion:

- Ensure script artefacts are preserved
- Ensure decoded content is documented
- Ensure execution source is identified
- Ensure escalation decisions are recorded
- Ensure incident ticket is updated
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
