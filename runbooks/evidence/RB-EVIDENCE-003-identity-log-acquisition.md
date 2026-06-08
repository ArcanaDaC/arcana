# RB-EVIDENCE-003: Identity & Authentication Log Acquisition
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Identity & Authentication Log Acquisition | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- Impacted identity (UPN/email, user ID, service principal ID, service account name, or API key ID)
- Incident time window (the period over which activity is to be reviewed)
- Authorisation to query identity and SaaS / application logs for the impacted identity
- Access to the systems carrying the identity's auth and activity logs, which may include:
    - The identity provider (IdP) used to manage the identity if federated (e.g. Microsoft Entra ID, Okta, Google Workspace, Ping, Auth0, AWS IAM Identity Center)
    - The SaaS / cloud platforms the identity has access to (e.g. Microsoft 365, Google Workspace, Salesforce, Slack, GitHub, AWS, Azure, GCP)
    - The SaaS / application platform that the account belongs to, if it's a local account not tied to SSO (e.g. a standalone Salesforce account, personal GitHub account)
    - The VPN / network appliance the account authenticates through, where applicable (e.g. VPN concentrator, RADIUS server, bastion host)
    - On-premises Active Directory and its audit logs where the identity is AD-managed
    - The SIEM / central log platform if identity or auth logs are forwarded there

**Required Tools:**
- IdP administrative console and/or API (e.g. Microsoft Graph, Okta API, Google Admin SDK, AWS CLI/IAM Identity Center API)
- SaaS / application admin console and/or audit log API for each platform in scope
- Network / VPN / bastion appliance admin interface (where applicable)
- SIEM query interface

## 2. Step-by-Step Instructions
> Common Failure Modes
> - Pulling only IdP sign-in logs and missing downstream SaaS audit logs (where the actual attacker actions occurred)
> - Assuming an IdP carries the auth log when the account is local to the SaaS / application (no SSO)
> - Forgetting non-human identities (service principals, service accounts, workload identities, API keys)
> - Missing logs that have already aged out of the platform's short retention window (e.g. Entra ID sign-in logs default 30 days)
> - Failing to scope cross-tenant or federated activity (B2B guest access, federated identity, SSO downstream apps)
> - Querying only successful authentications and missing failed-auth volume patterns that confirm brute force, password spray, or credential stuffing
> - Allowing the suspect identity to alter or delete logs by not snapshotting first when admin compromise is suspected

1. Validate Need and Scope of Log Acquisition
    - Confirm the identity is in scope for the incident and define the time window of interest
    - Identify whether the identity is human or non-human (service principal, service account, workload identity, API key, OAuth app), as this dictates which log categories apply
    - Identify the **authentication path** for the impacted account, as this dictates *where the auth log lives*:
        - **Federated / SSO (IdP-fronted)** — the IdP carries the auth log; the downstream SaaS carries activity logs
        - **Local SaaS / application account (no SSO)** — the SaaS / application platform carries both auth and activity logs
        - **Network / VPN / RADIUS / bastion account** — the appliance carries the auth log
        - **API / programmatic credential (token, key, secret)** — the platform's API / audit log carries the auth event
    - List all platforms the identity has access to; these are all in scope
    - Where possible, preserve logs centrally first (SIEM, IdP, SaaS audit) to guard against tampering, especially where admin or IdP-level compromise is suspected

