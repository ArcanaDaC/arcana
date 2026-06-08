# RB-ANALYSIS-032: Device Security Posture Assessment

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Device Security Posture Assessment | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Lost or stolen device incident
- Completion of Lost & Stolen Device Validation
- Access to MDM platform
- Access to EDR platform
- Access to asset inventory
- Access to Identity Provider (IdP)
- Access to device management records
- Device identifier available:
  - Hostname
  - Serial number
  - Asset tag
  - Mobile device identifier
- Incident ticket created

## 2. Step-by-Step Instructions

1. **Identify Device Details**
   - Confirm:
     - Device type
     - Asset owner
     - Operating system
     - Device management status
   - Document device information.

2. **Validate Device Enrollment Status**
   - Determine whether the device is enrolled in:
     - MDM
     - EDR
     - Asset management systems
   - Document management coverage.

3. **Review Encryption Status**
   - Verify:
     - Full disk encryption status
     - Encryption technology in use
     - Encryption key escrow status
   - Document findings.

4. **Review Endpoint Security Controls**
   - Determine whether the device has:
     - EDR protection
     - Antivirus protection
     - Firewall enabled
     - Device control policies
     - Application control policies
   - Document security controls present.

5. **Review Authentication Controls**
   - Determine:
     - MFA requirements
     - Device trust status
     - Conditional access policies
     - Privileged account usage
   - Document authentication protections.

6. **Review Remote Management Capabilities**
   - Verify availability of:
     - Remote lock
     - Remote wipe
     - Device location tracking
     - Remote access revocation
   - Determine available containment options.

7. **Review Compliance Status**
   - Determine whether the device complies with:
     - Security baselines
     - Patch requirements
     - Encryption requirements
     - Device management requirements
   - Document non-compliance findings.

8. **Assess Security Risk**
   - Evaluate:
     - Likelihood of compromise
     - Likelihood of data exposure
     - Effectiveness of existing controls
     - Ability to contain the device remotely
   - Assign a risk rating.

9. **Determine Recommended Actions**
   - Identify required actions including:
     - Account containment
     - Session revocation
     - Remote lock
     - Remote wipe
     - Additional investigation
   - Document recommendations.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Escalate to:
      - Device Data Exposure Assessment
      - Remote Device Lock & Wipe
      - Account containment activities
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all device security controls are documented.
- Ensure encryption status is recorded.
- Document all identified security gaps.
- Attach assessment findings to the incident record.
- Preserve supporting evidence and screenshots where applicable.
- Ensure recommended containment actions are tracked to completion.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
