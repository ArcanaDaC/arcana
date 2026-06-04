# RB-CONTAIN-002: Rapid Containment & Network Segmentation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Rapid Containment & Network Segmentation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- EDR alerts
- Impacted host list
- Network telemetry
- Access to EDR platform
- Access to firewall management
- Access to NAC / segmentation platform
- Access to Active Directory
- Access to virtualisation platform

## 2. Step-by-Step Instructions
1. Identify Actively Impacted Systems
    - Determine:
        - Currently encrypting systems
        - Systems communicating with ransomware infrastructure
        - Shared resources impacted

2. Isolate Impacted Hosts
    - Immediately:
        - Isolate hosts via EDR
        - Disconnect from network if EDR unavailable
        - Prevent SMB access

3. Restrict Lateral Movement
    - Temporarily restrict:
        - SMB
        - RDP
        - PsExec
        - WMI
        - WinRM
        - Remote admin shares

4. Segment Impacted Networks
    - Isolate impacted VLANs/subnets
    - Block east-west traffic where feasible
    - Restrict server-to-server communications

5. Protect Critical Infrastructure
    - Prioritise protection for:
        - Domain Controllers
        - Backup infrastructure
        - Hypervisors
        - Identity providers
        - Critical business applications

6. Verify Containment and Segmentation
    - Confirm isolated hosts are no longer communicating externally or laterally
    - Confirm blocked protocols (SMB, RDP, PsExec, WMI, WinRM, remote admin shares) are no longer in use
    - Confirm east-west traffic across segmented VLANs/subnets is blocked
    - Confirm critical infrastructure remains protected and unaffected
    - Confirm no new compromise indicators are observed post-containment
    - If activity persists, expand containment scope and re-verify

## 3. Post-Action
- Document all actions taken in the incident ticket, along with the time each action was taken
## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.