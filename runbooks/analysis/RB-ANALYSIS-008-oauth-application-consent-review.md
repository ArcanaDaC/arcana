# RB-ANALYSIS-008: OAuth & Application Consent Review

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | OAuth & Application Consent Review | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- OAuth audit logs
- Application consent telemetry
- Identity provider logs
- SaaS integration inventory
- Session telemetry data
- Identity provider access
- OAuth administration portal access
- SIEM platform access
- Cloud audit logs access
- Threat intelligence platform access

## 2. Step-by-Step Instructions
1. Enumerate OAuth Applications
- Identify:
   - User-consented applications
   - Admin-consented applications
   - Third-party integrations
   - Newly registered applications

2. Review Granted Permissions
   - Assess:
		- Mail access permissions
		- File access permissions
		- Offline access permissions
		- Administrative scopes
		- API access scopes


3. Identify Suspicious Applications
	- Review:
		- Unknown publishers
		- Recently registered applications
		- Excessive permission requests
		- Suspicious redirect URIs
		- Low-reputation applications


4. Review Token Activity
	- Identify:
		- Long-lived refresh tokens
		- Persistent delegated access
		- API abuse activity
		- Unusual application behaviour

## 3. Post-Action
- Document all findings within the incident ticket

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
