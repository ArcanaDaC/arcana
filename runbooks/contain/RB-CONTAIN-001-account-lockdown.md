# RB-001.4 Account Lockdown

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Account Lockdown | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- User identity (email / username)
- Identity provider logs
- Session/token data
- MFA status
- Associated endpoint telemetry (if available)
- Access to Identity Provider (IdP): Okta, Azure AD / Entra, Google Workspace
- EDR platform access
- SIEM / logging platform access
- SaaS admin consoles access

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current account status and active sessions

5. **Preserve Evidence (if applicable)**
   - Document current security posture before modifications

6. **Execute Task Steps**
   - **6.1 Assess Compromise Status**
     - Determine whether credentials were submitted
     - Check for suspicious login activity
     - Identify active sessions
     - Assess for MFA bypass or fatigue

   - **6.2 Disable or Lock Account**
     - Disable user account immediately OR force password reset with temporary lockout
     - Ensure user cannot authenticate during containment

   - **6.3 Revoke Active Sessions & Tokens**
     - Revoke browser sessions
     - Revoke OAuth tokens
     - Revoke refresh tokens
     - Revoke mobile sessions
     - Revoke API sessions
     - Validate revocation success

   - **6.4 Reset Credentials**
     - Force password reset
     - Require strong password
     - Prevent password reuse (if supported)

   - **6.5 Enforce MFA Re-Registration**
     - Reset MFA factors
     - Require re-enrollment
     - Remove unknown/authenticator devices

   - **6.6 Review Account Activity**
     - Check for inbox rules
     - Check for mail forwarding
     - Check for OAuth app consent
     - Check for new devices
     - Check for privilege changes

   - **6.7 Validate Lateral Movement Risk**
     - Review SaaS access logs
     - Review VPN usage
     - Review shared credentials
     - Review admin portal access
     - If suspicious activity observed, escalate to PB-002 Account Takeover or PB-009 Privilege Escalation

   - **6.8 Restore User Access**
     - Once verified, re-enable account
     - Confirm MFA operational
     - Notify user

7. **Verify Task Completion**
   - Confirm account containment completed
   - Verify sessions revoked
   - Confirm MFA reset completed
   - Validate timeline of compromise actions

8. **Update Incident Documentation**
   - Record all actions taken
   - Document timeline
   - Update incident ticket with status

9. **Escalate if Issues Arise**
   - Escalate if suspicious activity cannot be contained
   - Escalate if lateral movement confirmed

10. **Hand Off or Notify Next Responsible Party**
    - Notify user of account restoration
    - Provide guidance on credential change
    - Provide MFA re-registration instructions

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Credentials confirmed exposed | Immediate containment |
| Suspicious sessions active | Revoke all sessions |
| Admin account impacted | Escalate severity |
| OAuth abuse identified | Remove app access |

---

## Output

- Account containment completed
- Sessions revoked
- MFA reset completed
- Timeline of compromise actions

---

## Automation Hooks

- Auto-disable account
- Auto-revoke sessions
- Auto-reset MFA
- Auto-remove malicious inbox rules

---

## Notes

- Session revocation is critical — password reset alone is insufficient
- Check for persistence via OAuth applications
- Prioritise privileged accounts immediately

---

## Related

- Playbook: [PB-001 Phishing](../../playbooks/PB-001-phishing.md)
- Escalation: [PB-002 Account Takeover](../../playbooks/PB-002-account-takeover.md)
- Previous: [RB-001.3 Credential Exposure Validation](./RB-001.3-credential-exposure-validation.md)
