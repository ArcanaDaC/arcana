# RB-RECOVERY-002: Clean System Rebuild

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Clean System Rebuild | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

Applies to any single compromised system that needs to be brought back to a clean state — endpoints, servers, cloud VMs, containers, or SaaS tenants. Reconnection and access restoration are handled at the campaign level by the recovery coordination runbook.

## 1. Prerequisites
- Compromise analysis findings (artefacts, persistence, IOCs)
- System criticality / business impact context
- Access to the target system's management platform (for cleanup, rebuild, and validation)
- Access to EDR / security tooling on the target system

## 2. Step-by-Step Instructions

1. **Determine Recovery Approach**
	- Assess compromise severity
	- Assess persistence mechanisms
	- Assess system criticality
	- Assess confidence in cleanup capability
	- Determine whether cleanup is sufficient or full rebuild / re-provisioning (**recommended**) is required

> Execute **either** 2 (cleanup-in-place) **or** 3 (rebuild / re-provision), based on the decision made in 1. Do not execute both.

2. **Execute Cleanup (Cleanup-In-Place Path Only)**
	- Remove malicious binaries
	- Remove persistence mechanisms
	- Remove malicious services
	- Remove unauthorised configuration changes (registry, system config, IAM policies, app settings)
	- Remove scheduled tasks / cron jobs / automation triggers
	- Remove unauthorised accounts, API keys, tokens, or app installs

3. **Execute Rebuild / Re-provision (Rebuild Path Only)**
	- Perform full system reimage, container rebuild, VM re-provisioning, or tenant reset as appropriate
	- Perform operating system / platform validation
	- Perform security tooling reinstallation
	- Perform patch validation

4. **Validate System Integrity**
	- Confirm no active compromise indicators
	- Confirm no persistence remains
	- Confirm EDR / security tooling operational
	- Confirm security controls healthy
	- Confirm system activity normal


## 3. Post-Action
- Record the chosen recovery path (cleanup or rebuild), the rationale, and a timestamped log of all recovery actions in the incident ticket.
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.