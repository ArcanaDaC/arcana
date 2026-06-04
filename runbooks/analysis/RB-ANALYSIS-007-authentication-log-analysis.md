# RB-ANALYSIS-007: Authentication Log Analysis

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | URL Detonation & Analysis | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Authentication logs access
- MFA logs access
- VPN logs access
- Session telemetry data
- Conditional access logs
- Identity provider access
- SIEM platform access
- MFA platform access
- Threat intelligence platform access

## 2. Step-by-Step Instructions

1. **Build Authentication Timeline**
   - Identify
      - Earliest suspicious login
      - Successful authentications
      - Failed login attempts
      - MFA activity
      - Session creation events

2. **Review Source Infrastructure**
   - Assess:
      - Source IPs
      - ASN/provider
      - Geolocation
      - Is Known malicious infrastructure
      - VPN or anonymisation usage

3. **Analyse Device & Session Context**
   - Review:
      - Device identifiers
      - Browser fingerprints
      - Session duration
      - User-agent strings
      - New device registrations


4. **Review MFA Activity**
   - Identify:
      - MFA fatigue attempts
      - Push bombing
      - MFA bypass
      - Device registration anomalies
      - Failed MFA attempts

5. **Assess Privileged Activity**
   - Review:
      - administrative logins
      - privileged role usage
      - sensitive application access
      - unusual administrative actions

6. **Correlate Additional Activity**
   - Review:
      - Endpoint telemetry
      - VPN access
      - SaaS access
      - Cloud activity
      - Lateral movement indicators

## 3. Post-Action
- Document all investigation findings within the incident ticket

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
