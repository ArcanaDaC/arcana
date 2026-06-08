# PB-012: Third-Party Compromise

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-012: Third-Party Compromise | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    Provide a structured response for suspected or confirmed third-party compromise. Use this playbook to validate the report, assess exposure, restrict risky access, identify secondary impact, and restore trusted access safely.

- **Scope:**

    Applies to compromised vendors, suppliers, MSPs, SaaS providers, cloud providers, software dependencies, contractors, partners, and trusted integrations. Impact is not assumed; it must be confirmed through evidence.

## 2. Incident Identification & Criteria

**Incident Type:** Third-Party Compromise

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- A vendor, MSP, SaaS provider, cloud provider, supplier, or partner reports a breach or possible customer impact
- A third-party product, dependency, package, update, appliance, or managed service used by the organisation is compromised or exploited
- Third-party credentials, API keys, tokens, certificates, secrets, integrations, delegated access, or federation relationships are exposed or abused
- Threat intelligence or internal telemetry indicates trusted third-party access may have been used against organisational systems, data, or operations

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | Notification or advisory received; organisational exposure not confirmed |
| Sev 2 | Affected vendor, product, integration, or account is in use; no active abuse observed |
| Sev 1 | Confirmed third-party access, credential exposure, data access, privileged access, production impact, or active exploitation |
| Sev 0 | Widespread supply chain compromise, critical provider compromise, active attacker access, major customer impact, or enterprise-wide disruption |

## 3. Roles & Responsibilities

- **Incident Commander:** Sets severity, coordinates response, approves containment, and owns escalation decisions.
- **Incident Responder / Forensic Analyst:** Validates the report, scopes exposure, analyses activity, and preserves evidence.
- **Communications Lead:** Coordinates internal updates, vendor communications, and affected-user messaging.
- **Other Roles:**
    - **Vendor / Third-Party Owner:** Confirms business relationship, services used, access paths, and vendor contacts.
    - **Identity & Access Team:** Reviews SSO, federation, MFA, accounts, tokens, API keys, and privileged roles.
    - **Cloud / SaaS / Platform Teams:** Review integrations, audit logs, service accounts, and workload exposure.
    - **Application / Service Owners:** Validate affected dependencies, data access, business impact, and recovery needs.
    - **Legal / Compliance / Vendor Risk:** Assess contractual, regulatory, customer, partner, and vendor-risk obligations.

## 4. Initial Actions

- **Immediate Steps:**
    - Validate notification source, affected service, scope, and urgency before taking disruptive action.
        - 📘 [RB-TRIAGE-004: Third-Party Notification Validation](../runbooks/triage/RB-TRIAGE-004-third-party-notification-validation.md)
    - Identify the affected vendor, product, service, integration, account, or dependency.
    - Confirm whether the organisation uses it and identify the internal business owner.
    - Engage IR leadership, vendor owner, identity/platform owners, and Legal as needed.
        - 📘 [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)

    > **Decision Point:**
    > - If the organisation does not use the affected vendor, product, service, or integration → document evidence and close or downgrade.
    > - If the organisation uses it → continue to exposure assessment.
    > - If active abuse is suspected or identified → begin containment in parallel.

## 5. Investigation & Analysis
> **Common Failure Modes**
> - Assuming third-party compromise automatically means internal compromise
> - Assuming no internal impact exists because no initial indicators were found
> - Missing delegated access, service accounts, OAuth apps, API keys, or stale vendor accounts
> - Restoring trust before vendor remediation and internal exposure validation are complete
> - Failing to assess downstream dependencies, customer impact, or delayed attacker activity

- **Evidence Collection:**
    - Collect vendor notices, advisories, IOCs, affected versions, timelines, and contacts.
    - Collect relevant logs and inventory for affected vendors, products, accounts, integrations, keys, data stores, and connected systems.

