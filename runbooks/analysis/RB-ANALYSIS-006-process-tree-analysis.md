# RB-ANALYSIS-006: Process Tree Analysis

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Process Tree Analysis | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- EDR telemetry access
- Process creation logs
- Command-line arguments data
- File execution telemetry
- User activity logs
- EDR platform access
- SIEM platform access
- Process analysis tools

## 2. Step-by-Step Instructions

1. **Identify Initial Execution Process**
    - Determine:
        - Initial executable
        - Launch source
        - User context
        - Execution timestamp

2. **Review Parent-Child Relationships**
    - Identify:
        - Suspicious ancestry
        - Office application spawning scripts
        - LOLBin usage
        - Script interpreter execution

3. **Analyse Command-Line Arguments**
    - Review for:
        - Encoded commands
        - PowerShell abuse
        - Download cradles
        - Obfuscation
        - Suspicious parameters

4. **Identify Secondary Payload Execution**
    - Look for:
        - Additional binaries
        - Script downloads
        - DLL execution
        - Injection behaviour

5. **Review Network Activity**
    - Identify:
        - External connections
        - C2 behaviour
        - DNS activity
        - Beaconing intervals

6. **Correlate with User Activity**
    - Determine:
        - Was execution user initiated?
        - Was phishing involved?
        - Was remote execution involved?

## 3. Post-Action
- Ensure all analysis steps and findings are fully documented in the incident ticket

---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
