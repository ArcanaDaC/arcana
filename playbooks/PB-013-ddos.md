# PB-013: Distributed Denial of Service (DDoS)

## Overview

This playbook outlines the response process for Distributed Denial of Service (DDoS) attacks targeting internet-facing infrastructure, applications, services, networks, APIs, cloud environments, and supporting systems.

This playbook is intended for:

- Volumetric DDoS attacks
- Protocol attacks
- Application-layer attacks
- HTTP flood attacks
- API abuse
- DNS amplification attacks
- Reflection attacks
- Cloud service disruption
- Availability-focused attacks

---

## Status

Live

---

## Warning

Do NOT assume service outages are caused by DDoS activity.

Likewise, do NOT assume a DDoS attack is solely an availability event.

DDoS attacks may be used to:

- Distract defenders
- Mask data exfiltration
- Conceal intrusion activity
- Impact business operations
- Extort organisations
- Support broader attack campaigns

Investigations should consider secondary attacker objectives.

---

## Immediate Emergency Actions

1. Confirm service degradation or outage.
2. Notify Incident Response leadership.
3. Engage network and infrastructure teams.
4. Preserve relevant logs and telemetry.
5. Identify impacted services.
6. Assess business impact.
7. Activate DDoS mitigation capabilities.

---

## Linked Runbooks

### Triage

- [RB-TRIAGE-005 DDoS Alert Validation](../runbooks/triage/RB-TRIAGE-005-ddos-alert-validation.md)

### Analysis

- [RB-ANALYSIS-029 DDoS Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-029-ddos-traffic-analysis.md)
- [RB-ANALYSIS-030 Service Impact Assessment](../runbooks/analysis/RB-ANALYSIS-030-service-impact-assessment.md)
- [RB-ANALYSIS-031 DDoS Attribution & Threat Assessment](../runbooks/analysis/RB-ANALYSIS-031-ddos-attribution-threat-assessment.md)

### Containment

- [RB-CONTAIN-009 DDoS Mitigation Activation](../runbooks/contain/RB-CONTAIN-009-ddos-mitigation-activation.md)
- [RB-CONTAIN-010 Traffic Filtering & Rate Limiting](../runbooks/contain/RB-CONTAIN-010-traffic-filtering-rate-limiting.md)

### Recovery

- [RB-RECOVERY-006 Service Availability Restoration](../runbooks/recovery/RB-RECOVERY-006-service-availability-restoration.md)

### Post-Incident

- [RB-POST-003: DDoS Resilience Improvement](../runbooks/post-incident/RB-POST-003-ddos-resilience-improvement.md)

---

## Trigger Conditions

Initiate this playbook when any of the following occur:

- DDoS alerts generated
- Significant increase in inbound traffic
- Service availability degradation
- Network saturation observed
- API exhaustion identified
- Application performance degradation
- CDN or cloud provider DDoS notifications received
- Extortion demands involving DDoS threats received

---

## Severity Guidelines

| Severity | Description |
|----------|------------|
| Sev3 | Localised performance degradation |
| Sev2 | Service disruption affecting a limited customer population |
| Sev1 | Major outage affecting critical business services |
| Sev0 | Widespread outage impacting multiple critical services or business operations |

---

## Objectives

- Confirm DDoS activity
- Identify affected services
- Maintain business availability
- Activate mitigation controls
- Minimise customer impact
- Identify secondary attacker objectives
- Improve future resilience

---

## Required Inputs

- Network telemetry
- Firewall logs
- CDN logs
- WAF logs
- Load balancer logs
- Cloud telemetry
- Service health metrics
- Application performance metrics

---

## Playbook Workflow

### 1. Validate DDoS Activity

Runbook:

- [RB-TRIAGE-005 DDoS Alert Validation](../runbooks/triage/RB-TRIAGE-005-ddos-alert-validation.md)

Actions:

- Validate alert legitimacy
- Confirm abnormal traffic patterns
- Identify affected services
- Establish attack start time
- Determine initial severity

---

### 2. Analyse Traffic Characteristics

Runbook:

- [RB-ANALYSIS-029 DDoS Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-029-ddos-traffic-analysis.md)

Actions:

- Identify attack type
- Identify source distribution
- Review protocols involved
- Assess traffic volume
- Identify amplification indicators

---

