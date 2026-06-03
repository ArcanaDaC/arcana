# RB-004.7-Credential Exposure Investigation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Credential Exposure Investigation | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

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

1. **Confirm Task Assignment** — Verify responsibility for credential exposure analysis

2. **Notify Stakeholders** — Alert security and user management teams of exposure investigation

3. **Access Target System/Resource** — Prepare threat intel platforms and authentication logs for review

4. **Document Current State** — Record known exposure vectors and affected users

5. **Preserve Evidence (if applicable)** — Capture credential-related logs and threat intel data

6. **Execute Task Steps**

   6.1. **Identify Initial Exposure Vector**
   - Determine exposure through phishing
   - Determine exposure through malware
   - Determine exposure through credential stuffing
   - Determine exposure through password reuse
   - Determine exposure through browser credential theft
   - Determine exposure through token theft
   - Determine exposure through public credential leaks

   6.2. **Review Authentication Timeline**
   - Identify earliest suspicious login
   - Identify failed authentication attempts
   - Review MFA activity
   - Review password reset activity
   - Review session creation activity

   6.3. **Assess Password Reuse Risk**
   - Determine shared password usage
   - Assess corporate/personal password overlap
   - Assess service account reuse
   - Assess administrative credential reuse

   6.4. **Review Endpoint Exposure Indicators**
   - Identify browser credential dumping
   - Identify token theft activity
   - Identify session cookie theft
   - Identify password manager compromise
   - Review infostealer activity

   6.5. **Review External Exposure Sources**
   - Check credential dump repositories
   - Review threat intelligence feeds
   - Review dark web monitoring sources
   - Review known breach datasets

   6.6. **Identify Adjacent Risk**
   - Assess additional affected accounts
   - Assess shared devices
   - Assess shared authentication infrastructure
   - Assess shared API credentials

7. **Verify Task Completion** — Confirm exposure vector identified and scope determined

8. **Update Incident Documentation** — Record exposure findings and adjacent risk assessment

9. **Escalate if Issues Arise** — Flag malware or privilege credential exposure for escalation

10. **Hand Off or Notify Next Responsible Party** — Pass to credential reset and adjacent account hunting teams

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Malware-based theft identified | Escalate to PB-003 |
| Phishing identified | Escalate to PB-001 |
| Password reuse identified | Expand credential reset scope |
| Privileged credential exposure identified | Escalate to PB-009 |

---

## Output

- Credential exposure assessment
- Exposure source determination
- Password reuse findings
- Adjacent risk assessment

---

## Common Failure Modes

- Resetting only one affected account
- Ignoring browser-stored credentials
- Missing service account reuse

---

## Automation Hooks

- Auto-password reuse detection
- Auto-credential leak enrichment
- Auto-token exposure hunting
- Auto-adjacent account correlation

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.6 Privileged Access Assessment](./RB-004.6-privileged-access-assessment.md)
- Next: [RB-004.8 Adjacent Account Hunting](./RB-004.8-adjacent-account-hunting.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
