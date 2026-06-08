# PB-018: Zero-Day Response

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-018: Zero-Day Response | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    Provide a structured response for zero-day vulnerabilities where no vendor patch or durable fix is available. Use this playbook to validate exposure, reduce exploitability, monitor for exploitation, coordinate vendor communications, and transition to remediation when a fix becomes available.

- **Scope:**

    Applies to newly disclosed or privately reported vulnerabilities affecting organisational assets when exploitation risk exists and no patch, upgrade, or durable remediation is available. If exploitation is confirmed, invoke PB-015.

## 2. Incident Identification & Criteria

**Incident Type:** Zero-Day Response

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- A zero-day vulnerability affects organisational technology and no patch or durable fix is available
- Vendor advisory, threat intelligence, researcher report, or internal finding identifies high-risk exposure without remediation
- Public exploit code, active threat activity, or emergency mitigation guidance exists before a patch is released
- Vulnerability response determines that only temporary containment or compensating controls are currently possible

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | Zero-day exposure is limited, non-critical, or protected by strong compensating controls |
| Sev 2 | Zero-day affects multiple assets, internet-facing systems, or important business services |
| Sev 1 | Zero-day affects critical, privileged, sensitive-data, production, or externally exposed systems |
| Sev 0 | Exploitation is confirmed, widespread impact is likely, or emergency business disruption is required to reduce risk |

## 3. Roles & Responsibilities

- **Incident Commander:** Sets severity, coordinates response, approves containment tradeoffs, and owns escalation decisions.
- **Vulnerability Management Lead:** Tracks advisory status, exposure, mitigations, patch availability, and remediation planning.
- **Technical Lead:** Coordinates compensating controls, monitoring, validation, and transition to remediation.
- **Communications Lead:** Coordinates internal, executive, legal, vendor, customer, and stakeholder communications.
- **Other Roles:**
    - **System / Application Owners:** Implement mitigations, test service impact, and prepare for patching.
    - **Cloud / Network / Platform Teams:** Apply segmentation, access restrictions, WAF/CDN rules, provider controls, and monitoring.
    - **Legal / Compliance:** Reviews disclosure, customer, contractual, regulatory, and law enforcement implications.

## 4. Initial Actions

- **Immediate Steps:**
    - Validate the vulnerability, affected product/version, exposure conditions, and lack of available patch or durable fix.
        - 📘 [RB-TRIAGE-009: Vulnerability Validation](../runbooks/triage/RB-TRIAGE-009-vulnerability-validation.md)
    - Assess vendor guidance, threat intelligence, exploit availability, active campaigns, and emergency mitigations.
        - 📘 [RB-ANALYSIS-042: Vulnerability Threat Intelligence Assessment](../runbooks/analysis/RB-ANALYSIS-042-vulnerability-threat-intelligence-assessment.md)
    - Identify asset owners, business owners, affected services, and emergency decision makers.
    - Contact vendor or provider when clarification, mitigations, timelines, or support are needed.
        - 📘 [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)
    - Engage vulnerability management, platform owners, system/application owners, and IR leadership.
        - 📘 [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)

    > **Decision Point:**
    > - If exploitation is confirmed → execute [PB-015: Active Exploitation](PB-015-active-exploitation.md) immediately.
    > - If a patch, upgrade, or durable fix is available → execute [PB-017: Vulnerability Response](PB-017-vulnerability-response.md).
    > - If no patch or durable fix is available → continue this playbook.

## 5. Investigation & Analysis
> **Common Failure Modes:**
    >- Waiting for a patch while leaving exposed systems reachable
    >- Treating compensating controls as permanent remediation
    > - Failing to monitor for exploitation while no patch exists
    > - Missing cloud, SaaS, third-party, or unsupported asset exposure
    > - Not transitioning to vulnerability response once a fix becomes available

- **Evidence Collection:**
    - Collect vendor advisories, threat intelligence, affected versions, exposure data, asset inventories, mitigations, and detection coverage.
    - Preserve relevant telemetry where exploitation is suspected.

