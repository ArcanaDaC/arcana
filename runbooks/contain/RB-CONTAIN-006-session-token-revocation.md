# RB-004.3 Session & Token Revocation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Session & Token Revocation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Authentication telemetry
- Session inventory
- OAuth telemetry
- Identity provider logs
- Access to identity provider
- Access to OAuth management platform
- Access to SIEM
- Access to SaaS administration consoles

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current session status
   - Document active sessions

5. **Preserve Evidence (if applicable)**
   - Document authentication patterns before revocation

6. **Execute Task Steps**
   - **6.1 Identify Active Sessions**
     - Review browser sessions
     - Review mobile sessions
     - Review OAuth sessions
     - Review API sessions
     - Review VPN sessions

   - **6.2 Revoke Sessions**
     - Perform global sign-out
     - Perform browser session invalidation
     - Perform VPN session termination
     - Perform SaaS session revocation

   - **6.3 Revoke Tokens**
     - Invalidate refresh tokens
     - Invalidate OAuth access tokens
     - Invalidate API tokens
     - Invalidate persistent sessions

   - **6.4 Remove Unauthorised Access**
     - Review and remove rogue devices
     - Remove suspicious browser sessions
     - Remove unknown API integrations
     - Remove persistent login approvals

   - **6.5 Validate Revocation Success**
     - Confirm sessions terminated successfully
     - Verify tokens invalidated
     - Confirm no continued attacker activity
     - Verify new authentication required

7. **Verify Task Completion**
   - Confirm revoked session inventory
   - Verify token revocation status
   - Validate active session assessment
   - Verify residual risk findings

8. **Update Incident Documentation**
   - Record revocation actions
   - Document sessions revoked
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if sessions remain active
   - Escalate if persistent OAuth access identified
   - Escalate if continued attacker activity observed

10. **Hand Off or Notify Next Responsible Party**
    - Notify identity team of revocation
    - Provide session inventory

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Sessions remain active | Expand revocation scope |
| Persistent OAuth access identified | Proceed to RB-004.5 |
| Continued attacker activity observed | Escalate containment |

---

## Output

- Revoked session inventory
- Token revocation status
- Active session assessment
- Residual risk findings

---

## Common Failure Modes

- Resetting passwords without revoking sessions
- Ignoring mobile or API sessions
- Missing OAuth persistence

---

## Automation Hooks

- Auto-global sign-out
- Auto-token revocation
- Auto-session inventory collection

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.2 Authentication Log Analysis](./RB-004.2-authentication-log-analysis.md)
- Next: [RB-004.4 MFA Reset & Validation](./RB-004.4-mfa-reset-validation.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
