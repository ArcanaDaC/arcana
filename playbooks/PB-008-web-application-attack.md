# PB-008: Web Application Attack

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-008: Web Application Attack | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

  Provide a clear response workflow for suspected or confirmed web application attacks, including exploitation, API abuse, broken access control, web shells, application-layer denial of service, data exposure, and application tampering.

- **Scope:**

  Applies to internet-facing and internal web applications, APIs, portals, administrative interfaces, and supporting infrastructure across on-premises, cloud, container, serverless, PaaS, and SaaS-integrated environments.

## 2. Incident Identification & Criteria

**Incident Type:** Web Application Attack

**Trigger Conditions:**

- Web, API, WAF, CDN, IDS/IPS, or SIEM alert
- Exploit attempts against application endpoints
- Broken access control or unauthorised object access
- Web shell, suspicious upload, or defacement
- Unusual API usage, scraping, or enumeration
- Credential stuffing, session abuse, or token abuse
- Reported exploitation, tampering, or data exposure

**Severity Levels:**

| Severity | Description |
|----------|------------|
| Sev 3 | Suspected or confirmed exploitation with minimal impact, no sensitive data exposure, no privileged access, and no active attacker presence |
| Sev 2 | Confirmed exploitation with limited impact, contained unauthorised access, or impact to a non-critical application |
| Sev 1 | Confirmed exploitation of a production or sensitive application, unauthorised sensitive data access, web shell, privileged access, or active attacker presence |
| Sev 0 | Large-scale customer or regulated data exposure, critical service compromise/outage, payment or authentication system compromise, or multi-application compromise |

## 3. Roles & Responsibilities

- **Incident Commander:** Owns severity, coordination, containment decisions, escalation, and incident timeline.
- **Technical Lead / AppSec Lead:** Directs technical investigation, containment strategy, and remediation validation.
- **Incident Responder / Forensic Analyst:** Collects evidence, builds timeline, scopes impact, and documents findings.
- **Application Engineering Team:** Supports application logs, code/config review, emergency fixes, deployments, and validation.
- **Platform / Infrastructure Team:** Supports WAF/CDN/API gateway changes, workload isolation, log export, and recovery.
- **IAM Team:** Supports account lockdown, session/token revocation, MFA reset, and API key/secret rotation.
- **Communications Lead:** Coordinates internal/external updates with Legal/Privacy where required.

## 4. Initial Actions

- Validate the alert or report and classify the suspected attack type.
  - 📘 [RB-TRIAGE-012: Web Application Attack Triage](../runbooks/triage/RB-TRIAGE-012-web-application-attack-triage.md)
  > **Decision Point:**
  > - Benign or authorised testing → close with documented rationale.
  > - Suspicious or malicious → continue.

- Determine whether attacker activity is ongoing and whether immediate containment is required.

> **Warning:** Preserve evidence where feasible before deleting files, terminating workloads, rotating secrets, or deploying blocks. If active harm is ongoing, contain first and document the evidence trade-off.

## 5. Investigation & Analysis

