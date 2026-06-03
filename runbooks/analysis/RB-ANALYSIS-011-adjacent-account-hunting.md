# RB-004.8-Adjacent Account Hunting

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Adjacent Account Hunting | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

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

1. **Confirm Task Assignment** — Verify responsibility for adjacent account investigation

2. **Notify Stakeholders** — Alert incident management of scope expansion analysis

3. **Access Target System/Resource** — Prepare identity and endpoint platforms for correlation analysis

4. **Document Current State** — Record initial compromised account and known shared indicators

5. **Preserve Evidence (if applicable)** — Capture baseline telemetry before expanded hunting

6. **Execute Task Steps**

   6.1. **Identify Shared Indicators**
   - Review shared source IPs
   - Review shared devices
   - Review shared browser fingerprints
   - Review shared session tokens
   - Review shared geolocation patterns

   6.2. **Hunt for Similar Authentication Behaviour**
   - Identify similar impossible travel activity
   - Identify similar MFA anomalies
   - Identify similar login timing patterns
   - Identify similar user-agent strings

   6.3. **Review Shared Infrastructure Usage**
   - Assess shared endpoints
   - Assess shared VPN gateways
   - Assess shared jump hosts
   - Assess shared SaaS integrations

   6.4. **Identify Administrative Relationship Exposure**
   - Determine shared privileged access
   - Determine delegated administration
   - Determine shared mailbox access
   - Determine shared API access

   6.5. **Review OAuth & Token Reuse**
   - Identify shared OAuth grants
   - Identify shared refresh tokens
   - Identify suspicious delegated permissions
   - Identify cross-account token activity

   6.6. **Expand Scope Investigation**
   - If additional compromise identified, escalate investigation scope
   - Expand containment actions
   - Expand credential reset scope

7. **Verify Task Completion** — Confirm adjacent account assessment complete and scope determined

8. **Update Incident Documentation** — Record adjacent accounts and shared infrastructure findings

9. **Escalate if Issues Arise** — Flag multiple compromises or privileged access for escalation

10. **Hand Off or Notify Next Responsible Party** — Pass to user recovery and restoration teams

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Multiple accounts compromised | Expand incident severity |
| Shared privileged access identified | Escalate to PB-009 |
| Shared malware indicators identified | Escalate to PB-003 |

---

## Output

- Adjacent account assessment
- Additional impacted account inventory
- Shared infrastructure findings
- Expanded compromise scope

---

## Common Failure Modes

- Focusing only on the initially impacted user
- Ignoring delegated access
- Missing shared endpoint relationships

---

## Automation Hooks

- Auto-identity correlation
- Auto-behaviour clustering
- Auto-shared infrastructure mapping
- Auto-risk scoring

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.7 Credential Exposure Investigation](./RB-004.7-credential-exposure-investigation.md)
- Next: [RB-004.9 User Recovery & Access Restoration](./RB-004.9-user-recovery-access-restoration.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
