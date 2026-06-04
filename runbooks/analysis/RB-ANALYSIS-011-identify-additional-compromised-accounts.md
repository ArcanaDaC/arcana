# RB-ANALYSIS-011: Identify Additional Compromised Accounts

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Identify Additional Compromised Accounts| |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Authentication telemetry
- Session telemetry
- Identity provider logs
- Endpoint telemetry
- Device inventory data
- VPN telemetry
- Identity provider access
- SIEM platform access
- EDR platform access
- Threat intelligence platform access
- UEBA platform access

## 2. Step-by-Step Instructions

1. Identify Shared Indicators
   - Review:
      - Shared source IPs
      - Shared devices
      - Shared browser fingerprints
      - Shared session tokens
      - Shared geolocation patterns

2. Hunt for Similar Authentication Behaviour
   - Identify:
      - Similar impossible travel activity
      - Similar MFA anomalies
      - Similar login timing patterns
      - Similar user-agent strings

3. Review Shared Infrastructure Usage
   - Assess:
      - Shared endpoints
      - Shared VPN gateways
      - Shared jump hosts
      - Shared SaaS integrations

4. Identify Administrative Relationship Exposure
   - Determine:
      - Shared privileged access
      - Delegated administration
      - Shared mailbox access
      - Shared API accesss

5. Review OAuth & Token Reuse
   - Identify:
      - Shared OAuth grants
      - Shared refresh tokens
      - Suspicious delegated permissions
      - Cross-account token activity

## 3. Post-Action
- Document all newly identified compromised accounts discovered during the investigation in  the incident ticket
- Record any new IOCs (hashes, IPs, domains, accounts, tokens, signatures) in the incident ticket

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.