- Collect web, application, identity, host, and cloud evidence as applicable.
  - 📘 [RB-EVIDENCE-006: Web Application Log Acquisition](../runbooks/evidence/RB-EVIDENCE-006-web-application-log-acquisition.md)
  - 📘 [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
  - 📘 [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
  - 📘 [RB-EVIDENCE-005: Cloud Workload Snapshot Acquisition](../runbooks/evidence/RB-EVIDENCE-005-cloud-workload-snapshot-acquisition.md)

- Reconstruct the request timeline, confirm exploitation status, and identify affected endpoints, sessions, users, and data.
  - 📘 [RB-ANALYSIS-044: Web Application Attack Analysis](../runbooks/analysis/RB-ANALYSIS-044-web-application-attack-analysis.md)

- If exploitation of a vulnerability is suspected, validate exploitation and identify affected assets.
  - 📘 [RB-ANALYSIS-034: Exploitation Activity Analysis](../runbooks/analysis/RB-ANALYSIS-034-exploitation-activity-analysis.md)
  - 📘 [RB-ANALYSIS-035: Affected Asset Identification](../runbooks/analysis/RB-ANALYSIS-035-affected-asset-identification.md)

- If outbound callbacks, reverse shells, or data movement are observed, analyse outbound traffic and data impact.
  - 📘 [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
  - 📘 [RB-ANALYSIS-021: Sensitive Data Impact Assessment](../runbooks/analysis/RB-ANALYSIS-021-sensitive-data-impact-assessment.md)
  - 📘 [RB-ANALYSIS-022: Exfiltration Scoping Hunt](../runbooks/analysis/RB-ANALYSIS-022-exfiltration-scoping-hunt.md)

- If credentials, sessions, tokens, or API keys are involved, analyse identity activity.
  - 📘 [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
  - 📘 [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)

> **Decision Point:**
> Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
> - Account/session/token compromise → [PB-004: Account Takeover](PB-004-account-takeover.md)
> - Data exposure/exfiltration → [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
> - Web shell or host compromise → [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
> - Active exploitation → [PB-015: Active Exploitation](PB-015-active-exploitation.md)
> - Cloud workload/control plane compromise → [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
> - Application-layer denial of service → [PB-013: DDoS](PB-013-ddos.md)

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
  - Restrict affected applications, APIs, routes, features, tenants, upload paths, export paths, integrations, or admin functions.
    - 📘 [RB-CONTAIN-016: Web Application Access Restriction](../runbooks/contain/RB-CONTAIN-016-web-application-access-restriction.md)
  - Reduce exploitation or vulnerability exposure where the root cause is a vulnerable service, component, or endpoint.
    - 📘 [RB-CONTAIN-012: Exploitation Surface Containment](../runbooks/contain/RB-CONTAIN-012-exploitation-surface-containment.md)
    - 📘 [RB-CONTAIN-014: Vulnerability Exposure Reduction](../runbooks/contain/RB-CONTAIN-014-vulnerability-exposure-reduction.md)
  - Isolate compromised hosts or cloud workloads if code execution, web shell, or runtime compromise is suspected.
    - 📘 [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
    - 📘 [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
  - Revoke affected accounts, sessions, tokens, API keys, and credentials.
    - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - 📘 [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - Block active outbound attacker channels or exfiltration destinations.
    - 📘 [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)

- **Eradication Steps:**
  - Remove web shells, malicious uploads, attacker-created accounts/tokens, persistence jobs, and unauthorised integrations.
  - Patch or reconfigure the vulnerable code path, dependency, route, feature, or access control.
  - Rotate exposed or potentially exposed secrets, signing keys, API keys, database credentials, service credentials, and session secrets.

- **Recovery Steps:**
  - Redeploy or rebuild compromised workloads from known-good source, images, or infrastructure-as-code where integrity is uncertain.
    - 📘 [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
  - Validate remediation and service functionality.
    - 📘 [RB-RECOVERY-007: Vulnerability Remediation Validation](../runbooks/recovery/RB-RECOVERY-007-vulnerability-remediation-validation.md)
  - Coordinate phased restoration where multiple services or dependencies are affected.
    - 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
  - Monitor for recurrence using source IPs, payload patterns, endpoints, user agents, sessions, object access patterns, and TTPs.

> **Decision Point:**
> If exploitation resumes after recovery, reinstate containment and reassess for missed persistence or incomplete remediation.

## 7. Communication & Escalation

- **Internal Communication:**
  - Notify application owners, service owners, affected business units, security leadership, and engineering teams.
  - Use [SOP-002](../sops/SOP-002-incident-handoff-between-geos.md) for active incidents spanning shifts or geographic regions.
  - Notify affected users where action is required.
    - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **External Communication:**
  - Engage Legal/Privacy for customer data, regulated data, payment data, credential exposure, customer-impacting outage, or public vulnerability communication.
  - Coordinate customer, regulator, partner, media, and public messaging through Legal and Communications Lead.
    - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)

- **Escalation Criteria:**

  | Condition | Escalate To |
  |-----------|-------------|
  | Account/session/token compromise | [PB-004: Account Takeover](PB-004-account-takeover.md) |
  | Sensitive data exposure or exfiltration | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
  | Web shell, malware, or host/runtime compromise | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) |
  | Known vulnerability exploited in production | [PB-015: Active Exploitation](PB-015-active-exploitation.md) |
  | Cloud workload or control plane compromise | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
  | Application-layer denial of service | [PB-013: DDoS](PB-013-ddos.md) |
  | Critical customer, payment, authentication, or regulated-data impact | [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md) / Executive escalation |

## 8. Post-Incident Activities

- Conduct a PIR covering root cause, exploit path, affected endpoints/data, containment decisions, recovery timeline, and customer/service impact.
- Review detection gaps across WAF/CDN, application, API gateway, authentication, database, workload, and cloud telemetry.
- Complete web application hardening.
  - 📘 [RB-POST-004: Web Application Security Hardening](../runbooks/post-incident/RB-POST-004-web-application-security-hardening.md)
- Update detections, WAF rules, test cases, threat models, and this playbook where required.

## 9. References & Linked Resources

- **Playbooks:**
  - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
  - [PB-004: Account Takeover](PB-004-account-takeover.md)
  - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
  - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
  - [PB-013: DDoS](PB-013-ddos.md)
  - [PB-015: Active Exploitation](PB-015-active-exploitation.md)
  - [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md)

- **Runbooks:**
  - [RB-TRIAGE-012: Web Application Attack Triage](../runbooks/triage/RB-TRIAGE-012-web-application-attack-triage.md)
  - [RB-EVIDENCE-006: Web Application Log Acquisition](../runbooks/evidence/RB-EVIDENCE-006-web-application-log-acquisition.md)
  - [RB-ANALYSIS-044: Web Application Attack Analysis](../runbooks/analysis/RB-ANALYSIS-044-web-application-attack-analysis.md)
  - [RB-CONTAIN-016: Web Application Access Restriction](../runbooks/contain/RB-CONTAIN-016-web-application-access-restriction.md)
  - [RB-CONTAIN-012: Exploitation Surface Containment](../runbooks/contain/RB-CONTAIN-012-exploitation-surface-containment.md)
  - [RB-CONTAIN-014: Vulnerability Exposure Reduction](../runbooks/contain/RB-CONTAIN-014-vulnerability-exposure-reduction.md)
  - [RB-RECOVERY-007: Vulnerability Remediation Validation](../runbooks/recovery/RB-RECOVERY-007-vulnerability-remediation-validation.md)
  - [RB-POST-004: Web Application Security Hardening](../runbooks/post-incident/RB-POST-004-web-application-security-hardening.md)

- **SOPs:**
  - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
  - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
  - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
  - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

## 10. Appendices

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
