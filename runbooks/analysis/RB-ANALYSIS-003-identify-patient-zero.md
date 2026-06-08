# RB-ANALYSIS-003: Identify Patient Zero

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Identify Patient Zero | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- Log Access
	- EDR telemetry access
	- Authentication logs access (IdP, SSO, Active Directory, Entra ID, Okta, etc.)
	- Active Directory / directory service logs access
	- Email gateway / mail flow telemetry access
	- VPN logs access
	- Cloud audit logs access (e.g. AWS CloudTrail, Azure Activity Logs, GCP Audit Logs)
	- SaaS application logs access (e.g. Microsoft 365, Google Workspace, Salesforce, GitHub, Okta)
	- Network / proxy / DNS / firewall logs
- SIEM timeline data
- Endpoint timeline data (file, process, registry, autorun events)
- SIEM platform access
- EDR platform access
- Asset and user directory data (to correlate hostnames, accounts, and owners)

## 2. Step-by-Step Instructions

1. **Build Initial Timeline**
	- Identify the earliest confirmed indicator of compromise (alert, user report, log anomaly, externally reported indicator)
	- Identify the first suspicious execution, action, or transaction observed
	- Flag first suspicious authentication event
	- Anchor the timeline to a known-good reference point prior to the first suspicious event

2. **Identify Earliest Impacted Host, Account, or Entity**
	- Use known IOCs (hashes, IPs, domains, accounts, signatures) from step 1 as search terms to pivot into alerts and telemetry
	- Check whether alerts fired (EDR, SIEM, IDS, DLP, cloud security tooling):
		- **If alerts exist** - identify the earliest across all entity types (host, account, cloud tenant, SaaS app, mailbox, repository, API key/token); treat it as a starting point, not a conclusion
		- **If no alerts fired** - pivot to raw telemetry using known IOCs: review auth logs for first unusual login; access logs for first unusual resource access; DNS/proxy logs for first suspicious outbound connection; cloud/SaaS audit logs for first unusual API call, permission grant, or data export; EDR telemetry for first suspicious execution or persistence artefact
	- **Note**: earliest alert ≠ earliest activity - always look back further in raw telemetry to confirm nothing pre-dates it
	- Document user reports
	- Record the earliest confirmed timestamp of suspicious activity and the entity it is associated with

3. **Review Initial Access Indicators**
	- Check for phishing activity
	- Investigate VPN compromise indicators
	- Assess exposed remote-access services (RDP, SSH, VPN, jump hosts, management interfaces)
	- Review credential theft indicators
	- Identify malicious payload delivery (drive-by, download, attachment, supply chain, third-party software)
	- Check for vulnerability exploitation (recently disclosed CVEs, web app exploitation, public-facing service abuse)
	- Check for valid-account abuse (purchased credentials, leaked tokens, OAuth consent abuse, session hijack)
	- Check for trusted-relationship abuse (third party, contractor, managed service provider, supply chain)
	- Check for physical / insider vectors (lost device, USB, insider misuse) where applicable

4. **Analyse User Activity**
	- Review privileged account usage
	- Identify unusual login locations, devices, or impossible travel
	- Document non-human identity activity (service accounts, machine identities, API keys, OAuth apps)
	- Flag MFA, conditional access, and session anomalies (prompt bombing, token theft, consent grants)
	- Identify activity from accounts that are dormant, recently created, or recently re-enabled

5. **Identify How Lateral Movement Occurred**
	- Determine lateral movement techniques
	- Track shared credential usage
	- Identify administrative tooling, RMM, and dual-use tooling abused for movement
	- Document remote execution methods
	- Identify identity-driven propagation (token reuse, federation abuse, role assumption, cross-tenant access)
	- Identify cloud / SaaS propagation (cross-account, cross-tenant, app-to-app)
	- Determine how the compromise spread from the initial entity to others

6. **Validate the Candidate Patient Zero**
	- Confirm no earlier indicator exists for that host, identity, or entity
	- Confirm the initial access vector is consistent with the proposed timeline
	- Confirm the spread from the identified patient zero is consistent with observed compromise across other entities
	- If any of the above fail, the candidate is not patient zero - return to 1.

## 3. Post-Action
- Record timeline and initial access vector in the incident ticket
- Document all newly identified compromised accounts, hosts, and entities discovered during the investigation
- Record any new IOCs (hashes, IPs, domains, accounts, tokens, signatures) in the incident ticket

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.