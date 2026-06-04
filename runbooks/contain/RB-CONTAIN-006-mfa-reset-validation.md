# RB-CONTAIN-006: MFA Reset & Validation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | MFA Reset & Validation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Identity provider logs
- MFA telemetry
- Device registration logs
- User account information
- Authentication timeline
- Access to identity provider
- Access to MFA platform
- Access to SIEM
- Access to mobile device management platform

## 2. Step-by-Step Instructions
>Common Failure Modes
>- Leaving trusted devices intact
>- Ignoring backup recovery methods
>- Re-enrolling MFA without identity verification


1. Review Existing MFA Configuration
    - Identify:
        - Registered MFA methods
        - Trusted devices
        - Recovery methods
        - Push notification approvals
        - Hardware token assignments

2. Identify Suspicious MFA Activity

    - Review:
        - MFA fatigue attempts
        - Unexpected approvals
        - Rogue device registrations
        - Suspicious enrollment events
        - Bypass activity

3. Remove Existing MFA Enrollments

    - Reset:
        - Push-based MFA
        - TOTP applications
        - SMS-based MFA
        - Hardware token associations
        - Backup/recovery methods

4. Validate Trusted Devices

    - Review:
        - Device ownership
        - Device health
        - Device compliance status
        - Device registration timestamps

    Remove:
        - Unknown devices
        - Non-compliant devices
        - Suspicious device enrollments

5. Re-Enroll MFA Securely
    - Require:
        - Fresh MFA registration
        - Verified user identity
        - Approved authentication methods
        - Device compliance validation

6. Validate Authentication Integrity
    - Confirm:
        - MFA functioning correctly
        - No rogue devices remain
        - No persistent approvals exist
        - Authentication challenges enforced


## 3. Post-Action
- Document all containment steps taken in the incident ticket, along with the time each action was taken
---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.

