# RB-004.2-Authentication Log Analysis

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Authentication Log Analysis | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

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

1. **Confirm Task Assignment** — Verify responsibility for authentication analysis

2. **Notify Stakeholders** — Alert identity and security teams of authentication review initiation

3. **Access Target System/Resource** — Prepare identity provider and SIEM for comprehensive log review

4. **Document Current State** — Record known suspicious login events and timeline markers

5. **Preserve Evidence (if applicable)** — Capture authentication logs for forensic analysis

6. **Execute Task Steps**

   6.1. **Build Authentication Timeline**
   - Identify earliest suspicious login
   - Document successful authentications
   - Document failed login attempts
   - Review MFA activity
   - Review session creation events

   6.2. **Review Source Infrastructure**
   - Assess source IPs
   - Determine ASN/provider
   - Determine geolocation
   - Review known malicious infrastructure
   - Identify VPN or anonymisation usage

   6.3. **Analyse Device & Session Context**
   - Review device identifiers
   - Review browser fingerprints
   - Assess session duration
   - Review user-agent strings
   - Identify new device registrations

   6.4. **Review MFA Activity**
   - Identify MFA fatigue attempts
   - Identify push bombing
   - Identify MFA bypass activity
   - Review device registration anomalies
   - Analyze failed MFA attempts

   6.5. **Assess Privileged Activity**
   - Determine administrative logins
   - Review privileged role usage
   - Review sensitive application access
   - Document unusual administrative actions

   6.6. **Correlate Additional Activity**
   - Review endpoint telemetry
   - Review VPN access
   - Review SaaS access
   - Review cloud activity
   - Review lateral movement indicators

7. **Verify Task Completion** — Confirm authentication timeline built and suspicious sessions identified

8. **Update Incident Documentation** — Record authentication findings and MFA anomalies

9. **Escalate if Issues Arise** — Flag MFA bypass or administrative compromise for escalation

10. **Hand Off or Notify Next Responsible Party** — Pass to session revocation or containment teams

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| MFA bypass identified | Escalate severity |
| Administrative access identified | Escalate to PB-009 |
| Multiple identities impacted | Expand hunting scope |

---

## Output

- Authentication timeline
- Suspicious session inventory
- Source infrastructure assessment
- MFA findings

---

## Common Failure Modes

- Focusing only on failed logins
- Ignoring token reuse activity
- Missing impossible travel suppression logic

---

## Automation Hooks

- Auto-timeline generation
- Auto-IP enrichment
- Auto-impossible travel correlation
- Auto-MFA anomaly detection

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.1 Identity Alert Triage](./RB-004.1-identity-alert-triage.md)
- Next: [RB-004.3 Session & Token Revocation](./RB-004.3-session-token-revocation.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
