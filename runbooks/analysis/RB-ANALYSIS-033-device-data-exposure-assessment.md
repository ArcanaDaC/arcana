# RB-ANALYSIS-033: Device Data Exposure Assessment

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Device Data Exposure Assessment | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial creation | |

## 1. Prerequisites

- Lost or stolen device incident
- Completion of Lost & Stolen Device Validation
- Completion of Device Security Posture Assessment
- Access to asset inventory
- Access to endpoint telemetry
- Access to MDM platform
- Access to data classification standards
- Access to affected user information
- Incident ticket created

## 2. Step-by-Step Instructions

1. **Identify Device Owner and Usage**
   - Determine:
     - Assigned user
     - Business unit
     - Role
     - Privilege level
   - Document findings.

2. **Identify Data Sources Accessible from the Device**
   - Review access to:
     - File shares
     - SaaS platforms
     - Cloud storage
     - Databases
     - Internal applications
   - Document accessible resources.

3. **Assess Local Data Storage**
   - Determine whether the device stores:
     - Local files
     - Cached files
     - Offline synchronised data
     - Email data
     - Application data
   - Document potential exposure points.

4. **Review Data Classification Exposure**
   - Determine whether the device may contain:
     - Public data
     - Internal data
     - Confidential data
     - Restricted data
     - Regulated data
   - Document classifications involved.

5. **Assess Credential Exposure**
   - Identify:
     - Stored credentials
     - Browser-stored passwords
     - Authentication tokens
     - Certificates
     - VPN credentials
   - Document potential credential exposure.

6. **Assess Privileged Access Exposure**
   - Determine whether the user has:
     - Administrative privileges
     - Production access
     - Cloud administration access
     - Security administration access
   - Document findings.

7. **Review Security Controls**
   - Evaluate:
     - Full disk encryption
     - Screen lock controls
     - MDM protections
     - EDR protections
   - Determine effectiveness of controls against exposure.

8. **Determine Potential Business Impact**
   - Assess:
     - Data exposure risk
     - Operational risk
     - Regulatory risk
     - Reputational risk
   - Document overall impact assessment.

9. **Develop Exposure Summary**
   - Summarise:
     - Potentially exposed data
     - Potentially exposed credentials
     - Potentially exposed systems
     - Risk level
   - Prepare findings for stakeholders.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Escalate to:
      - Data Exfiltration response activities
      - Account containment activities
      - Regulatory review activities (if required)
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all identified exposure risks are documented.
- Record affected systems and datasets.
- Preserve supporting evidence and assessment results.
- Attach the completed assessment to the incident record.
- Support containment and recovery activities as required.
- Participate in post-incident review activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
