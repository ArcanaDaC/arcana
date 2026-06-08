# PB-011: Suspicious Execution

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-011: Suspicious Execution | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    This playbook defines the response workflow for suspicious process, command-line, script, binary, or interpreter execution. It helps responders validate whether activity is authorised, malicious, or part of a broader incident such as malware, privilege escalation, lateral movement, account takeover, cloud compromise, or data exfiltration.

- **Scope:**

    Applies to suspicious execution on endpoints, servers, cloud workloads, containers, virtual machines, administrative hosts, and user workstations. Includes LOLBin abuse, encoded or obfuscated commands, script execution, suspicious parent-child processes, unknown binaries, EDR behavioural detections, and unauthorised administrative tooling.

## 2. Incident Identification & Criteria

**Incident Type:** Suspicious Execution

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- Suspicious process execution or EDR behavioural alert
- Encoded, obfuscated, or high-risk command-line activity
- PowerShell, bash, Python, JavaScript, VBScript, HTA, or batch execution from unusual context
- LOLBin abuse such as suspicious PowerShell, rundll32, regsvr32, mshta, wmic, certutil, bitsadmin, schtasks, cscript, or wscript activity
- Office, browser, email client, archive utility, or PDF reader spawning a shell, interpreter, or downloader
- Unknown, unsigned, or newly dropped binary execution
- Execution from temporary directories, user profile paths, network shares, removable media, or cloud sync folders
- Process behaviour indicating persistence, credential theft, lateral movement, discovery, staging, or exfiltration

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | Suspicious execution requiring validation; no confirmed malicious outcome |
| Sev 2 | Confirmed unauthorised or malicious execution on a single non-critical endpoint with limited impact |
| Sev 1 | Execution linked to credential theft, persistence, privilege escalation, lateral movement, data staging, or a critical asset |
| Sev 0 | Widespread malicious execution, active propagation, ransomware behaviour, or enterprise-wide compromise |

## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates response, sets severity, approves containment, and manages escalation.
- **Incident Responder / Forensic Analyst:** Validates execution activity, analyses command lines and process trees, scopes affected assets, and preserves evidence.
- **Communications Lead:** Coordinates internal updates and affected-user communications.
- **Other Roles:**
    - **Endpoint / Platform Team:** Supports host isolation, log collection, rebuild, and endpoint control validation.
    - **Identity & Access Team:** Supports account containment if execution indicates credential or token theft.
    - **Network Team:** Supports outbound blocking or segmentation when C2, download, exfiltration, or lateral movement is identified.
    - **Cloud Security / Platform Team:** Supports cloud workload evidence collection and isolation when suspicious execution occurs in cloud-hosted infrastructure.
    - **Application / Service Owners:** Validate business purpose and support recovery where execution occurred in production systems.

## 4. Initial Actions

