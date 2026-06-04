# RB-ANALYSIS-023 Command-Line Analysis

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Runbook ID | RB-ANALYSIS-023 | 2026-06-04 |
| Runbook Name | Command-Line Analysis | 2026-06-04 |
| Owner | Arcana Framework | 2026-06-04 |
| Version | 1.0 | 2026-06-04 |
| Status | Live | 2026-06-04 |

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

### Step 1 – Identify Suspicious Process Execution

Collect:

- Process name
- Process path
- Parent process
- Child processes
- User context
- Execution timestamp

Determine:

- Whether execution aligns with alert telemetry
- Whether execution is still occurring

---

### Step 2 – Obtain Full Command Line

Collect:

- Full command line
- Parent command line
- Child command lines
- Execution path
- Working directory

Review for:

- Truncation
- Missing arguments
- Alternate execution paths

---

### Step 3 – Analyse Command-Line Arguments

Review for:

- Encoded content
- Download operations
- Remote resource retrieval
- File execution
- Process spawning
- Credential access
- Registry modification
- Persistence creation

Identify:

- Suspicious switches
- Unusual argument combinations
- Hidden execution flags

---

### Step 4 – Decode Obfuscated Content

Review for:

- Base64 encoding
- Hex encoding
- String concatenation
- Variable substitution
- Multi-stage execution

If encoded content exists:

- Decode safely
- Preserve decoded output
- Document findings

---

### Step 5 – Identify Common Adversary Techniques

Review for:

- PowerShell download cradles
- Invoke-WebRequest usage
- Bitsadmin activity
- Certutil abuse
- Rundll32 execution
- Regsvr32 execution
- Mshta execution
- Wscript/Cscript execution

Map activity to known ATT&CK techniques where applicable.

---

### Step 6 – Assess Execution Intent

Determine whether command line indicates:

- Malware execution
- Persistence establishment
- Credential theft
- Lateral movement
- Data staging
- Data exfiltration
- Reconnaissance
- Legitimate administration

Document rationale.

---

### Step 7 – Correlate Additional Activity

Review:

- Authentication activity
- Network activity
- File access activity
- Registry modifications
- Scheduled task creation
- Service creation

Determine whether execution was isolated or part of broader activity.

---

### Step 8 – Escalate if Required

If evidence supports another incident type:

Activate:

- PB-003 Endpoint Malware
- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

Continue executing current playbook concurrently.

---

### Step 9 – Document Findings

Record:

- Full command line
- Decoded content
- Analysis findings
- ATT&CK mappings
- Associated activity
- Escalation decisions

Attach supporting evidence.

---

### Step 10 – Update Incident Record

Update:

- Investigation notes
- Scope assessment
- Risk assessment
- Containment recommendations
- Next investigative actions

Notify Incident Lead if escalation required.

---

# 3. Post-Action

Upon completion:

- Ensure all command-line evidence has been preserved
- Ensure decoded content is documented
- Ensure escalation decisions are recorded
- Ensure related playbooks are activated if required
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
