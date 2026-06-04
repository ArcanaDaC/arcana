# RB-ANALYSIS-022: Exfiltration Scope Expansion Hunt

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Exfiltration Scope Expansion Hunt | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial creation | |

## 1. Prerequisites

- Suspected or confirmed data exfiltration incident
- Completion of:
  - Outbound Traffic Analysis
  - Data Staging Investigation
  - Cloud Storage & SaaS Review
  - Sensitive Data Impact Assessment
- Access to SIEM
- Access to EDR telemetry
- Access to authentication logs
- Access to cloud audit logs
- Access to network telemetry
- Access to DLP telemetry (if available)
- Known indicators identified during the investigation
- Investigation timeline established

## 2. Step-by-Step Instructions

1. **Establish Hunt Scope**
   - Identify:
     - Affected users
     - Affected endpoints
     - Affected servers
     - Affected cloud workloads
     - Affected SaaS applications
   - Document the initial scope of the investigation.

2. **Identify Related Accounts**
   - Review:
     - Authentication activity
     - Shared credentials
     - Administrative relationships
     - Privileged access assignments
   - Identify additional accounts potentially involved in the activity.

3. **Identify Related Systems**
   - Investigate:
     - Systems accessed by affected users
     - Systems communicating with affected hosts
     - Shared file repositories
     - Shared cloud resources
   - Identify additional systems that may have been involved.

4. **Hunt for Similar Data Transfer Activity**
   - Search for:
     - Similar outbound destinations
     - Similar transfer volumes
     - Similar transfer methods
     - Similar cloud upload activity
   - Identify additional instances of suspicious behaviour.

5. **Review Historical Activity**
   - Expand the investigation window.
   - Review historical telemetry for:
     - Prior transfers
     - Prior staging activity
     - Prior authentication anomalies
     - Prior cloud sharing activity
   - Determine whether activity predates the initial alert.

6. **Identify Additional Data Sources**
   - Review:
     - File shares
     - Databases
     - Collaboration platforms
     - Cloud storage repositories
     - SaaS applications
   - Determine whether additional data sources may have been accessed.

7. **Investigate Additional Users**
   - Review activity from:
     - Administrators
     - Service accounts
     - Privileged users
     - Users interacting with affected assets
   - Identify additional users requiring investigation.

8. **Correlate Findings Across Data Sources**
   - Correlate:
     - Authentication activity
     - Endpoint activity
     - Network activity
     - Cloud activity
     - SaaS activity
   - Identify common indicators, timelines, and behaviours.

9. **Determine Expanded Scope**
   - Document:
     - Additional users identified
     - Additional systems identified
     - Additional datasets identified
     - Additional transfer activity identified
     - Additional exposure identified
   - Assess overall expansion of incident scope.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Update:
      - Incident severity
      - Impact assessment
      - Containment scope
      - Recovery planning
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all newly identified assets are documented.
- Ensure all newly identified users are documented.
- Document all newly identified datasets and repositories.
- Preserve all evidence supporting scope expansion findings.
- Update the incident timeline with newly discovered activity.
- Attach hunt results and supporting evidence to the incident record.
- Participate in containment, recovery, and post-incident activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
