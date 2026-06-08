# RB-ANALYSIS-040: Vulnerable Asset Identification

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Vulnerable Asset Identification | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Completion of Vulnerability Validation
- Completion of Vulnerability Exposure Assessment
- CVE, advisory, or finding identifier available
- Access to vulnerability management platform
- Access to asset inventory
- Access to CMDB (if available)
- Access to cloud asset inventory
- Access to endpoint management platform
- Access to SIEM
- Incident or tracking ticket created

## 2. Step-by-Step Instructions

1. **Review Vulnerability Scope**
    - Review:
        - CVE identifier
        - Affected products
        - Affected versions
        - Vulnerability prerequisites
    - Document affected technologies.

2. **Query Vulnerability Management Platform**
    - Search for:
        - Existing vulnerability findings
        - Matching software versions
        - Matching operating systems
        - Matching services
    - Export relevant findings where possible.

3. **Review Asset Inventory**
    - Identify assets running:
        - Affected operating systems
        - Affected applications
        - Affected services
        - Affected cloud workloads
    - Document candidate assets.

4. **Review Cloud Environments**
    - Identify:
        - Virtual machines
        - Containers
        - Serverless functions
        - Managed services
    - Determine whether vulnerable software is present.

5. **Review Endpoint Population**
    - Review endpoint inventory for:
        - Installed software
        - Software versions
        - Configuration information
    - Identify affected endpoints.

6. **Review Internet-Facing Assets**
    - Identify:
        - Public applications
        - Public services
        - External infrastructure
        - Public cloud resources
    - Prioritise exposed assets.

7. **Validate Asset Status**
    - Confirm:
        - Asset ownership
        - Business function
        - Production status
        - Operational status
    - Remove false positives where appropriate.

8. **Assign Asset Criticality**
    - Determine:
        - Business criticality
        - Data sensitivity
        - Availability requirements
        - Exposure level
    - Prioritise remediation targets.

9. **Create Vulnerable Asset Inventory**
    - Record:
        - Hostname
        - IP address
        - Asset owner
        - Business unit
        - Asset criticality
        - Vulnerability status
    - Prepare final asset list.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Escalate to:
        - Exploitation Verification
        - Vulnerability Exposure Reduction
        - Remediation activities
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all affected assets are documented.
- Ensure asset ownership and criticality are recorded.
- Preserve vulnerability scan results and supporting evidence.
- Document any identified false positives.
- Attach the vulnerable asset inventory to the incident record.
- Support containment and remediation activities as required.

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
