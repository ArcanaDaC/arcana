# RB-ANALYSIS-024 LOLBin Abuse Investigation

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |
| Runbook ID | RB-ANALYSIS-024 | 2026-06-04 |
| Runbook Name | LOLBin Abuse Investigation | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Access to EDR telemetry
- Access to SIEM telemetry
- Process execution logs available
- Command-line logging enabled
- Endpoint hostname identified
- User context identified
- Incident ticket created

---

# 2. Step-by-Step Instructions

### Step 1 – Identify LOLBin Usage

Determine whether execution involved a Living-Off-the-Land Binary (LOLBin).

Common examples include:

- powershell.exe
- cmd.exe
- rundll32.exe
- regsvr32.exe
- mshta.exe
- wmic.exe
- certutil.exe
- bitsadmin.exe
- cscript.exe
- wscript.exe
- installutil.exe
- msbuild.exe
- schtasks.exe
- net.exe
- net1.exe

Document all observed LOLBins.

---

### Step 2 – Collect Execution Context

Collect:

- Full command line
- Parent process
- Child processes
- Execution path
- User context
- Hostname
- Execution timestamp

Review:

- Process ancestry
- Associated activity
- Related alerts

---

### Step 3 – Analyse Parent-Child Relationships

Review:

- Initial execution source
- Office application spawning LOLBins
- Browser spawning LOLBins
- Script interpreter spawning LOLBins
- Service-based execution

Identify suspicious execution chains.

Examples:

- winword.exe → powershell.exe
- outlook.exe → cmd.exe
- chrome.exe → mshta.exe
- excel.exe → rundll32.exe

---

### Step 4 – Review Command-Line Activity

Analyse:

- Download activity
- Remote resource access
- Encoded commands
- Obfuscated content
- DLL loading
- Script execution
- Registry modifications

Review for common attacker tradecraft.

---

### Step 5 – Assess LOLBin Purpose

Determine whether LOLBin was used for:

- Execution
- Persistence
- Credential access
- Discovery
- Lateral movement
- Data staging
- Data exfiltration
- Defence evasion

Document findings.

---

### Step 6 – Review Network Activity

Identify:

- Outbound connections
- Downloaded payloads
- Cloud storage access
- Suspicious domains
- External IP addresses

Correlate network activity with execution events.

---

### Step 7 – Hunt for Additional LOLBin Activity

Search for:

- Similar command lines
- Same LOLBin usage
- Same user activity
- Same parent process
- Same destination infrastructure

Expand investigation scope where required.

---

### Step 8 – Determine Legitimacy

Validate:

- Approved administrative activity
- IT operations usage
- Security tooling activity
- Software deployment activity
- User-authorised execution

Document rationale for determination.

---

### Step 9 – Escalate if Required

If evidence supports another incident type:

Activate:

- PB-003 Endpoint Malware
- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

Continue executing current playbook concurrently.

---

### Step 10 – Update Incident Record

Record:

- LOLBins identified
- Execution chains
- Command-line findings
- Associated activity
- ATT&CK mappings
- Escalation decisions

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure all LOLBin activity has been documented
- Ensure command-line evidence is preserved
- Ensure investigation scope has been assessed
- Ensure escalation decisions are recorded
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
