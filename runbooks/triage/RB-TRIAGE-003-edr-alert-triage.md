# RB-003.1 EDR Alert Triage
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | EDR Alert Triage | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- EDR alerts
- Endpoint telemetry
- Process execution data
- File hashes
- User and host information
- Threat intelligence enrichment

**Required Tools:**
- EDR platform
- SIEM
- Threat intelligence platform
- Asset inventory
- Authentication telemetry

## 2. Step-by-Step Instructions
1. **Confirm Task Assignment** - Verify assignment and review the EDR alert details.

2. **Notify Stakeholders** - Inform the incident commander and relevant endpoint security team.

3. **Access Target System/Resource** - Log in to EDR platform and SIEM to retrieve alert and telemetry data.

4. **Document Current State** - Record alert and endpoint metadata:
   - Alert source, detection type, and confidence level
   - Hostname, IP address, logged-in user
   - Device criticality and business owner
   - Operating system details

5. **Preserve Evidence (if applicable)** - Collect and document malware indicators:
   - File hashes and process names
   - Command-line arguments
   - Parent-child process chains
   - Network connections

6. **Execute Task Steps** - Perform systematic EDR alert triage:
   - **6.1 Validate Alert Authenticity:** Determine alert source, detection type, and confidence level. Review detection signatures, behavioural indicators, and alert metadata. Assess whether detection is prevention or detection only.
   - **6.2 Identify Impacted Endpoint:** Collect hostname, IP address, logged-in user, device criticality, operating system, and business owner information.
   - **6.3 Review Malware Indicators:** Identify file hashes, process names, command-line arguments, parent-child process chains, and network connections.
   - **6.4 Assess Execution Status:** Determine whether malware was blocked, whether execution was successful, whether malware is still active, and whether persistence occurred.
   - **6.5 Assess Potential Scope:** Review similar detections across environment, same hash/process activity, shared user activity, and shared infrastructure usage.
   - **6.6 Determine Severity:** Assess malware capability, credential theft potential, lateral movement indicators, persistence mechanisms, and critical system involvement.

7. **Verify Task Completion** - Confirm all alert validation steps completed:
   - Alert authenticity validated
   - Impacted endpoint fully inventoried
   - IOCs extracted and enriched
   - Severity assessment completed
   - Scope determined

8. **Update Incident Documentation** - Log all alert validation findings, IOCs, and severity assessment with timestamps.

9. **Escalate if Issues Arise** - If malware is active, multiple systems impacted, or credential theft suspected, escalate immediately per decision points.

10. **Hand Off or Notify Next Responsible Party** - Inform incident commander and next team of alert status and recommended containment or escalation actions.

## 3. Post-Action
- Ensure all alert validation findings and initial IOC list are documented in the incident ticket
- Participate in post-incident review if required

## Decision Points
| Condition | Action |
|----------|--------|
| False positive suspected | Validate before escalation |
| Malware active | Proceed to containment |
| Multiple systems impacted | Expand investigation scope |
| Credential theft suspected | Escalate to PB-004 |

## Output
- Alert validation status
- Severity assessment
- Impacted endpoint list
- Initial IOC list
- Recommended containment actions

## Common Failure Modes
- Treating behavioural detections as false positives too early
- Ignoring blocked malware activity
- Failing to assess broader scope

## Related
- Playbook: [PB-003 Endpoint Malware Infection](../../playbooks/PB-003-endpoint-malware.md)
- Next: [RB-003.2 Process Tree Analysis](./RB-003.2-process-tree-analysis.md)

## Automation Hooks
- Auto-IOC enrichment
- Auto-hash reputation checks
- Auto-scope expansion searches
- Auto-ticket creation