### 3. Assess Service Impact

Runbook:

- [RB-ANALYSIS-030 Service Impact Assessment](../runbooks/analysis/RB-ANALYSIS-030-service-impact-assessment.md)

Actions:

- Identify impacted systems
- Assess customer impact
- Assess business impact
- Assess operational impact
- Determine restoration priorities

---

### 4. Activate Mitigation Controls

Runbook:

- [RB-CONTAIN-009 DDoS Mitigation Activation](../runbooks/contain/RB-CONTAIN-009-ddos-mitigation-activation.md)

Actions:

- Activate DDoS protection services
- Engage CDN providers
- Engage cloud providers
- Engage ISP support where required
- Enable mitigation profiles

---

### 5. Filter Malicious Traffic

Runbook:

- [RB-CONTAIN-010 Traffic Filtering & Rate Limiting](../runbooks/contain/RB-CONTAIN-010-traffic-filtering-rate-limiting.md)

Actions:

- Implement filtering rules
- Apply rate limits
- Block malicious traffic sources
- Protect critical services
- Monitor mitigation effectiveness

---

### 6. Assess Secondary Attacker Objectives

Runbook:

- [RB-ANALYSIS-031 DDoS Attribution & Threat Assessment](../runbooks/analysis/RB-ANALYSIS-031-ddos-attribution-threat-assessment.md)

Actions:

- Review extortion indicators
- Review concurrent security alerts
- Review authentication activity
- Review data access activity
- Assess broader attack objectives

Decision Point:

If evidence of additional attacker activity exists:

Activate:

- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

---

### 7. Monitor Mitigation Effectiveness

Actions:

- Review traffic trends
- Monitor service availability
- Monitor customer impact
- Adjust controls as required
- Validate service stability

---

### 8. Coordinate Communications

Actions:

- Notify leadership
- Notify business stakeholders
- Notify affected customers where appropriate
- Coordinate vendor communications
- Coordinate executive updates

---

### 9. Restore Service Availability

Runbook:

- [RB-RECOVERY-006 Service Availability Restoration](../runbooks/recovery/RB-RECOVERY-006-service-availability-restoration.md)

Actions:

- Validate service health
- Remove temporary controls where appropriate
- Restore normal operations
- Confirm customer impact resolution

---

### 10. Improve DDoS Resilience

Runbook:

- [RB-POST-003: DDoS Resilience Improvement](../runbooks/post-incident/RB-POST-003-ddos-resilience-improvement.md)

Actions:

- Review mitigation effectiveness
- Review detection effectiveness
- Review provider performance
- Improve resilience controls
- Document lessons learned

---

## Playbook Relationships

DDoS attacks may be standalone availability events or part of broader attack campaigns.

Additional playbooks should be activated when evidence supports them.

### Common Escalations

| Evidence Identified | Activate Playbook |
|---|---|
| Account compromise | PB-004 Account Takeover |
| Data exposure | PB-005 Data Exfiltration |
| Cloud compromise | PB-007 Cloud Compromise |
| Privilege escalation | PB-009 Privilege Escalation |
| Lateral movement | PB-010 Lateral Movement |

### Operational Guidance

When additional attacker activity is identified:

- Continue this playbook
- Activate related playbooks
- Execute playbooks concurrently
- Close playbooks independently

---

## Escalation Paths

| Condition | Escalate To |
|----------|------------|
| Account compromise | PB-004 Account Takeover |
| Data exposure | PB-005 Data Exfiltration |
| Cloud compromise | PB-007 Cloud Compromise |
| Privilege escalation | PB-009 Privilege Escalation |
| Lateral movement | PB-010 Lateral Movement |

---

## Outputs

- DDoS assessment
- Impact assessment
- Mitigation actions
- Service restoration status
- Attribution findings
- Lessons learned
- Resilience improvement recommendations

---

## Common Failure Modes

- Misidentifying outages as DDoS activity
- Delaying mitigation activation
- Failing to assess secondary attacker objectives
- Overblocking legitimate traffic
- Poor stakeholder communication
- Insufficient monitoring during recovery

---

## Automation Opportunities

- DDoS detection
- Traffic classification
- Automated mitigation activation
- Dynamic rate limiting
- Service health monitoring
- Stakeholder notification workflows

---

## Related

- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
