# PB-013: Distributed Denial of Service (DDoS)

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-013: Distributed Denial of Service (DDoS) | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    Provide a structured response for suspected or confirmed DDoS attacks. Use this playbook to validate service impact, analyse traffic, activate mitigation, restore availability, and assess whether the DDoS is masking broader attacker activity.

- **Scope:**

    Applies to volumetric, protocol, application-layer, DNS, API, CDN, cloud, and network availability attacks affecting internet-facing infrastructure, applications, services, and supporting systems.

## 2. Incident Identification & Criteria

**Incident Type:** Distributed Denial of Service (DDoS)

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- DDoS, CDN, cloud, ISP, WAF, or monitoring alert indicates abnormal traffic or service degradation
- Internet-facing services, APIs, DNS, applications, or networks experience unexplained availability impact
- Network saturation, connection exhaustion, API exhaustion, HTTP flood, reflection, or amplification activity is observed
- Extortion demand or threat intelligence indicates an active or imminent DDoS threat

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | Suspicious traffic increase or minor degradation; no confirmed customer or critical service impact |
| Sev 2 | Confirmed DDoS activity affecting one service, region, or non-critical business function |
| Sev 1 | Sustained attack causing material customer impact, critical service degradation, or provider escalation |
| Sev 0 | Major outage, multi-service impact, extortion-linked attack, or DDoS activity masking broader compromise |

## 3. Roles & Responsibilities

- **Incident Commander:** Sets severity, coordinates response, approves mitigation and escalation decisions, and owns stakeholder updates.
- **Incident Responder / Network Analyst:** Validates DDoS activity, analyses traffic, tracks indicators, and monitors for secondary attacker objectives.
- **Communications Lead:** Coordinates internal, executive, customer, provider, and legal communications.
- **Other Roles:**
    - **Network / Infrastructure Team:** Implements network controls, routing changes, filtering, and provider coordination.
    - **Application / Service Owners:** Validate service health, customer impact, dependencies, and restoration success.
    - **Cloud / CDN / WAF Owners:** Activate mitigation, rate limiting, scaling, edge filtering, and provider support.
    - **Legal / Compliance:** Reviews extortion, customer impact, regulator, contractual, or law enforcement considerations.

## 4. Initial Actions

- **Immediate Steps:**
    - Validate that degradation is caused by abnormal traffic, not routine outage, deployment failure, capacity issue, or provider fault.
        - 📘 [RB-TRIAGE-005: DDoS Alert Validation](../runbooks/triage/RB-TRIAGE-005-ddos-alert-validation.md)
    - Identify affected services, regions, users, networks, APIs, and business owners.
    - Preserve traffic, CDN, WAF, firewall, load balancer, DNS, cloud, application, and service health telemetry.
    - Engage IR leadership, network/infrastructure teams, application owners, and provider contacts as needed.
        - 📘 [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)

    > **Decision Point:**
    > - If service impact is not caused by DDoS activity → document evidence and route to the appropriate operational incident process.
    > - If DDoS activity is suspected or confirmed → continue analysis and prepare mitigation.
    > - If customer, critical service, or extortion impact exists → escalate severity and begin communications in parallel.

## 5. Investigation & Analysis

- **Evidence Collection:**
    - Collect network, CDN, WAF, firewall, DNS, load balancer, cloud, application, service health, and provider telemetry.
    - Capture attack timeline, impacted services, source distribution, traffic characteristics, mitigations applied, and business impact.

- **Analysis Steps:**
    - Classify attack type, traffic volume, source distribution, targeted assets, protocols, payload patterns, and amplification/reflection indicators.
        - 📘 [RB-ANALYSIS-029: DDoS Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-029-ddos-traffic-analysis.md)
    - Assess service, customer, operational, infrastructure, and dependency impact.
        - 📘 [RB-ANALYSIS-030: DDoS Service Impact Assessment](../runbooks/analysis/RB-ANALYSIS-030-ddos-service-impact-assessment.md)
    - Assess extortion indicators, threat intelligence, attribution signals, targeting significance, and secondary attack objectives.
        - 📘 [RB-ANALYSIS-031: DDoS Attribution & Threat Assessment](../runbooks/analysis/RB-ANALYSIS-031-ddos-attribution-threat-assessment.md)
    - Monitor for concurrent security alerts, authentication anomalies, data access, malware, cloud control plane activity, and intrusion indicators.

    > **Decision Point:**
    > Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
    > - If account compromise or credential abuse is suspected or identified → execute [PB-004: Account Takeover](PB-004-account-takeover.md) concurrently.
    > - If data exposure, staging, or exfiltration is suspected or identified → execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) concurrently.
    > - If cloud compromise is suspected or identified → execute [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) concurrently.
    > - If malware or suspicious execution is suspected or identified → execute [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) or [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) concurrently.
    > - If privilege escalation is suspected or identified → execute [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) concurrently.
    > - If lateral movement is suspected or identified → execute [PB-010: Lateral Movement](PB-010-lateral-movement.md) concurrently.

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Activate approved DDoS mitigation services, provider protections, CDN/WAF controls, scrubbing, traffic rerouting, or emergency protection modes.
        - 📘 [RB-CONTAIN-009: DDoS Mitigation Activation](../runbooks/contain/RB-CONTAIN-009-ddos-mitigation-activation.md)
    - Apply traffic filtering, source blocking, protocol filtering, geo controls, application-layer controls, and rate limits where appropriate.
        - 📘 [RB-CONTAIN-010: Traffic Filtering & Rate Limiting](../runbooks/contain/RB-CONTAIN-010-traffic-filtering-rate-limiting.md)
    - Protect critical services first and avoid overblocking legitimate customer traffic.

