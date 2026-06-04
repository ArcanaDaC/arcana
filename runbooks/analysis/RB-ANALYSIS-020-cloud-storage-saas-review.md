# RB-ANALYSIS-020: Cloud Storage & SaaS Review

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Cloud Storage & SaaS Review | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial creation | |

## 1. Prerequisites

- Suspected or confirmed data exfiltration incident
- Access to cloud provider audit logs
- Access to SaaS audit logs
- Access to cloud storage activity logs
- Access to Identity Provider (IdP) logs
- Access to SIEM
- Access to CASB tooling (if available)
- User accounts, hostnames, and assets identified during triage
- Investigation timeline established

## 2. Step-by-Step Instructions

1. **Identify Cloud and SaaS Services in Scope**
   - Identify:
     - Cloud storage platforms
     - SaaS applications
     - Collaboration platforms
     - File sharing services
   - Document all platforms associated with the investigation.

2. **Review User Authentication Activity**
   - Review:
     - Login events
     - Failed login attempts
     - MFA activity
     - Geographic anomalies
     - Impossible travel events
   - Identify suspicious authentication activity associated with affected users.

3. **Review File Upload Activity**
   - Investigate:
     - Large file uploads
     - Bulk upload activity
     - Unusual upload patterns
     - Uploads outside business hours
   - Document all suspicious file transfer activity.

4. **Review File Download Activity**
   - Identify:
     - Mass download activity
     - Unusual download locations
     - External access events
     - Bulk export activity
   - Determine whether data may have been collected for exfiltration.

5. **Review Sharing Activity**
   - Investigate:
     - Public sharing links
     - Anonymous sharing
     - External user access
     - Guest account access
     - Shared folders and repositories
   - Identify potential exposure paths.

6. **Review Third-Party Application Access**
   - Investigate:
     - OAuth applications
     - API integrations
     - Service accounts
     - Third-party connectors
   - Identify unauthorised or suspicious integrations.

7. **Review Administrative Activity**
   - Review:
     - Permission changes
     - Role assignments
     - Configuration modifications
     - Sharing policy changes
   - Determine whether access controls were modified to facilitate data access or transfer.

8. **Correlate with Endpoint and Network Activity**
   - Compare findings against:
     - Outbound Traffic Analysis
     - Data Staging Investigation
     - Authentication Log Analysis
   - Determine whether cloud or SaaS activity aligns with identified exfiltration behaviour.

9. **Determine Scope and Impact**
   - Identify:
     - Affected users
     - Affected applications
     - Affected datasets
     - External recipients
     - Potentially exposed information
   - Document findings and confidence level.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Escalate to:
      - Sensitive Data Impact Assessment
      - Exfiltration Scope Expansion Hunt
      - Containment activities
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all affected cloud and SaaS platforms are documented.
- Preserve relevant audit logs and artifacts.
- Document all external sharing activity.
- Document all identified third-party integrations.
- Record all affected users, applications, and datasets.
- Attach investigation findings to the incident record.
- Participate in subsequent containment and impact assessment activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
