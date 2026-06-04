# RB-CONTAIN-001: Account Lockdown

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Account Lockdown | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |


## 1. Prerequisites
- User identity (email / username)
- Session/token data
- MFA status
- Access to Identity Provider (IdP): Okta, Azure AD / Entra, Google Workspace

## 2. Step-by-Step Instructions

1. **Assess Compromise Status**
    - Determine whether:
      - Credentials were submitted
      - Suspicious login activity exists
      - Active sessions are present
      - MFA bypass or fatigue occurred
2. **Disable or Lock Account**
	- Immediately:
		- Disable user account OR
		- Force password reset with temporary lockout
	- User cannot authenticate during containment

3. **Revoke Active Sessions & Tokens**
	- Revoke:
		- Browser sessions
		- OAuth tokens
		- Refresh tokens
		- Mobile sessions
		- API sessions
	- Validate revocation success.

4. **Reset Credentials**
	- Force password reset
	- Require strong password
	- Prevent password reuse (if supported)

5. **Enforce MFA Re-Registration**
	- Reset MFA factors
	- Require re-enrollment
	- Remove unknown/authenticator devices


## 3. Post-Action
- Document findings within the incident ticket
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.