# RB-TRIAGE-004: Third-Party Notification Validation

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Document Name | Third-Party Notification Validation | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

Before starting this runbook, ensure the following:

- Third-party compromise notification received
- Incident ticket created
- Access to vendor inventory
- Access to asset inventory
- Access to threat intelligence sources
- Access to vendor management contacts
- Access to security advisories and public reporting

## 2. Step-by-Step Instructions

1. **Identify Notification Source**

    Determine the source of the notification.

    Common sources include:

    - Vendor security notification
    - Vendor trust centre advisory
    - Security mailing list
    - Threat intelligence provider
    - Government advisory
    - Regulatory notification
    - Public disclosure
    - Social media disclosure
    - News reporting
    - Customer notification
    - Internal security team

    Document the source.

2. **Validate Notification Authenticity**

    Verify:

    - Notification sender
    - Vendor domain ownership
    - Advisory authenticity
    - Security bulletin legitimacy
    - Supporting references

    Review:

    - Vendor trust centre
    - Official advisories
    - Public statements
    - Security bulletins

    Identify potential phishing, spoofing, or misinformation attempts.

    Document findings.

3. **Identify Affected Third Party**

    Determine:

    - Vendor name
    - Product name
    - Service name
    - Business owner
    - Vendor criticality

    Identify:

    - Whether the vendor is actively used
    - Whether the relationship is current
    - Whether the service remains operational

    Document findings.

4. **Gather Incident Details**

    Collect:

    - Incident summary
    - Date of compromise
    - Discovery date
    - Attack vector
    - Impact statement
    - Scope of compromise
    - Known affected products
    - Known affected versions

    Document all available details.

5. **Collect Technical Information**

    Gather:

    - CVEs
    - Indicators of Compromise (IOCs)
    - Vendor mitigation guidance
    - Vendor remediation guidance
    - Detection recommendations
    - Published attacker techniques

    Store references within the incident record.

6. **Determine Organisational Exposure**

    Identify:

    - Use of affected products
    - Use of affected services
    - Use of affected versions
    - Existing integrations
    - Existing trust relationships

    Determine:

    - Whether the organisation is potentially exposed
    - Whether exposure can be immediately ruled out

    Document findings.

7. **Assess Severity**

    Determine whether the event represents:

    - Advisory only
    - Vulnerability disclosure
    - Suspected compromise
    - Confirmed compromise
    - Active exploitation
    - Confirmed organisational exposure

    Assign an initial severity rating.

    Document rationale.

. **Update Incident Record**

    Record:

    - Notification source
    - Validation results
    - Vendor details
    - Product details
    - Exposure assessment
    - Severity assessment
    - Stakeholder notifications

    Attach supporting evidence and references.

## 3. Post-Action

Upon completion:

- Ensure notification authenticity has been validated
- Ensure affected vendor and products have been identified
- Ensure exposure assessment has been completed
- Ensure severity assessment is documented
- Ensure incident ticket is updated

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