- **Eradication Steps:**
    - Remove or disable malicious rules, abusive clients, exposed endpoints, misconfigurations, or vulnerable services contributing to attack effectiveness.
    - Tune filtering, rate limiting, caching, autoscaling, DNS, CDN, and WAF controls based on observed traffic.
    - Coordinate with providers to block attacker infrastructure and adjust mitigation profiles.

- **Recovery Steps:**
    - Restore normal service availability, validate customer impact resolution, and remove temporary controls only after attack traffic stabilises.
        - 📘 [RB-RECOVERY-006: Service Availability Restoration](../runbooks/recovery/RB-RECOVERY-006-service-availability-restoration.md)
    - Monitor service stability, legitimate traffic, error rates, latency, and provider status during recovery.

    > **Decision Point:**
    > If service degradation returns after controls are relaxed, re-enable mitigation, preserve new telemetry, and return to Investigation & Analysis.

## 7. Communication & Escalation

- **Internal Communication:**
    - Notify security leadership, network/infrastructure owners, application owners, service owners, support teams, and business stakeholders.
    - Use geo handoff when the incident spans response shifts.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)

- **External Communication:**
    - Coordinate provider, customer, legal, executive, and public communications through approved communication processes.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
        - 📘 [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Account compromise or credential abuse suspected or identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
    | Data exposure, staging, or exfiltration suspected or identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
    | Cloud compromise suspected or identified | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
    | Malware or suspicious execution suspected or identified | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) / [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) |
    | Privilege escalation suspected or identified | [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) |
    | Lateral movement suspected or identified | [PB-010: Lateral Movement](PB-010-lateral-movement.md) |
    | Major outage, extortion, or multi-service business impact | [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a PIR covering detection timing, traffic classification, mitigation speed, provider performance, communication timing, customer impact, and recovery decisions.
    - Review whether DDoS activity masked intrusion, data access, account abuse, cloud compromise, or other concurrent attacker objectives.

- **Documentation Updates:**
    - Update detection logic, runbooks, provider contacts, escalation paths, network diagrams, rate-limit policies, and mitigation profiles.
    - Track resilience improvements and service hardening actions.
        - 📘 [RB-POST-003: DDoS Resilience Improvement](../runbooks/post-incident/RB-POST-003-ddos-resilience-improvement.md)

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    - [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
    - [PB-010: Lateral Movement](PB-010-lateral-movement.md)
    - [PB-011: Suspicious Execution](PB-011-suspicious-execution.md)
    - [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md)

- **Runbooks:**
    - [RB-TRIAGE-005: DDoS Alert Validation](../runbooks/triage/RB-TRIAGE-005-ddos-alert-validation.md)
    - [RB-ANALYSIS-029: DDoS Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-029-ddos-traffic-analysis.md)
    - [RB-ANALYSIS-030: DDoS Service Impact Assessment](../runbooks/analysis/RB-ANALYSIS-030-ddos-service-impact-assessment.md)
    - [RB-ANALYSIS-031: DDoS Attribution & Threat Assessment](../runbooks/analysis/RB-ANALYSIS-031-ddos-attribution-threat-assessment.md)
    - [RB-CONTAIN-009: DDoS Mitigation Activation](../runbooks/contain/RB-CONTAIN-009-ddos-mitigation-activation.md)
    - [RB-CONTAIN-010: Traffic Filtering & Rate Limiting](../runbooks/contain/RB-CONTAIN-010-traffic-filtering-rate-limiting.md)
    - [RB-RECOVERY-006: Service Availability Restoration](../runbooks/recovery/RB-RECOVERY-006-service-availability-restoration.md)
    - [RB-POST-003: DDoS Resilience Improvement](../runbooks/post-incident/RB-POST-003-ddos-resilience-improvement.md)

- **SOPs:**
    - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-005: Vendor Communication During a Security Incident](../sops/SOP-005-vendor-communication.md)

## 10. Appendices

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
