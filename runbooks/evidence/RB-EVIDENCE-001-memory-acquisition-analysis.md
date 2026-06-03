# RB-003.6 Memory Acquisition & Analysis
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Memory Acquisition & Analysis | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Impacted endpoint
- EDR telemetry
- Process execution data
- Suspicious network activity
- Malware indicators

**Required Tools:**
- Memory acquisition tools
- Volatility
- EDR platform
- SIEM
- Threat intelligence platforms

## 2. Step-by-Step Instructions
1. **Confirm Task Assignment** - Verify assignment and confirm need for memory acquisition based on EDR telemetry.

2. **Notify Stakeholders** - Inform the incident commander and endpoint forensics team before acquiring memory.

3. **Access Target System/Resource** - Gain secure access to the impacted endpoint and memory acquisition tools.

4. **Document Current State** - Record endpoint and malware context:
   - Endpoint hostname and IP address
   - Active processes and suspicious indicators
   - Timeline of malware detection
   - Known malware indicators and capabilities

5. **Preserve Evidence (if applicable)** - Prepare for safe memory acquisition:
   - Assess whether system reboot is acceptable
   - Identify acquisition tool and method
   - Plan metadata preservation and chain of custody documentation

6. **Execute Task Steps** - Perform systematic memory acquisition and analysis:
   - **6.1 Validate Need for Memory Acquisition:** Determine whether malware is currently active, whether in-memory execution is suspected, whether credential theft is suspected, and whether process injection is suspected.
   - **6.2 Acquire Memory Safely:** Perform full memory acquisition while preserving acquisition metadata and documenting acquisition time. Maintain chain of custody where required. Avoid rebooting system prior to acquisition and running unnecessary tools.
   - **6.3 Analyse Active Processes:** Identify suspicious processes, hidden processes, injected processes, unsigned modules, and parent-child anomalies.
   - **6.4 Review Network Connections:** Check active sockets, suspicious outbound connections, beaconing behaviour, and listening services.
   - **6.5 Identify Credential Artefacts:** Look for LSASS access, plaintext credentials, tokens, Kerberos tickets, and browser session data.
   - **6.6 Identify In-Memory Persistence:** Review reflective DLL loading, process hollowing, APC injection, and memory-only payloads.

7. **Verify Task Completion** - Confirm all memory analysis steps completed:
   - Memory acquired safely with metadata preserved
   - Active processes analysed for indicators
   - Network connections reviewed
   - Credential artefacts identified
   - In-memory persistence mechanisms identified

8. **Update Incident Documentation** - Log all memory analysis findings, IOCs discovered, and credential exposure assessment with timestamps.

9. **Escalate if Issues Arise** - If credential theft, lateral movement artefacts, or memory-only malware identified, escalate immediately per decision points.

10. **Hand Off or Notify Next Responsible Party** - Inform incident commander and next team of memory analysis findings and recommended escalation or hunting activities.

## 3. Post-Action
- Ensure all memory analysis findings are documented in the incident record
- Participate in post-incident review if required

## Decision Points
| Condition | Action |
|----------|--------|
| Credential theft identified | Escalate to PB-004 |
| Lateral movement artefacts identified | Escalate to PB-010 |
| Memory-only malware identified | Expand hunting activities |

## Output
- Memory analysis findings
- Process injection findings
- Credential exposure assessment
- Active network connection inventory

## Common Failure Modes
- Rebooting systems before acquisition
- Ignoring memory-only malware
- Failing to preserve acquisition metadata

## Related
- Playbook: [PB-003 Endpoint Malware Infection](../../playbooks/PB-003-endpoint-malware.md)
- Previous: [RB-003.5 Malware Payload Analysis](./RB-003.5-malware-payload-analysis.md)
- Next: [RB-003.7 Recovery & Rebuild](./RB-003.7-recovery-rebuild.md)

## Automation Hooks
- Auto-memory acquisition
- Auto-process anomaly detection
- Auto-network artefact extraction