- **Analysis Steps:**
    - Determine what access the third party has to systems, data, identity, production, source code, CI/CD, or administration.
        - 📘 [RB-ANALYSIS-027: Third-Party Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-027-third-party-exposure-assessment.md)
    - Assess affected products, versions, dependencies, deployment footprint, downstream dependencies, and attack paths.
        - 📘 [RB-ANALYSIS-028: Supply Chain Impact Analysis](../runbooks/analysis/RB-ANALYSIS-028-supply-chain-impact-analysis.md)
    - Review vendor-related SSO, federation, VPN, API, service account, and privileged login activity.
        - 📘 [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - Review privileged third-party accounts, delegated admin, OAuth apps, API keys, and managed service tooling.
        - 📘 [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
    - Identify related accounts, integrations, service accounts, secrets, systems, and business units with shared exposure.
    - Review SaaS, cloud storage, file access, and integration activity for sensitive data access.
        - 📘 [RB-ANALYSIS-020: Cloud Storage & SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)
        - 📘 [RB-ANALYSIS-021: Sensitive Data Impact Assessment](../runbooks/analysis/RB-ANALYSIS-021-sensitive-data-impact-assessment.md)

    > **Decision Point:**
    > Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
    > - If account compromise or credential abuse is suspected or identified → execute [PB-004: Account Takeover](PB-004-account-takeover.md) concurrently.
    > - If data exposure, staging, or exfiltration is suspected or identified → execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) concurrently.
    > - If cloud compromise is suspected or identified → execute [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) concurrently.
    > - If malware is suspected or identified → execute [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) concurrently.
    > - If privilege escalation is suspected or identified → execute [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) concurrently.
    > - If lateral movement is suspected or identified → execute [PB-010: Lateral Movement](PB-010-lateral-movement.md) concurrently.

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Restrict exposed or unnecessary third-party accounts, delegated roles, service accounts, OAuth apps, API keys, tokens, VPN access, remote support tooling, and integrations.
        - 📘 [RB-CONTAIN-008: Third-Party Access Restriction](../runbooks/contain/RB-CONTAIN-008-third-party-access-restriction.md)
    - Lock compromised accounts and revoke exposed sessions or tokens.
        - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
        - 📘 [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - Block outbound transfers, attacker infrastructure, or malicious update paths when active abuse is observed.
        - 📘 [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
    - Reduce exposure for affected third-party software, appliances, integrations, or public-facing services.
        - 📘 [RB-CONTAIN-014: Vulnerability Exposure Reduction](../runbooks/contain/RB-CONTAIN-014-vulnerability-exposure-reduction.md)

- **Eradication Steps:**
    - Remove stale vendor accounts, unused integrations, exposed secrets, overprivileged roles, and untrusted packages.
    - Rotate credentials, API keys, certificates, service account secrets, signing keys, webhook secrets, and tokens.
    - Patch, upgrade, rebuild, or replace affected third-party software and dependencies.

- **Recovery Steps:**
    - Restore third-party access only after remediation is validated, exposure is resolved, credentials are rotated, and monitoring is active.
        - 📘 [RB-RECOVERY-005: Third-Party Trust Restoration](../runbooks/recovery/RB-RECOVERY-005-third-party-trust-restoration.md)
    - Validate business functionality after restoring approved integrations.
    - Monitor for delayed activity, credential reuse, malicious updates, API abuse, and abnormal vendor account activity.

    > **Decision Point:**
    > Do not restore trust because the vendor says the incident is closed. Restore only after internal exposure is assessed, remediation evidence is sufficient, and business owners approve remaining risk.

## 7. Communication & Escalation

- **Internal Communication:**
    - Notify security leadership, vendor owners, service owners, identity/platform teams, vendor risk, and affected stakeholders.
    - Use geo handoff when the incident spans response shifts.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - Notify affected users if credentials, MFA, access, device posture, or availability is impacted.
        - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **External Communication:**
    - Engage Legal/Privacy for contractual, customer, regulator, partner, law enforcement, and executive communication decisions.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - Route vendor communications through the Incident Commander, vendor owner, Legal, and Communications Lead.
        - 📘 [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Account compromise or credential abuse suspected or identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
    | Data exposure, staging, or exfiltration suspected or identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
    | Cloud compromise suspected or identified | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
    | Malware suspected or identified | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) |
    | Privilege escalation suspected or identified | [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) |
    | Lateral movement suspected or identified | [PB-010: Lateral Movement](PB-010-lateral-movement.md) |
    | Widespread supply chain compromise, critical provider compromise, or major business impact | [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a PIR covering notification handling, exposure, integrations, access restrictions, trust restoration, communications, and evidence gaps.
    - Review vendor risk posture, contractual requirements, access review cadence, monitoring, integration inventory, and dependency management.

- **Documentation Updates:**
    - Update this playbook, vendor inventory, integration inventory, access review procedures, detections, and trust restoration criteria.

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    - [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
    - [PB-010: Lateral Movement](PB-010-lateral-movement.md)
    - [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)

- **Runbooks:**
    - [RB-TRIAGE-004: Third-Party Notification Validation](../runbooks/triage/RB-TRIAGE-004-third-party-notification-validation.md)
    - [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
    - [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
    - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
    - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
    - [RB-ANALYSIS-020: Cloud Storage & SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)
    - [RB-ANALYSIS-021: Sensitive Data Impact Assessment](../runbooks/analysis/RB-ANALYSIS-021-sensitive-data-impact-assessment.md)
    - [RB-ANALYSIS-027: Third-Party Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-027-third-party-exposure-assessment.md)
    - [RB-ANALYSIS-028: Supply Chain Impact Analysis](../runbooks/analysis/RB-ANALYSIS-028-supply-chain-impact-analysis.md)
    - [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
    - [RB-CONTAIN-008: Third-Party Access Restriction](../runbooks/contain/RB-CONTAIN-008-third-party-access-restriction.md)
    - [RB-CONTAIN-014: Vulnerability Exposure Reduction](../runbooks/contain/RB-CONTAIN-014-vulnerability-exposure-reduction.md)
    - [RB-RECOVERY-005: Third-Party Trust Restoration](../runbooks/recovery/RB-RECOVERY-005-third-party-trust-restoration.md)

- **SOPs:**
    - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)
    - [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)

## 10. Appendices
## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
