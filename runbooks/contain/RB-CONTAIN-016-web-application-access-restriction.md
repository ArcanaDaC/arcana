# RB-CONTAIN-016: Web Application Access Restriction

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Web Application Access Restriction | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |
## 1. Prerequisites

- Application, API, route, endpoint, feature, tenant, or function requiring restriction identified
- Access to relevant application, WAF, CDN, API gateway, identity, or configuration controls
- Business-critical access requirements known
- Rollback method available
- Incident ticket or change record created

## 2. Step-by-Step Instructions

1. **Define Restriction Scope**
    - Identify the application, API, route, endpoint, tenant, feature, admin function, upload path, export path, or integration to restrict.
    - Record the reason for restriction and required time window.

2. **Identify Required Access**
    - Determine which users, services, source networks, methods, regions, tenants, or integrations must remain allowed.
    - Identify access that can be blocked, limited, or challenged.

3. **Select Restriction Method**
    - Choose the least disruptive effective control:
        - Disable route, feature, upload, export, or integration
        - Apply WAF, CDN, or API gateway rule
        - Require authentication or step-up authentication
        - Apply IP, ASN, geo, tenant, user, or service allowlist/denylist
        - Restrict HTTP methods, request size, file types, or high-risk parameters
        - Apply rate limits, bot controls, or request throttling
        - Remove admin interface from public exposure

4. **Record Current State**
    - Capture current routing, WAF/CDN/API gateway rules, feature flags, access policies, rate limits, and relevant application configuration.
    - Record rollback values before making changes.

5. **Apply Restriction**
    - Implement the selected restriction.
    - Keep the scope as narrow as possible.
    - Record exact rule, configuration, feature flag, route, or policy changed.

6. **Validate Restriction**
    - Confirm blocked or restricted access is no longer allowed.
    - Confirm required users, services, tenants, and business-critical flows still work.
    - Check for unintended outage or authentication failures.

7. **Monitor for Bypass**
    - Review logs for alternate routes, changed payloads, new source IPs, token reuse, method switching, rate-limit evasion, or tenant/object switching.
    - Adjust restriction if bypass attempts continue.

8. **Record Restriction Details**
    - Document restriction scope, method, timestamp, configuration change, validation result, expected duration, rollback condition, and known business impact.

9. **Review Continued Need**
    - Reassess whether the restriction is still required.
    - Remove, narrow, or replace temporary controls once durable remediation is complete.

10. **Restore Access**
    - Remove or reduce the restriction when criteria are met.
    - Validate normal functionality.
    - Record restoration time and final state.

## 3. Post-Action

- Confirm restriction remains effective and scoped appropriately.
- Record business impact, bypass attempts, and required follow-up changes.
- Preserve before/after configuration where applicable.

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
