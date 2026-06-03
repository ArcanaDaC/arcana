# RB-ANALYSIS-012: Phishing Interaction Validation
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Phishing Interaction Validation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- User identity (email / username)
- Email indicators (URLs, timestamp)
- Email logs
- Identity provider logs (Okta, Azure AD, Google)
- Proxy / web logs
- Endpoint telemetry (optional)
- User confirmation (if available)

**Required Tools:**
- IdP: Okta / Azure AD / Google Workspace
- Email platform: Message trace / click tracking
- Proxy / network logs: Zscaler, Netskope, etc.
- SIEM / log platform

## 2. Step-by-Step Instructions
1. **Check Email Interaction (Click Activity):** 
   - Query email security logs
      - Link click events
      - Time of Click
   Validate:
      - Which URL was accessed and how many times.
2. **Confirm Web Access:** 
   - Check proxy / DNS logs:
      - Did user resolve or connect to phishing domain?
   - Validate:
      - IP address
      - Timestamp alignment with email delivery
3. **Identify Credential Submission:** 
   - Indicators:
      - Access to known credential harvesting page
      - POST requests to suspicious endpoints
   - If available:
      - Inspect sandbox results from URL analysis
4. **Analyse Identity Provider Logs:** 
   - Look for:
      - Login attempts shortly after click
      - Successful login from:
         - New IP / geolocation  
         - Unusual device
      - MFA events:
         - Push approvals
         - MFA fatigue patterns

5. **Check for Active Sessions:**
   - Identify:
      - Existing active sessions
      - Token usage across services
   - Look for:
      - API usage spikes
      - SaaS access anomalies
6. **6.6 User Verification (if needed):** 
   - Contact user:
      - Did they click?
      - Did they enter credentials?
   - Cross-check with logs (do not rely solely on user memory)

## 3. Post-Action
- Document findings within the incident ticket
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.