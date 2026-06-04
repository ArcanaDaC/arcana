# RB-RECOVERY-001: Recovery & Restoration Coordination

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Recovery & Restoration Coordination | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Recovery prioritisation list
- Backup validation status
- Containment status
- Infrastructure dependency mapping
- Business impact assessment
- Access to backup platform
- Access to virtualisation platform
- Access to asset inventory
- Access to SIEM
- Access to EDR platform

## 2. Step-by-Step Instructions

1. **Validate Containment Status**
	- Confirm lateral movement has stopped
	- Confirm persistence mechanisms addressed
	- Confirm privileged access reviewed
	- Confirm compromised systems isolated

2. **Prioritise Recovery Activities**
	- Restore based on business criticality
	- Restore based on dependency order
	- Restore based on infrastructure requirements
	- Restore based on recovery feasibility

3. **Plan the Recovery**
	- Define RTO/RPO for each in-scope system based on business impact
	- Determine the recovery method per system (restore from backup, rebuild from gold image, re-deploy from IaC, re-provision in clean account/tenant)
	- Map dependencies between systems and confirm the restoration order respects them
	- Define success criteria for each phase (system reachable, service responsive, end-to-end flow validated)
	- Define a rollback plan for each phase
	- Confirm people, tooling, and vendor support are available for the planned execution window
	- Align the plan with the Incident Commander and stakeholder communications plan

4. **Coordinate Phased Restoration**
	- Sequence restoration in phases (typically: core infrastructure → identity → critical applications → user endpoints), informed by the plan in 6.3
	- For each system in scope, dispatch the appropriate per-system runbook (e.g. RB-RECOVERY-002 for system rebuild, RB-RECOVERY-003 for user access restoration)
	- Gate progression to the next phase on validation of the current phase (step 6.5)
	- Track per-phase progress and blockers

5. **Validate Restored Systems**
	- Check system functionality
	- Check for compromise indicators (malware, persistence, unauthorised access, modified configuration)
	- Check authentication integrity
	- Check network connectivity

6. **Monitor for Recurrence**
	- Monitor EDR telemetry
	- Monitor authentication anomalies
	- Monitor for activity matching the incident's IOCs and TTPs
	- Monitor suspicious outbound traffic

7. **Reintroduce Systems Carefully**
	- Gradually reconnect segmented systems
	- Gradually restore trust relationships
	- Gradually re-enable network pathways

## 3. Post-Action
- Document all coordination actions, decisions, and phase outcomes in the incident ticket, including timestamps
- Confirm all in-scope systems have a closed state (restored / rebuild deferred / decommissioned / risk accepted)
- Notify the Incident Commander that recovery coordination is complete
---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.