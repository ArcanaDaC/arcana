# RB-ANALYSIS-010: Credential Exposure Investigation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Credential Exposure Investigation | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- Authentication telemetry
- Identity provider logs
- User reports
- Browser telemetry
- Threat intelligence data
- Endpoint telemetry
- Identity provider access
- SIEM platform access
- EDR platform access
- Threat intelligence platform access
- Password exposure monitoring tools

## 2. Step-by-Step Instructions

1. Identify Initial Exposure Vector
   - Determine whether exposure occurred through:
      - Phishing
      - Malware
      - Credential stuffing
      - Password reuse
      - Browser credential theft
      - Token theft
      - Public credential leaks

2. Review Authentication Timeline
   - Identify:
      - Earliest suspicious login
      - Failed authentication attempts
      - MFA activity
      - Password reset activity
      - Session creation activity

3. Assess Password Reuse Risk
   - Determine:
      - Shared password usage
      - Corporate/personal password overlap
      - Service account reuse
      - Administrative credential reuse

4. Review Endpoint Exposure Indicators

   - Identify:
      - Browser credential dumping
      - Token theft
      - Session cookie theft
      - Password manager compromise
      - Infostealer activity

5. Review External Exposure Sources
   - Check:
      - Credential dump repositories
      - Threat intelligence feeds
      - Dark web monitoring sources
      - Known breach datasets
6. Identify Adjacent Risk
   - Assess:
      - Additional affected accounts
      - Shared devices
      - Shared authentication infrastructure
      - Shared API credentials


## 3. Post-Action
- Document all findings within the incident ticket

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
