# RB-ANALYSIS-035: Affected Asset Identification

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Affected Asset Identification | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Confirmed exploitation activity
- Access to SIEM
- Access to EDR
- Access to asset inventory
- Access to authentication logs
- Access to network telemetry

## 2. Step-by-Step Instructions

1. **Identify Initial Affected Asset**
    - Confirm the originally affected system.
    - Document ownership and business function.

2. **Review Related Connections**
    - Review:
        - Network communications
        - Authentication relationships
        - Administrative access
    - Identify related assets.

3. **Identify Additional Hosts**
    - Search for:
        - Similar indicators
        - Similar activity
        - Related communications
    - Document findings.

4. **Review Authentication Activity**
    - Identify:
        - Shared accounts
        - Administrative access
        - Lateral movement indicators
    - Document findings.

5. **Review Cloud and SaaS Activity**
    - Identify:
        - Connected assets
        - Cloud resources
        - SaaS resources
    - Document findings.

6. **Review Asset Inventory**
    - Identify:
        - Asset owners
        - Business units
        - Criticality ratings
    - Document findings.

7. **Correlate Findings**
    - Correlate:
        - Endpoint telemetry
        - Authentication activity
        - Network activity
    - Determine full affected scope.

8. **Assess Business Impact**
    - Identify:
        - Critical systems
        - Production systems
        - Sensitive environments
    - Document impact.

9. **Create Asset Inventory**
    - Record:
        - Hostnames
        - IP addresses
        - Asset owners
        - Business criticality
    - Finalise affected asset list.

10. **Escalate and Hand Off**
    - Provide findings to containment and recovery teams.
    - Update the incident record.

## 3. Post-Action

- Ensure affected asset inventory is complete.
- Preserve evidence supporting asset identification.
- Attach asset inventory to the incident record.

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
