# RB-TRIAGE-008: Business Email Compromise Validation

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Business Email Compromise Validation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial creation | |

## 1. Prerequisites

- Suspected Business Email Compromise incident
- Access to email platform
- Access to Identity Provider (IdP)
- Access to SIEM
- Access to email security tooling
- Access to affected user information
- Incident ticket created

## 2. Step-by-Step Instructions

1. **Review Initial Report**
   - Identify:
     - Reporting party
     - Affected user
     - Suspected activity
     - Time of occurrence
   - Record findings.

2. **Validate User Identity**
   - Confirm ownership of the affected mailbox.
   - Validate account details.

3. **Review Authentication Activity**
   - Review:
     - Successful logins
     - Failed logins
     - MFA activity
     - Geographic anomalies
   - Document findings.

4. **Review Mailbox Activity**
   - Review:
     - Sent emails
     - Deleted emails
     - Mailbox configuration changes
   - Identify suspicious activity.

5. **Review Email Security Alerts**
   - Review:
     - Email detections
     - Phishing alerts
     - BEC detections
   - Document findings.

6. **Assess Financial Fraud Indicators**
   - Determine whether:
     - Payment requests were sent
     - Vendor changes were requested
     - Payroll changes were requested
   - Document findings.

7. **Determine Compromise Status**
   - Assess:
     - No compromise
     - Suspected compromise
     - Confirmed compromise
   - Document confidence level.

8. **Assess Immediate Risk**
   - Determine:
     - Business impact
     - Financial exposure
     - Data exposure
   - Assign preliminary severity.

9. **Document Findings**
   - Record all observations and evidence.

10. **Escalate and Hand Off**
    - Escalate confirmed incidents for investigation and containment.
    - Update the incident record.

## 3. Post-Action

- Preserve evidence supporting validation.
- Document findings and severity.
- Ensure appropriate escalation has occurred.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
