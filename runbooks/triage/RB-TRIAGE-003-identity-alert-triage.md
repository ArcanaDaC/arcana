# RB-TRIAGE-003: Identity Alert Triage
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Identity Alert Triage | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Identity provider alerts
- Authentication telemetry
- MFA telemetry
- User reports
- VPN telemetry
- Session activity logs

**Required Tools:**
- Identity provider
- SIEM
- MFA platform
- VPN telemetry
- Threat intelligence platform

## 2. Step-by-Step Instructions
>Common Failure Modes
>- Treating impossible travel as definitive compromise
>- Ignoring successful MFA activity
>- Missing shared infrastructure indicators

1. Validate Alert Authenticit
	- Determine:
		- Alert source
		- Detection type
		- Alert confidence
		- Triggering conditions

	- Review:
		- Alert metadata
		- Authentication anomalies
		- Associated indicators

2. Identify Impacted Identity

	- Collect:
		- Username
		- Email address
		- Privilege level
		- Group memberships
		- Administrative roles
		- Device associations

3. Review Authentication Activity

	- Review:
		- Login timestamps
		- Source IPs
		- Geolocation
		- Device fingerprints
		- MFA outcomes

4. Assess Active Risk

	- Determine:
		- Is attacker activity ongoing?
		- Are active sessions present?
		- Is privilege escalation suspected?
		- Is lateral movement suspected?

5. Assess Scope
	- Identify:
		- Additional impacted accounts
		- Shared devices
		- Shared IPs
		- Similar authentication patterns


## 3. Post-Action
- Ensure all alert validation findings and containment recommendations are documented in the incident ticket

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.