- **Analysis Steps:**
    - Assess exposure requirements, affected attack paths, accessibility, business criticality, and potential impact.
        - 📘 [RB-ANALYSIS-039: Vulnerability Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-039-vulnerability-exposure-assessment.md)
    - Identify all vulnerable assets, owners, versions, environments, and compensating-control groups.
        - 📘 [RB-ANALYSIS-040: Vulnerable Asset Identification](../runbooks/analysis/RB-ANALYSIS-040-vulnerable-asset-identification.md)
    - Verify whether exploitation has occurred or is occurring.
        - 📘 [RB-ANALYSIS-041: Exploitation Verification](../runbooks/analysis/RB-ANALYSIS-041-exploitation-verification.md)
    - Monitor for exploitation indicators across endpoint, identity, cloud, web, network, and application telemetry.
        - 📘 [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
        - 📘 [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
        - 📘 [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md)
        - 📘 [RB-TRIAGE-012: Web Application Attack Triage](../runbooks/triage/RB-TRIAGE-012-web-application-attack-triage.md)

    > **Decision Point:**
    > Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
    > - If exploitation is confirmed → execute [PB-015: Active Exploitation](PB-015-active-exploitation.md) concurrently.
    > - If a patch or durable fix becomes available → transition to [PB-017: Vulnerability Response](PB-017-vulnerability-response.md).
    > - If malware or suspicious execution is identified → execute [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) or [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) concurrently.
    > - If account compromise or credential abuse is identified → execute [PB-004: Account Takeover](PB-004-account-takeover.md) concurrently.
    > - If data exposure, staging, or exfiltration is identified → execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) concurrently.
    > - If cloud compromise is identified → execute [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) concurrently.
    > - If web application compromise is identified → execute [PB-008: Web Application Attack](PB-008-web-application-attack.md) concurrently.

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Reduce exposure using compensating controls such as access restrictions, segmentation, WAF rules, feature disablement, protocol blocking, configuration changes, or service isolation.
        - 📘 [RB-CONTAIN-014: Vulnerability Exposure Reduction](../runbooks/contain/RB-CONTAIN-014-vulnerability-exposure-reduction.md)
    - Apply exploit-path containment if threat intelligence indicates active targeting or high exploitability.
        - 📘 [RB-CONTAIN-012: Exploitation Surface Containment](../runbooks/contain/RB-CONTAIN-012-exploitation-surface-containment.md)
    - Restrict cloud workloads or web application access where affected assets cannot be safely exposed.
        - 📘 [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
        - 📘 [RB-CONTAIN-016: Web Application Access Restriction](../runbooks/contain/RB-CONTAIN-016-web-application-access-restriction.md)

- **Eradication Steps:**
    - Maintain temporary mitigations until a patch, upgrade, replacement, or durable configuration fix is available.
    - Remove exposed features, vulnerable services, integrations, or components if risk cannot be reduced safely.
    - Prepare emergency remediation plans for when a vendor fix becomes available.

- **Recovery Steps:**
    - Transition to PB-017 once a patch, upgrade, or durable fix is available.
    - Validate compensating controls remain effective until permanent remediation is complete.
        - 📘 [RB-RECOVERY-007: Vulnerability Remediation Validation](../runbooks/recovery/RB-RECOVERY-007-vulnerability-remediation-validation.md)
    - Track accepted residual risk, exceptions, compensating controls, and review dates.

## 7. Communication & Escalation

- **Internal Communication:**
    - Notify security leadership, vulnerability management, system/application owners, platform owners, and impacted business stakeholders.
    - Use geo handoff where response spans shifts.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)

- **External Communication:**
    - Coordinate vendor, customer, regulator, executive, and legal communications through approved processes.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
        - 📘 [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Exploitation confirmed | [PB-015: Active Exploitation](PB-015-active-exploitation.md) |
    | Patch, upgrade, or durable fix becomes available | [PB-017: Vulnerability Response](PB-017-vulnerability-response.md) |
    | Malware or suspicious execution identified | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) / [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) |
    | Account compromise or credential abuse identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
    | Data exposure, staging, or exfiltration identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
    | Cloud compromise identified | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
    | Web application compromise identified | [PB-008: Web Application Attack](PB-008-web-application-attack.md) |
    | Major business impact, emergency shutdown, or widespread exposure | [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a PIR covering zero-day intake, exposure assessment, mitigation timing, vendor coordination, monitoring coverage, and transition to remediation.
    - Review whether compensating controls, asset inventory, threat intelligence, and communication paths were sufficient.

- **Documentation Updates:**
    - Update vulnerability records, mitigations, monitoring content, vendor contacts, exception tracking, runbooks, and this playbook based on lessons learned.

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    - [PB-008: Web Application Attack](PB-008-web-application-attack.md)
    - [PB-011: Suspicious Execution](PB-011-suspicious-execution.md)
    - [PB-015: Active Exploitation](PB-015-active-exploitation.md)
    - [PB-017: Vulnerability Response](PB-017-vulnerability-response.md)
    - [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)

- **Runbooks:**
    - [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
    - [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
    - [RB-TRIAGE-009: Vulnerability Validation](../runbooks/triage/RB-TRIAGE-009-vulnerability-validation.md)
    - [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md)
    - [RB-TRIAGE-012: Web Application Attack Triage](../runbooks/triage/RB-TRIAGE-012-web-application-attack-triage.md)
    - [RB-ANALYSIS-039: Vulnerability Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-039-vulnerability-exposure-assessment.md)
    - [RB-ANALYSIS-040: Vulnerable Asset Identification](../runbooks/analysis/RB-ANALYSIS-040-vulnerable-asset-identification.md)
    - [RB-ANALYSIS-041: Exploitation Verification](../runbooks/analysis/RB-ANALYSIS-041-exploitation-verification.md)
    - [RB-ANALYSIS-042: Vulnerability Threat Intelligence Assessment](../runbooks/analysis/RB-ANALYSIS-042-vulnerability-threat-intelligence-assessment.md)
    - [RB-CONTAIN-012: Exploitation Surface Containment](../runbooks/contain/RB-CONTAIN-012-exploitation-surface-containment.md)
    - [RB-CONTAIN-014: Vulnerability Exposure Reduction](../runbooks/contain/RB-CONTAIN-014-vulnerability-exposure-reduction.md)
    - [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
    - [RB-CONTAIN-016: Web Application Access Restriction](../runbooks/contain/RB-CONTAIN-016-web-application-access-restriction.md)
    - [RB-RECOVERY-007: Vulnerability Remediation Validation](../runbooks/recovery/RB-RECOVERY-007-vulnerability-remediation-validation.md)

- **SOPs:**
    - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)

## 10. Appendices

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
