# RB-ANALYSIS-044: Web Application Attack Analysis

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Web Application Attack Analysis | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Web Application Attack Triage completed
- Relevant application, edge, auth, infrastructure, and database logs collected
- Affected app, endpoints, users, and time window identified
- Evidence locations documented

## 2. Step-by-Step Instructions

1. **Build Timeline**
   - Correlate edge, application, API gateway, authentication, infrastructure, and database logs.
   - Identify reconnaissance, first exploit attempt, first suspicious success, follow-on activity, and last activity.

2. **Classify Attack Path**
   - Identify the primary technique: injection, broken access control, session abuse, credential stuffing, file upload abuse, path traversal, API abuse, SSRF, deserialisation, or known CVE exploitation.

3. **Confirm Exploitation Status**
   - Classify as no evidence, suspected exploitation, confirmed exploitation, or ongoing exploitation.
   - Record supporting evidence.

4. **Identify Affected Identities**
   - Review user IDs, session IDs, API keys, OAuth tokens, cookies, JWTs, and service accounts tied to suspicious activity.

5. **Assess Data Impact**
   - Identify records, objects, files, exports, API responses, and database queries accessed during the attack window.
   - Flag customer, payment, credential, regulated, or proprietary data.

6. **Review Changes and Persistence**
   - Check deployments, configuration changes, admin actions, permission changes, uploaded files, web shells, jobs, and secret access.

7. **Correlate Adjacent Activity**
   - Review host, container, serverless, cloud control plane, and identity activity where runtime or credential compromise is suspected.

8. **Scope Similar Activity**
   - Search for the same IPs, user agents, payloads, endpoints, object access patterns, accounts, and tokens across apps and historical logs.

9. **Document Findings**
   - Record attack type, timeline, affected endpoints, affected users, affected data, indicators, confidence level, and business impact.

10. **Record Required Follow-On Actions**
    - Flag account compromise, data exposure, exfiltration, known vulnerability exploitation, or active attacker presence.
    - Document containment recommendations and unresolved questions in the incident record.

## 3. Post-Action

- Attach timeline, findings, affected endpoints, indicators, and evidence references to the incident record.
- Document containment, remediation, monitoring, and detection gaps identified during analysis.

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
