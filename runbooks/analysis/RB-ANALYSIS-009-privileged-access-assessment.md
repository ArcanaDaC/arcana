# RB-ANALYSIS-009: Privileged Access Assessment

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Privileged Access Assessment | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Authentication logs
- Administrative activity logs
- Role assignment telemetry
- Endpoint telemetry
- Session activity logs
- Identity provider access
- SIEM platform access
- PAM platform access
- EDR platform access
- Cloud audit logs access

## 2. Step-by-Step Instructions
1. Identify Privileged Access Exposure
   - Determine:
      - Administrative roles assigned
      - Active privileged sessions
      - Privileged application access
      - Shared administrative accounts
   - Common Failure Modes:
      - Failing to review inherited privilege
      - Ignoring service account exposure
2. Review Administrative Activity
   - Assess:
      - Role assignment changes
      - Policy modifications
      - Access control changes
      - Security configuration changes
      - Administrative API activity
3. Identify Privilege Escalation Indicators
   - Look for:
      - New privileged accounts
      - Group membership changes
      - Conditional access modifications
      - MFA policy changes
      - Service principal abuse
4. Review Lateral Movement Activity
   - Identify:
      - Remote administrative access
      - Cross-system authentication
      - Privileged session hopping
      - Administrative tool usage

## 3. Post-Action
- Document all findings within the incident ticket


## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
