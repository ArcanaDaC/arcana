# RB-CONTAIN-005: Session & Token Revocation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Session & Token Revocation | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

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

> **Common Failure Modes**
>   - Resetting passwords without revoking sessions
>   - Ignoring mobile or API sessions
>   - Missing OAuth persistence

1. Identify Active Sessions
   - Review:
      - Browser sessions
      - Mobile sessions
      - OAuth sessions
      - API sessions
      - VPN sessions

2. Revoke Session
   - Perform:
      - Global sign-out
      - Browser session invalidation
      - VPN session termination
      - SaaS session revocation

3. Revoke Tokens
   - Invalidate:
      - Refresh tokens
      - OAuth access tokens
      - API tokens
      - Persistent sessions

4. Remove Unauthorised Access
   - Review and remove:
      - Rogue devices
      - Suspicious browser sessions
      - Unknown API integrations
      - Persistent login approvals

5. Validate Revocation Success
   - Confirm:
      - Sessions terminated successfully
      - Tokens invalidated
      - No continued attacker activity
      - New authentication required

## 3. Post-Action
- Document all containment steps taken in the incident ticket, along with the time each action was taken
---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
