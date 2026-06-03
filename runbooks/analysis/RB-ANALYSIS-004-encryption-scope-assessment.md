# RB-002.3-Encryption Scope Assessment

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Encryption Scope Assessment | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- EDR telemetry access
- File server logs
- User reports and incident notifications
- SIEM alerts
- Network share telemetry
- SIEM platform access
- EDR platform access
- File integrity monitoring access
- Backup platform access
- Asset inventory systems access

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment** — Verify responsibility for impact assessment

2. **Notify Stakeholders** — Alert business units and leadership of scope assessment initiation

3. **Access Target System/Resource** — Prepare tools for comprehensive asset and encryption analysis

4. **Document Current State** — Record initial reports and known impacted systems

5. **Preserve Evidence (if applicable)** — Capture snapshots of file servers and backup status

6. **Execute Task Steps**

   6.1. **Identify Impacted Systems**
   - Determine endpoints impacted
   - Identify servers impacted
   - Identify hypervisors impacted
   - Identify cloud resources impacted

   6.2. **Identify Encrypted Data**
   - Assess file shares impact
   - Assess databases impact
   - Assess user directories impact
   - Assess critical applications impact
   - Assess SaaS platforms impact

   6.3. **Assess Business Impact**
   - Determine business units impacted
   - Identify critical services unavailable
   - Assess operational disruption severity

   6.4. **Review Encryption Patterns**
   - Identify file extensions used
   - Review ransom note patterns
   - Determine encryption speed
   - Assess selective targeting behaviour

   6.5. **Identify Backup Exposure**
   - Determine if backups were encrypted
   - Identify backup deletion activity
   - Assess immutable storage impact

   6.6. **Build Impact Inventory**
   - Document impacted systems
   - Prioritize recovery sequence
   - Estimate restoration effort for each asset

7. **Verify Task Completion** — Confirm scope assessment complete and business impact documented

8. **Update Incident Documentation** — Record impact inventory and recovery priorities

9. **Escalate if Issues Arise** — Flag severity escalations and backup compromise to leadership

10. **Hand Off or Notify Next Responsible Party** — Pass to containment and recovery coordination teams

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Critical infrastructure impacted | Escalate severity |
| Backup compromise identified | Immediate executive escalation |
| Cloud resources impacted | Expand scope investigation |

---

## Output

- Scope assessment
- Impact inventory
- Business impact summary
- Recovery prioritisation list

---

## Common Failure Modes

- Underestimating scope
- Ignoring cloud/SaaS impact
- Failing to identify backup compromise

---

## Automation Hooks

- Auto-identify impacted assets
- Auto-map impacted business services
- Auto-generate recovery inventory

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Previous: [RB-002.2 Identify Patient Zero](./RB-002.2-identify-patient-zero.md)
- Next: [RB-002.6 Active Directory Containment](./RB-002.6-active-directory-containment.md)
