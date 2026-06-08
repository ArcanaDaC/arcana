# RB-POST-003: Data Exfiltration Hardening

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Data Exfiltration Hardening | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Incident declared contained and recovered
- Completion of Post-Incident Review (PIR)
- Completion of Sensitive Data Impact Assessment
- Root cause identified or reasonably understood
- Existing security controls documented
- Access to relevant security, cloud, and SaaS platforms
- Stakeholder approval for remediation activities (if required)

## 2. Step-by-Step Instructions

1. **Review Incident Findings**
   - Review:
     - Root cause
     - Attack path
     - Exfiltration method
     - Impacted systems
     - Impacted datasets
     - Existing control failures
   - Document all identified security gaps.

2. **Review Data Access Controls**
   - Assess:
     - User permissions
     - Group memberships
     - Administrative privileges
     - Shared access models
   - Identify opportunities to reduce unnecessary access.

3. **Review Data Classification Coverage**
   - Validate that sensitive data is appropriately:
     - Identified
     - Classified
     - Labelled
     - Protected
   - Document classification gaps.

4. **Review Data Loss Prevention Controls**
   - Assess:
     - DLP policies
     - DLP alerting
     - DLP coverage
     - DLP enforcement actions
   - Identify opportunities for improvement.

5. **Review Cloud and SaaS Security Controls**
   - Assess:
     - Sharing controls
     - Guest access controls
     - External collaboration settings
     - OAuth application governance
     - Data retention controls
   - Identify required hardening activities.

6. **Review Monitoring and Detection Coverage**
   - Assess:
     - Exfiltration detections
     - Cloud activity monitoring
     - SaaS activity monitoring
     - Authentication monitoring
     - Data access monitoring
   - Identify detection gaps.

7. **Implement Approved Hardening Measures**
   - Implement:
     - Access control improvements
     - Monitoring enhancements
     - DLP improvements
     - Cloud security improvements
     - SaaS security improvements
     - Logging improvements
   - Document all changes.

8. **Validate Control Effectiveness**
   - Confirm:
     - Controls are functioning correctly
     - New detections generate expected alerts
     - Access restrictions are effective
     - Monitoring coverage has improved
   - Document validation results.

9. **Update Documentation**
   - Update:
     - Playbooks
     - Runbooks
     - SOPs
     - Detection documentation
     - Security standards
   - Ensure lessons learned are incorporated.

10. **Escalate and Hand Off**
    - Provide hardening summary to:
      - Incident Commander
      - Security Leadership
      - System Owners
      - Relevant Stakeholders
    - Update the incident record with all actions performed.
    - Track outstanding remediation items to completion.

## 3. Post-Action

- Ensure all remediation actions are documented.
- Ensure all identified security gaps are tracked to closure.
- Record all implemented security improvements.
- Attach validation results to the incident record.
- Update relevant security metrics and reporting.
- Participate in continuous improvement activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
