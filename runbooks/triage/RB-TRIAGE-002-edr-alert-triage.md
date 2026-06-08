# RB-TRIAGE-002: EDR Alert Triage
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | EDR Alert Triage | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- EDR alerts
- Endpoint telemetry
- Process execution data
- File hashes
- User and host information
- Threat intelligence enrichment

**Required Tools:**
- EDR platform
- SIEM
- Threat intelligence platform
- Asset inventory
- Authentication telemetry

## 2. Step-by-Step Instructions
>Common Failure Modes
>- Treating behavioural detections as false positives too early
>- Ignoring blocked malware activity
>- Failing to assess broader scope

1. Validate Alert Authenticity
    - Determine:
        - Alert source
        - Detection type
        - Confidence level
        - Whether detection is prevention or detection only

    Review:
        - Detection signatures
        - Behavioural indicators
        - Alert metadata

2. Identify Impacted Endpoint
    - Collect:
        - Hostname
        - IP address
        - Logged-in user
        - Device criticality
        - Operating system
        - Business owner

3. Review Malware Indicators
    - Identify:
        - File hashes
        - Process names
        - Command-line arguments
        - Parent-child process chains
        - Network connections

4. Assess Execution Status
    - Determine:
        - Was malware blocked?
        - Was execution successful?
        - Is malware still active?
        - Did persistence occur?

5. Assess Potential Scope

    - Review:
        - Similar detections across environment
        - Same hash/process activity
        - Shared user activity
        - Shared infrastructure usage

6. Determine Severity
    - Assess:
        - Malware capability
        - Credential theft potential
        - Lateral movement indicators
        - Persistence mechanisms
        - Critical system involvement

## 3. Post-Action
- Ensure all analysed headers, extracted IOCs, and initial verdict are documented in the incident ticket

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
