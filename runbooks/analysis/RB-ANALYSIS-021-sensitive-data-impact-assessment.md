# RB-ANALYSIS-021: Sensitive Data Impact Assessment

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Sensitive Data Impact Assessment | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Suspected or confirmed data exfiltration incident
- Completion of:
    - Outbound Traffic Analysis
    - Data Staging Investigation
    - Cloud Storage & SaaS Review (if applicable)
- Access to data classification standards
- Access to data inventory or asset inventory
- Access to data owners and business stakeholders
- Access to SIEM and investigation artifacts
- Access to DLP telemetry (if available)
- Investigation timeline established

## 2. Step-by-Step Instructions

1. **Identify Potentially Impacted Data Sources**
    - Identify:
        - File shares
        - Databases
        - Cloud storage repositories
        - SaaS platforms
        - Collaboration platforms
        - Endpoint data stores
    - Document all systems associated with the suspected exposure.

2. **Identify Potentially Exposed Data**
    - Review investigation findings to determine:
        - Files accessed
        - Files staged
        - Files transferred
        - Data repositories involved
    - Create an inventory of potentially exposed information.

3. **Determine Data Classification**
    - Classify identified data according to organisational standards.
    - Determine whether exposed data includes:
        - Public data
        - Internal data
        - Confidential data
        - Restricted data
        - Regulated data

4. **Assess Regulated Data Exposure**
    - Identify whether exposed data contains:
        - Personally Identifiable Information (PII)
        - Financial information
        - Health information
        - Government-regulated information
        - Contractually protected information
    - Document all regulatory implications.

5. **Assess Intellectual Property Exposure**
    - Determine whether exposed data includes:
        - Source code
        - Proprietary algorithms
        - Research data
        - Product designs
        - Strategic business information
    - Assess potential business impact.

6. **Identify Affected Business Units**
    - Determine:
        - Data owners
        - Business units impacted
        - Customers impacted
        - Partners impacted
    - Notify relevant stakeholders.

7. **Assess Exposure Scope**
    - Estimate:
        - Number of files exposed
        - Number of records exposed
        - Volume of data exposed
        - Duration of exposure
    - Document assumptions and confidence levels.

8. **Assess Business Impact**
    - Evaluate potential impacts including:
        - Operational disruption
        - Financial impact
        - Legal impact
        - Regulatory impact
        - Reputational impact
    - Assign an overall impact assessment.

9. **Prepare Impact Assessment Summary**
    - Document:
        - Impacted datasets
        - Data classifications
        - Regulatory considerations
        - Business impact assessment
        - Exposure estimates
    - Prepare summary for Incident Commander and stakeholders.

10. **Escalate and Hand Off**
    - Provide findings to:
        - Incident Commander
        - Legal & Compliance
        - Data Owners
        - Executive Stakeholders (if required)
    - Escalate to:
        - Escalation, Legal & Executive Communications
        - Recovery and Exposure Mitigation activities
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all impacted datasets are documented.
- Ensure data classifications are recorded.
- Preserve supporting evidence and investigation artifacts.
- Document all assumptions and confidence levels used during assessment.
- Attach the final impact assessment to the incident record.
- Support legal, compliance, and regulatory review activities as required.

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
