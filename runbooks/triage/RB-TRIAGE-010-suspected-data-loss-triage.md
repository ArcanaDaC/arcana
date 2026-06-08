# RB-TRIAGE-010: Suspected Data Loss Triage
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Suspected Data Loss Triage | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- DLP alert or user report of suspected data loss
- Endpoint telemetry (file access, file write, process execution)
- Network / proxy / CASB telemetry (outbound transfers, web uploads, cloud storage activity)
- Email gateway logs (attachments sent, recipients)
- SaaS / cloud storage audit logs (file share, download, external link creation)
- User and asset information for the actor involved

**Required Tools:**
- DLP platform
- EDR platform
- SIEM
- Email gateway
- CASB / proxy
- SaaS / cloud storage admin console
- Asset and identity inventory

## 2. Step-by-Step Instructions
>Common Failure Modes
>- Closing the alert as false positive without confirming the actor is the genuine user
>- Treating "blocked by DLP" as the end of the investigation when other channels may still be in use
>- Reviewing only the alerting transfer and missing related transfers in the same window
>- Failing to classify the data before assigning severity

1. Validate Alert Authenticity
	- Determine:
		- Trigger source (DLP rule, user report, third-party notification, SIEM correlation)
		- Trigger reason (rule matched, file pattern, destination, volume, user-reported observation)
		- Whether the transfer was blocked, allowed, or monitor-only
		- Whether the alert has known false-positive history for this rule / user / channel

2. Identify the Actor and Asset
	- Collect:
		- Username and email of the actor
		- Hostname, IP, and OS of the originating device
		- Logged-in user at the time of the event
		- Account type (employee, contractor, service account, shared mailbox)
		- Device managed / unmanaged status
		- Privilege level and group memberships

3. Identify the Transfer Path
	- Determine:
		- Channel used (e.g. web upload, email attachment, cloud storage sync, USB / removable media, IM / chat upload, code-repo push, print, screenshot)
		- Destination (domain, recipient address, cloud tenant, removable device ID, repo URL)
		- Whether the destination is sanctioned, unsanctioned, or unknown
		- Whether the destination is internal, external, or personal (e.g. personal email, personal cloud drive)

4. Identify the Data
	- Determine:
		- File names, file types, and file paths
		- File size and file count
		- Data classification (public, internal, confidential, regulated)
		- Whether the data contains PII, PCI, PHI, source code, customer data, credentials, or other regulated/sensitive content
		- Source of the data (which system, database, or repository it originated from)

5. Determine Whether the Activity Is Human or Automated
	- Determine:
		- Process and command line that initiated the transfer
		- Parent process (browser, mail client, sync agent, script, unknown binary)
		- Whether the action was performed interactively by the user or by automation / malware
		- Whether the actor was authenticated and active on the device at the time
	- Where a user is identified, contact them out-of-band to confirm whether the activity is legitimate

6. Assess Scope
	- Review:
		- Other transfers by the same actor in the incident window (same destination, same data, other channels)
		- Other actors transferring the same data or to the same destination
		- Other DLP alerts on the same rule / channel / destination across the environment
		- Sign-in and session activity for the actor for signs of account compromise

7. Determine Severity and Next Playbook
	- Assess:
		- Sensitivity and volume of data involved
		- Whether the transfer was blocked or completed
		- Whether the actor is the genuine user, a compromised account, or malware
		- Whether the destination is attacker-controlled, personal, or sanctioned-but-misused


## 3. Post-Action
- Ensure trigger source, actor, transfer path, data classification, scope findings, and verdict are documented in the incident ticket

## Contributor

**Jayden Vo**  
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
