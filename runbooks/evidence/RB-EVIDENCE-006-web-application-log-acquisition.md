# RB-EVIDENCE-006: Web Application Log Acquisition

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Web Application Log Acquisition | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Affected application, API, route, hostname, tenant, or endpoint identified
- Incident time window defined in UTC
- Access to application, edge, auth, runtime, and SIEM logs
- Evidence storage location available
- Incident ticket created

## 2. Step-by-Step Instructions

> **Common Failure Modes**
> - Collecting only WAF alerts
> - Missing API gateway, CDN, identity, or application logs
> - Letting short-retention logs rotate
> - Losing request IDs, session IDs, user IDs, or object IDs needed for correlation

1. **Confirm Scope**
    - Confirm affected application, environment, routes, APIs, tenants, and time window.

2. **Collect Edge Logs**
    - Export WAF, CDN, reverse proxy, load balancer, firewall, IDS/IPS, DNS, and NetFlow logs.
    - Preserve source IP, user agent, method, URI, query string, response code, bytes, rule ID, and action.

3. **Collect Application Logs**
    - Export application, API gateway, access, error, audit, and framework security logs.
    - Preserve request IDs, user IDs, tenant IDs, session IDs, auth outcomes, object IDs, and application errors.

4. **Collect Auth and Session Logs**
    - Export SSO, local auth, MFA, token, API key, and session activity for affected users or services.

5. **Collect Runtime Logs**
    - Export web server, container, serverless, database, cache, queue, deployment, and cloud control plane logs as applicable.

6. **Preserve Application State**
    - Capture relevant configuration, WAF rules, routes, access controls, feature flags, deployments, suspicious uploads, web shells, and modified content.

7. **Package Evidence**
    - Store exports by source and time range.
    - Hash exported files where applicable.
    - Record operator, export method, query, location, and hash.

8. **Validate Completeness**
    - Confirm expected sources and time ranges are present.
    - Document gaps, sampling, missing logs, disabled logging, or retention limits.

## 3. Post-Action

- Transfer evidence to approved storage.
- Record evidence metadata and known gaps in the incident ticket.
- Record evidence readiness and location in the incident ticket.

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
