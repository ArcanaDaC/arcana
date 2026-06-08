# RB-TRIAGE-006: Lost & Stolen Device Validation

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Lost & Stolen Device Validation | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Report of a lost, misplaced, or stolen device
- Device identifier available:
    - Hostname
    - Serial number
    - Asset tag
    - Mobile device identifier
- User information available
- Access to asset inventory
- Access to MDM or endpoint management platform
- Access to EDR platform
- Access to Identity Provider (IdP)
- Access to SIEM
- Incident ticket created

## 2. Step-by-Step Instructions

1. **Collect Initial Incident Information**
    - Obtain:
        - Reporting user
        - Device type
        - Asset identifier
        - Date and time last seen
        - Last known location
        - Circumstances of loss or theft
    - Record all details in the incident ticket.

2. **Validate Asset Ownership**
    - Confirm:
        - Device is organisationally owned or managed
        - Assigned user
        - Business unit
        - Asset status
    - Verify information against the asset inventory.

3. **Determine Device Classification**
    - Identify whether the asset is:
        - Laptop
        - Desktop
        - Mobile phone
        - Tablet
        - Removable media
        - Other managed device
    - Document the device classification.

4. **Review Device Management Status**
    - Determine whether the device:
        - Is enrolled in MDM
        - Is enrolled in EDR
        - Has full disk encryption enabled
        - Is actively reporting telemetry
        - Has remote lock or wipe capability
    - Document all security controls currently applied.

5. **Identify Last Known Device Activity**
    - Review:
        - MDM telemetry
        - EDR telemetry
        - Authentication logs
        - VPN logs
        - Network activity
    - Determine:
        - Last check-in time
        - Last known IP address
        - Last known geographic location
        - Last authenticated user

6. **Assess Loss vs Theft Indicators**
    - Determine whether available evidence suggests:
        - Misplacement
        - Accidental loss
        - Theft
        - Unauthorised possession
    - Document observations and supporting evidence.

7. **Review Recent Authentication Activity**
    - Review:
        - Successful logins
        - Failed logins
        - MFA events
        - Session activity
        - Geographic anomalies
    - Identify any indicators of unauthorised use.

8. **Assess Preliminary Risk**
    - Consider:
        - Device encryption status
        - Privileged access assigned to the user
        - Access to sensitive systems
        - Access to regulated data
        - Device management status
        - Evidence of unauthorised activity
    - Assign a preliminary incident severity.

9. **Determine Required Response Actions**
    - Determine whether the incident requires:
        - Device Security Posture Assessment
        - Device Data Exposure Assessment
        - Account containment
        - Session revocation
        - Remote lock
        - Remote wipe
        - Escalation to Physical Security
    - Document recommended next actions.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Update incident severity if required.
    - Escalate to:
        - Analysis activities
        - Containment activities
        - Physical Security investigation (if applicable)
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all device identifiers are documented.
- Ensure all asset ownership information is recorded.
- Preserve relevant authentication and device telemetry.
- Document risk assessment findings and supporting evidence.
- Attach all validation findings to the incident record.
- Ensure required analysis and containment activities have been initiated.
- Participate in subsequent investigation activities as required.

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
