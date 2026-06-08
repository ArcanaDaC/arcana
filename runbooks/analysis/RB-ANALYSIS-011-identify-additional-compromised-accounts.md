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
- Investigation involving a known compromised identity (human user, service account, workload identity, API key, OAuth app)
- Indicators captured from the known compromise: source IPs / ASNs, user-agents, device IDs, session/token IDs, OAuth grants
- The incident time window (extend backward by at least 7 days to capture pre-incident activity)
- Access to authentication and session telemetry from any platform the identity uses:
  - Identity providers (IdP / SSO)
  - SaaS / application platforms (for local accounts and workload activity)
  - Cloud provider control plane (CloudTrail / Azure Activity / GCP Admin Activity / OCI Audit) — for workload identity, instance role, and service account activity
  - VPN / RADIUS / TACACS+ / bastion logs (where applicable)
- Access to endpoint telemetry (EDR) where on-prem hosts are in scope
- Access to SIEM with all of the above indexed

## 2. Step-by-Step Instructions

1. **Search for the Same Indicators Across All Identities**
   For each indicator captured from the known compromise, search every authentication / activity log in scope for the same value:
   - Source IPs / ASNs / geolocation
   - User-agent strings
   - Device IDs / browser fingerprints
   - Session, refresh, or access tokens
   - OAuth client IDs / API key IDs
   Match against: human users in the IdP, local accounts on SaaS / applications, workload identities (instance roles, service accounts, managed identities), and API keys.

2. **Hunt for Similar Authentication / Authorisation Behaviour**
   Search for other identities exhibiting the same patterns as the known compromise:
   - Impossible travel, unusual geo / ASN, or unusual device
   - MFA fatigue, MFA bypass, or unauthorised MFA enrolment
   - Login timing patterns (off-hours, burst patterns)
   - Failed-then-success authentication sequences
   - Anomalous workload identity API call patterns (new region, new user agent, new target services)

3. **Review Shared Infrastructure and Trust Relationships**
   For each identity uncovered so far, check whether it shares:
   - On-prem: endpoints, VPN gateways, jump / bastion hosts, shared mailboxes
   - Cloud: instance roles, federation trusts, cross-account / cross-tenant access, workload identity federation, shared service accounts
   - SaaS: shared integrations, shared OAuth apps, shared API keys

4. **Identify Administrative Relationship Exposure**
   Determine where the known compromise has access to other identities through:
   - Shared privileged groups or role assignments (on-prem AD, cloud IAM, SaaS admin roles)
   - Delegated administration (on-prem OUs, Entra ID role groups, AWS Organisations, GCP folders, OCI compartments)
   - Shared mailbox / delegate access
   - Shared API keys, service principal credentials, or workload identity scopes

5. **Review OAuth, Token, and Credential Reuse**
   Search for:
   - Shared OAuth grants and admin-consented applications
   - Shared refresh / access / session tokens
   - Suspicious delegated permissions (mailbox, file, admin)
   - Cross-account / cross-tenant token activity (AssumeRole, federated access, B2B sign-ins)
   - API keys or service principal secrets observed in use across multiple identities or sources

## 3. Post-Action
- Document all newly identified compromised accounts discovered during the investigation in  the incident ticket
- Record any new IOCs (hashes, IPs, domains, accounts, tokens, signatures) in the incident ticket

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.

