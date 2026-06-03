# RB-004.4 MFA Reset & Validation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | MFA Reset & Validation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

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

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current MFA configuration
   - Document registered MFA methods

5. **Preserve Evidence (if applicable)**
   - Document MFA enrollment history

6. **Execute Task Steps**
   - **6.1 Review Existing MFA Configuration**
     - Identify registered MFA methods
     - Identify trusted devices
     - Identify recovery methods
     - Identify push notification approvals
     - Identify hardware token assignments

   - **6.2 Identify Suspicious MFA Activity**
     - Review MFA fatigue attempts
     - Review unexpected approvals
     - Review rogue device registrations
     - Review suspicious enrollment events
     - Review bypass activity

   - **6.3 Remove Existing MFA Enrollments**
     - Reset push-based MFA
     - Reset TOTP applications
     - Reset SMS-based MFA
     - Reset hardware token associations
     - Reset backup/recovery methods

   - **6.4 Validate Trusted Devices**
     - Review device ownership
     - Review device health
     - Review device compliance status
     - Review device registration timestamps
     - Remove unknown devices
     - Remove non-compliant devices
     - Remove suspicious device enrollments

   - **6.5 Re-Enroll MFA Securely**
     - Require fresh MFA registration
     - Verify user identity
     - Approve authentication methods
     - Validate device compliance

   - **6.6 Validate Authentication Integrity**
     - Confirm MFA functioning correctly
     - Verify no rogue devices remain
     - Verify no persistent approvals exist
     - Verify authentication challenges enforced

7. **Verify Task Completion**
   - Confirm MFA reset status
   - Verify trusted device inventory
   - Validate MFA integrity validation
   - Verify residual risk assessment

8. **Update Incident Documentation**
   - Record MFA reset actions
   - Document devices removed
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if rogue MFA device identified
   - Escalate if MFA bypass identified
   - Escalate if multiple accounts affected

10. **Hand Off or Notify Next Responsible Party**
    - Notify user of MFA reset
    - Provide MFA re-enrollment instructions

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Rogue MFA device identified | Expand compromise assessment |
| MFA bypass identified | Escalate severity |
| Multiple accounts affected | Expand investigation scope |

---

## Output

- MFA reset status
- Trusted device inventory
- MFA integrity validation
- Residual risk assessment

---

## Common Failure Modes

- Leaving trusted devices intact
- Ignoring backup recovery methods
- Re-enrolling MFA without identity verification

---

## Automation Hooks

- Auto-MFA reset
- Auto-device enumeration
- Auto-compliance validation
- Auto-risk scoring

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.3 Session & Token Revocation](./RB-004.3-session-token-revocation.md)
- Next: [RB-004.5 OAuth & Application Consent Review](./RB-004.5-oauth-application-consent-review.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
