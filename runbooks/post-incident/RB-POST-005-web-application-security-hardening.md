# RB-POST-005: Web Application Security Hardening

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Web Application Security Hardening | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Web application incident contained and recovered
- Root cause or best current hypothesis documented
- Remediation items tracked

## 2. Step-by-Step Instructions

1. **Review Root Cause**
   - Document exploited weakness, affected endpoint, vulnerable component, configuration issue, or access-control failure.

2. **Validate Fixes**
   - Confirm vulnerable code, dependencies, routes, access controls, secrets, and configuration have been remediated.

3. **Harden Application Controls**
   - Improve input validation, output encoding, authentication, authorisation, session management, rate limits, file upload controls, and error handling.

4. **Harden Edge Controls**
   - Review WAF, CDN, API gateway, bot protection, rate limits, security headers, TLS, and runtime detections.

5. **Rotate Secrets**
   - Rotate exposed or potentially exposed API keys, signing keys, session secrets, database credentials, and service credentials.

6. **Reduce Trust and Access**
   - Remove unnecessary integrations, unused endpoints, test routes, debug features, exposed admin panels, and excessive service account permissions.

7. **Improve Logging and Detection**
   - Ensure logs capture request IDs, user IDs, tenant IDs, source IPs, auth decisions, object access, admin actions, and security errors.
   - Add detections for the observed attack and close variants.

8. **Validate Effectiveness**
   - Retest the exploited path and similar paths.
   - Confirm scans, tests, and telemetry show no continued exposure or exploitation.

9. **Update Documentation**
   - Update playbooks, runbooks, threat models, test cases, dashboards, and service documentation where required.

## 3. Post-Action

- Record completed hardening, validation evidence, residual risk, and outstanding actions.
- Track remaining remediation to closure.
- Feed lessons into secure SDLC, threat modeling, detection engineering, and vulnerability management.

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
