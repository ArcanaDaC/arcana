# RB-CONTAIN-003: Active Directory Containment

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Active Directory Containment | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

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

> Common Failure Modes
> - Leaving privileged sessions active
> - Failing to rotate service account credentials
> - Ignoring shadow admin persistence
> - Restoring systems before AD validation

1. Review Privileged Account Activity
	- Identify:
		- Domain Admin usage
		- Enterprise Admin activity
		- Service account anomalies
		- Newly created privileged accounts

2. Disable Suspected Compromised Accounts
	- Immediately:
		- Disable compromised privileged accounts
		- Rotate privileged credentials
		- Reset KRBTGT if required

3. Identify Persistence Mechanisms
	- Review for:
		- Scheduled tasks
		- Startup scripts
		- GPO modifications
		- Malicious services
		- Shadow admin accounts

4. Protect Domain Controllers
	- Restrict administrative access
	- Isolate DCs if required
	- Review replication anomalies
	- Monitor authentication spikes

5. Validate Identity Infrastructure Integrity
	- Confirm:
		- GPO integrity
		- Replication health
		- Authentication stability
		- Administrative group integrity


## 3. Post-Action
- Document all containment steps taken in the incident ticket, along with the time each action was taken
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
