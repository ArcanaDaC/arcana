# RB-POST-001: Ransomware-Post-Incident Hardening

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Ransomware-Post-Incident Hardening | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- PIR findings
- Detection gaps
- TTP mapping report
- Recovery lessons learned
- Executive recommendations
- Access to SIEM
- Access to EDR platform
- Access to vulnerability management platform
- Access to identity management platform
- Access to network security tooling

## 2. Step-by-Step Instructions
1. Review Root Cause & Control Failures
	- Identify:
		- Initial access failures
		- Detection failures
		- Containment weaknesses
		- Recovery bottlenecks

2. Improve Detection Coverage
	- Implement:
		- New detection logic
		- Enhanced telemetry collection
		- Improved alert tuning
		- Additional hunt content

3. Harden Identity Infrastructure
	- Review:
		- Privileged access
		- MFA coverage
		- Service accounts
		- Administrative segmentation

4. Improve Network Segmentation
	- Enhance:
		- East-west restrictions
		- Administrative isolation
		- Backup network isolation
		- Critical infrastructure separation

5. Strengthen Backup Security
	- Implement:
		- Immutable backups
		- Offline recovery capability
		- Backup monitoring
		- Backup access restrictions

6. Conduct Lessons Learned Review
	- Document:
		- What worked well
		- What failed
		- Process improvements
		- Tooling improvements

## 3. Post-Action
- Ensure that improvements made are documented and tracked
- Recording findings from the Lessons Learned Review into the PIR document

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.