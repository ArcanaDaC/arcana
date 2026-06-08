# RB-TRIAGE-012: Web Application Attack Triage

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Web Application Attack Triage | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Web, API, WAF, CDN, IDS/IPS, or SIEM alert
- Access to application, edge, auth, and SIEM logs
- Affected application, endpoint, or API identified
- Incident ticket created

## 2. Step-by-Step Instructions

1. **Capture Alert Details**
    - Record alert source, timestamp, affected app, endpoint, source IP, user agent, request path, payload indicators, and current severity.

2. **Validate Application Context**
    - Identify business criticality, production status, internet exposure, and data sensitivity.

3. **Classify Attack Type**
    - Identify whether activity indicates injection, access control abuse, file upload abuse, path traversal, API abuse, credential stuffing, session abuse, denial of service, or known vulnerability exploitation.

4. **Assess Exploitation Status**
    - Classify as scanning, attempted exploitation, suspected exploitation, confirmed exploitation, or ongoing attacker activity.

5. **Assess Immediate Impact**
    - Check for unauthorised access, data access, privilege escalation, web shell, command execution, service disruption, or tampering.

6. **Check Active Risk**
    - Determine whether malicious requests, attacker sessions, tokens, API keys, or uploaded artifacts remain active.

7. **Assign Initial Severity**
    - Use application criticality, exploitation status, data sensitivity, active attacker presence, and service impact.

8. **Identify Required Evidence**
    - List required web, API, WAF/CDN, authentication, and infrastructure logs for follow-on collection.
    - Record sources, retention limits, and urgency.

9. **Record Triage Result**
    - Document verdict, severity, suspected attack type, affected assets, indicators, evidence needs, and open questions.

## 3. Post-Action

- Ensure triage findings, evidence needs, affected assets, severity rationale, indicators, and open questions are documented.

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
