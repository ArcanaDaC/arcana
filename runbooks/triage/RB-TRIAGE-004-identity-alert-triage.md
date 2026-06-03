# RB-004.1 Identity Alert Triage
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Identity Alert Triage | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Identity provider alerts
- Authentication telemetry
- MFA telemetry
- User reports
- VPN telemetry
- Session activity logs

**Required Tools:**
- Identity provider
- SIEM
- MFA platform
- VPN telemetry
- Threat intelligence platform

## 2. Step-by-Step Instructions
1. **Confirm Task Assignment** - Verify assignment and review the identity alert details.

2. **Notify Stakeholders** - Inform the incident commander and identity security team.

3. **Access Target System/Resource** - Log in to identity provider, SIEM, and MFA platform to retrieve alert and telemetry data.

4. **Document Current State** - Record identity and authentication metadata:
   - Username and email address
   - Privilege level and administrative roles
   - Group memberships and device associations
   - Alert source, detection type, and confidence level

5. **Preserve Evidence (if applicable)** - Collect and document authentication indicators:
   - Login timestamps and source IPs
   - Geolocation data and device fingerprints
   - MFA outcomes and challenges
   - Session activity logs

6. **Execute Task Steps** - Perform systematic identity alert triage:
   - **6.1 Validate Alert Authenticity:** Determine alert source, detection type, and triggering conditions. Review alert metadata and associated authentication anomalies.
   - **6.2 Identify Impacted Identity:** Collect username, email address, privilege level, group memberships, administrative roles, and device associations.
   - **6.3 Review Authentication Activity:** Review login timestamps, source IPs, geolocation, device fingerprints, and MFA outcomes.
   - **6.4 Assess Active Risk:** Determine whether attacker activity is ongoing, whether active sessions are present, whether privilege escalation is suspected, and whether lateral movement is suspected.
   - **6.5 Assess Scope:** Identify additional impacted accounts, shared devices, shared IPs, and similar authentication patterns.

7. **Verify Task Completion** - Confirm all identity alert validation steps completed:
   - Alert authenticity validated
   - Impacted identity fully inventoried
   - Authentication activity reviewed
   - Active risk assessed
   - Scope determined

8. **Update Incident Documentation** - Log all alert validation findings, account inventory, and compromise assessment with timestamps.

9. **Escalate if Issues Arise** - If privileged account impacted, multiple accounts impacted, or active attacker session identified, escalate immediately per decision points.

10. **Hand Off or Notify Next Responsible Party** - Inform incident commander and next team of identity alert status and recommended containment actions.

## 3. Post-Action
- Ensure all alert validation findings and containment recommendations are documented in the incident ticket
- Participate in post-incident review if required

## Decision Points
| Condition | Action |
|----------|--------|
| False positive suspected | Validate before containment |
| Privileged account impacted | Escalate severity |
| Multiple accounts impacted | Expand investigation scope |
| Active attacker session identified | Immediate session revocation |

## Output
- Alert validation status
- Impacted account inventory
- Initial compromise assessment
- Recommended containment actions

## Common Failure Modes
- Treating impossible travel as definitive compromise
- Ignoring successful MFA activity
- Missing shared infrastructure indicators

## Related
- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Next: [RB-004.2 Authentication Log Analysis](./RB-004.2-authentication-log-analysis.md)

## Automation Hooks
- Auto-risk enrichment
- Auto-IP reputation checks
- Auto-user context collection
- Auto-session enumeration

## Contributor
**Vishal Thakur**
GitHub: https://github.com/malienist
Contributed to the Arcana Incident Response Documentation Framework.
