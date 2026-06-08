# RB-ANALYSIS-004: Ransomware Encryption Scope Assessment

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Ransomware Encryption Scope Assessment | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- User reports 
- EDR platform access (telemetry and alerts)
- SIEM platform access (alerts and log search)
- File server and network share logs
- File integrity monitoring access
- Backup platform access
- Asset inventory access

## 2. Step-by-Step Instructions
1. **Identify Impacted Systems**
	- Determine endpoints impacted
	- Identify servers impacted
	- Identify hypervisors impacted
	- Identify cloud resources impacted

2. **Identify Encrypted Data**
	- Assess:
		- File shares
		- Databases
		- User directories
		- Critical applications
		- SaaS platforms

3. **Assess Business Impact**
	- Determine business units impacted
	- Identify critical services unavailable
	- Assess operational disruption severity

4. **Review Encryption Patterns**
	- Identify file extensions used
	- Review ransom note patterns
	- Determine encryption speed
	- Assess selective targeting behaviour

5. **Identify Backup Exposure**
	- Determine if backups were encrypted
	- Identify backup deletion activity
	- Assess immutable storage impact

6. **Build Impact Inventory**
	- Document impacted systems
	- Prioritize recovery sequence
	- Estimate restoration effort for each asset

## 3. Post-Action
- Document all findings in the incident ticket
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.