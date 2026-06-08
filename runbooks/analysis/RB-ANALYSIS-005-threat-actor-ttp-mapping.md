# RB-ANALYSIS-005: Threat Actor TTP Mapping

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Threat Actor TTP Mapping | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |


## 1. Prerequisites
- Incident timeline and IOCs collected so far
- Payload or malware analysis findings
- Access to a threat intelligence platform or vendor reporting
- Access to SIEM and EDR to review alerts, detections, and coverage
- MITRE ATT&CK framework reference

## 2. Step-by-Step Instructions

1. **Review Observed Techniques**
	- Identify initial access methods
	- Document credential access techniques
	- Document lateral movement methods
	- Identify persistence mechanisms
	- Document defence evasion techniques observed
	- Document exfiltration behaviour

2. **Map TTPs to MITRE ATT&CK**
	- Document technique IDs
	- Record sub-techniques
	- Document observed behaviours

3. **Correlate with Known Threat Actors**
	- Compare observed TTPs against public threat intelligence reporting
	- Cross-reference threat intel feeds for matching indicators or behaviour
	- Identify known infrastructure overlaps (IPs, domains, tooling, certificates)
	- Assess whether observed behaviour matches a known threat actor, cluster, or campaign

4. **Identify Detection Gaps**
	- Determine missed detections
	- Document delayed alerts
	- Identify visibility gaps
	- Assess logging deficiencies
	- Identify detection opportunities

## 3. Post-Action
- Document findings and identified TTPs within the incident ticket.
- Hand off detection gaps and improvement recommendations to detection engineering for follow-up
- Update threat intelligence platforms with newly identified IOCs, TTPs, and infrastructure

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.