- **Immediate Steps:**
    - Triage the alert, affected host, user context, process, parent process, command line, file hash, and detection source.
        - 📘 [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
    - Determine whether the process is still running, whether child processes exist, and whether network activity is active.

    > **Decision Point:**
    > - If execution is approved and expected → document rationale and close.
    > - If malicious, unauthorised, or unresolved → continue investigation and contain if active risk exists.

    > **Warning:** Do not assume execution is benign because the binary is signed, the command completed successfully, the user appears to have initiated it, or antivirus did not alert.

## 5. Investigation & Analysis

- **Evidence Collection:**
    - Collect process execution, command line, parent-child process, file, registry, persistence, network, DNS, authentication, and EDR telemetry for the affected host and time window.
        - 📘 [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
        - 📘 [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
        - If execution occurred on a cloud workload, preserve cloud control plane and workload evidence.
            - 📘 [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
            - 📘 [RB-EVIDENCE-005: Cloud Workload Snapshot Acquisition](../runbooks/evidence/RB-EVIDENCE-005-cloud-workload-snapshot-acquisition.md)
    - Preserve suspicious scripts, binaries, payloads, command output, decoded content, hashes, and sandbox results where available.

- **Analysis Steps:**
    - Reconstruct process ancestry, child processes, execution source, and user context.
        - 📘 [RB-ANALYSIS-006: Process Tree Analysis](../runbooks/analysis/RB-ANALYSIS-006-process-tree-analysis.md)
    - Analyse full command lines, arguments, hidden flags, download activity, encoded content, and adversary techniques.
        - 📘 [RB-ANALYSIS-023: Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)
    - Investigate LOLBin usage and determine whether legitimate tools were abused for execution, persistence, credential access, discovery, lateral movement, staging, exfiltration, or evasion.
        - 📘 [RB-ANALYSIS-024: LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)
    - Analyse script type, origin, contents, obfuscation, network activity, and execution intent.
        - 📘 [RB-ANALYSIS-025: Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)
    - Validate whether execution was authorised by the user, manager, system owner, IT operations, development team, change record, or scheduled maintenance.
        - 📘 [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
    - Review persistence mechanisms if execution created services, scheduled tasks, startup entries, registry changes, cron jobs, launch agents, WMI subscriptions, or cloud scheduled execution.
        - 📘 [RB-ANALYSIS-014: Malware Persistence Mechanism Hunt](../runbooks/analysis/RB-ANALYSIS-014-malware-persistence-mechanism-hunt.md)
    - Analyse malware behaviour where payloads, C2, credential theft, persistence, or secondary execution are identified.
        - 📘 [RB-ANALYSIS-015: Malware Analysis](../runbooks/analysis/RB-ANALYSIS-015-malware-analysis.md)
    - Analyse memory where process injection, in-memory execution, hidden processes, credential material, or memory-only malware is suspected.
        - 📘 [RB-ANALYSIS-016: Memory Analysis](../runbooks/analysis/RB-ANALYSIS-016-memory-analysis.md)
    - Review outbound traffic if execution involved downloads, C2, reverse shells, cloud storage, or external transfers.
        - 📘 [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
    - Hunt for the same hashes, command lines, scripts, tools, parent processes, users, or infrastructure across the environment.
        - 📘 [RB-ANALYSIS-035: Affected Asset Identification](../runbooks/analysis/RB-ANALYSIS-035-affected-asset-identification.md)

    > **Decision Point:**
    > Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
    > - Malware confirmed → execute [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) concurrently.
    > - Privilege escalation identified → execute [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) concurrently.
    > - Lateral movement identified → execute [PB-010: Lateral Movement](PB-010-lateral-movement.md) concurrently.
    > - Credential or account compromise identified → execute [PB-004: Account Takeover](PB-004-account-takeover.md) concurrently.
    > - Data staging or exfiltration identified → execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) concurrently.
    > - Cloud workload or control plane abuse identified → execute [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) concurrently.

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Isolate affected hosts when execution is malicious, still active, or associated with credential theft, persistence, C2, or lateral movement.
        - 📘 [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
    - Isolate affected cloud workloads when suspicious execution occurs in cloud infrastructure.
        - 📘 [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
    - Lock or reset accounts and revoke sessions where credential theft, token theft, or account misuse is suspected.
        - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
        - 📘 [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - Block active outbound attacker infrastructure or transfer paths.
        - 📘 [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
    - Restrict lateral movement paths if remote execution or propagation is suspected.
        - 📘 [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)

- **Eradication Steps:**
    - Remove malicious binaries, scripts, payloads, scheduled tasks, services, registry entries, cron jobs, launch agents, WMI subscriptions, attacker-created accounts, and unauthorised tooling.
    - Remove or roll back unauthorised configuration changes and persistence mechanisms.
    - Rotate credentials, secrets, tokens, certificates, and keys that may have been exposed during execution.

- **Recovery Steps:**
    - Rebuild or re-provision systems where integrity cannot be validated.
        - 📘 [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
    - Coordinate phased restoration when multiple hosts, users, or dependencies are affected.
        - 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
    - Restore user access only after credentials, sessions, tokens, MFA, and endpoint integrity are validated.
        - 📘 [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
    - Monitor for recurrence using hashes, command lines, decoded content, parent-child chains, network destinations, scripts, and observed TTPs.

## 7. Communication & Escalation

- **Internal Communication:**
    - Notify security leadership, endpoint/platform owners, identity teams, service owners, and affected business teams when containment or downtime is required.
    - Use geo handoff where the incident spans shifts.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - Notify affected users if account reset, MFA reset, device rebuild, or access restoration is required.
        - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **External Communication:**
    - Engage Legal/Privacy if suspicious execution resulted in customer data access, regulated data exposure, public service impact, or third-party impact.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Malware, payload, C2, or persistence confirmed | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) |
    | Credential theft or account compromise identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
    | Privilege escalation identified | [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) |
    | Lateral movement or remote execution identified | [PB-010: Lateral Movement](PB-010-lateral-movement.md) |
    | Data staging or exfiltration identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
    | Cloud workload or control plane abuse identified | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
    | Widespread execution, ransomware behaviour, or critical infrastructure impact | [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a Post-Incident Review (PIR)
    - Document what worked, what didn't, and what needs improvement

- **Documentation Updates:**
    - Update this playbook, linked runbooks, detection content, allowlists, administrative tooling guidance, and endpoint hardening guidance where required.

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    - [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
    - [PB-010: Lateral Movement](PB-010-lateral-movement.md)
    - [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md)

- **Runbooks:**
    - [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
    - [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
    - [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
    - [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
    - [RB-EVIDENCE-005: Cloud Workload Snapshot Acquisition](../runbooks/evidence/RB-EVIDENCE-005-cloud-workload-snapshot-acquisition.md)
    - [RB-ANALYSIS-006: Process Tree Analysis](../runbooks/analysis/RB-ANALYSIS-006-process-tree-analysis.md)
    - [RB-ANALYSIS-014: Malware Persistence Mechanism Hunt](../runbooks/analysis/RB-ANALYSIS-014-malware-persistence-mechanism-hunt.md)
    - [RB-ANALYSIS-015: Malware Analysis](../runbooks/analysis/RB-ANALYSIS-015-malware-analysis.md)
    - [RB-ANALYSIS-016: Memory Analysis](../runbooks/analysis/RB-ANALYSIS-016-memory-analysis.md)
    - [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
    - [RB-ANALYSIS-023: Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)
    - [RB-ANALYSIS-024: LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)
    - [RB-ANALYSIS-025: Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)
    - [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
    - [RB-ANALYSIS-035: Affected Asset Identification](../runbooks/analysis/RB-ANALYSIS-035-affected-asset-identification.md)
    - [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
    - [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
    - [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
    - [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
    - [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
    - [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
    - [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
    - [RB-POST-001: Ransomware Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-ransomware-post-incident-hardening.md)

- **SOPs:**
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

## 10. Appendices

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