2. Collect Relevant Identity Activity Logs
    - Identify which categories of activity are relevant to the incident and collect them from whichever source carries them (IdP, SaaS / application audit, network appliance, SIEM). Common categories and where they typically live:
        - **Authentication / sign-in events** (successful, failed, risk-scored, conditional-access decisions, source IP/ASN/geo, user-agent, device ID, session ID)
            - *If federated (SSO):* IdP sign-in logs (Entra ID Sign-ins, Okta System Log, Google Login Audit, Auth0 logs, AWS CloudTrail `ConsoleLogin`, AWS IAM Identity Center sign-ins)
            - *If local SaaS / application account:* the platform's own auth log (e.g. Salesforce LoginHistory, GitHub `user.login`, Slack `user_login`, WordPress login log, application access log)
            - *If network / VPN / bastion:* appliance auth log (RADIUS, TACACS+, VPN appliance log, bastion session log)
            - *If API / programmatic credential:* platform API audit (CloudTrail, Azure Activity, GCP Audit Logs, GitHub Audit, M365 Unified Audit) — look for the API key / token's principal in the actor field
        - **Brute force / spray / stuffing patterns** (high-volume failed auths against one or many accounts)
            - All paths: the same auth logs as above, but queried for failed-auth volume, rate, source IP diversity, and account diversity rather than single-event success/fail
            - Look for fail-then-success patterns (compromise confirmation), low-and-slow patterns, and geo/ASN concentration
        - **MFA events** (factor used, factor challenged/denied, factor enrolment, factor removal, MFA fatigue patterns)
            - *If federated:* IdP MFA logs (Entra ID Authentication Methods + Sign-ins, Okta System Log MFA events, Google 2SV logs)
            - *If local SaaS / application account:* the platform's own MFA log (e.g. GitHub 2FA events, AWS MFA events in CloudTrail, per-app TOTP/U2F logs)
            - *If account has no MFA enabled:* record this as a finding — the absence of MFA is itself key evidence and a recovery-time hardening requirement
        - **Session and token events** (token issuance, refresh, revocation, sign-out, suspicious token reuse)
            - *If federated:* IdP token logs (Entra ID token issuance via Sign-ins, Okta token events, Google OAuth token logs)
            - *If local SaaS / application account:* the platform's session log (session creation / expiry / revocation events in app audit logs)
            - *If API / programmatic credential:* token issuance / refresh events in the platform's audit log
        - **OAuth / consent / application access** (consent grants, admin consent, application access, service principal sign-ins, app role assignments)
            - *If federated:* IdP consent logs (Entra ID Audit + Sign-ins for service principals, Okta OAuth events, Google OAuth Token audit)
            - *If local SaaS / application account:* per-app access logs where the SaaS records third-party app activity (e.g. GitHub OAuth app authorizations, Slack app installs)
        - **Directory / identity management events** (account create / delete / disable, password reset, role assignment, group membership change, privileged role activation, federation / trust changes, sync account activity)
            - *If federated:* IdP audit logs (Entra ID Audit, Okta System Log, Google Admin Audit, AWS IAM CloudTrail)
            - *If local SaaS / application account:* the platform's admin / audit log (e.g. GitHub audit log for org/repo permission changes, Salesforce Setup Audit Trail, Slack audit logs API for admin actions)
            - *If on-premises Active Directory:* Security log (4720/4722/4723/4724/4725/4726/4728/4732/4738/4756), Directory Service log
        - **SaaS / application activity** (actions taken by the identity inside the platform — file access, sharing, configuration changes, data exports, admin actions)
            - The platform's audit log (M365 Unified Audit Log, Google Workspace Drive/Admin Audit, Salesforce Setup Audit Trail, Slack Audit Logs API, GitHub Audit Log, AWS CloudTrail data events)
        - **Mailbox-specific events** (inbox rule changes, forwarding rule changes, delegate access, mailbox permission changes, message send / read from new sources)
            - Email platform audit (M365 Exchange Audit / Unified Audit Log, Google Workspace Gmail audit)
        - **Conditional access / policy decisions** (policy applied, policy result, MFA required, block, session control applied)
            - *If federated:* IdP conditional access logs (Entra ID Sign-ins conditional access details, Okta policy evaluation events)
            - *If local SaaS / application account:* platform-side access policy logs where available (e.g. IP allow-list deny events)
        - **Risk and detection signals raised by the IdP / platform identity protection** (risky user, risky sign-in, leaked credentials, anomalous travel, anomalous token use)
            - *If federated:* IdP identity protection (Entra ID Identity Protection, Okta ThreatInsight, Google Security Center)
            - *If local SaaS / application account:* platform-native security signals (e.g. GitHub leaked-secret alerts, Salesforce Real-Time Event Monitoring threat events)
    - For each relevant category, prefer querying or exporting from your SIEM / IdP / platform admin console where the data is centralised; query directly via API for categories not centralised
    - Record the query, time range, and access location for each category collected

3. Collect Centralised Logs from the SIEM
    - Export matching events from the SIEM or central log platform for the impacted identity over the incident window
    - Include any enriched or correlated identity alerts for the impacted identity
    - Record the query, time range, and export location

4. Scope to Adjacent Identities and Shared Indicators
    - Identify shared indicators from the impacted identity's activity (source IPs, ASNs, user-agents, device IDs, OAuth application IDs, MFA factor metadata, session/correlation IDs)
    - Re-run the relevant queries across the IdP and SaaS / application audit logs using these indicators to surface adjacent compromised identities
    - Record findings and feed back into the incident scope

## 3. Post-Action
- Where logs are exported as files, transfer to the designated evidence storage location via a secure path; verify SHA-256 hashes match before and after transfer
- Record acquisition metadata: operator, timestamp, identity, sources collected, time range, tools / queries used, and (for exported files) the SHA-256 hash of the resulting archive
- Confirm chain of custody is recorded end-to-end where files were exported (collection → transfer → storage)
- Hand off to the analyst responsible for log review and update the incident ticket with the evidence reference

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
