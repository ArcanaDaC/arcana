# RB-ANALYSIS-002: Phishing Retro Hunt

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Phishing Retro Hunt | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |


## 1. Prerequisites
- Access to a list of IOCs
   - Sender addresses/domains
   - Subject lines
   - URLs
   - Attachment hashes
   - Email timestamps
   - Threat intel indicators
- Access to email platform (Microsoft 365, Google Workspace)
- SIEM / log platform access
- EDR platform access
- Proxy / DNS logs access
- Threat intel platform access

## 2. Step-by-Step Instructions
1. **Identify Core Indicators**
   - Collect:
      - Sender domains
      - Reply-To addresses
      - URLs
      - Attachment hashes
      - IP addresses
      - Subjects
2. **Search Email Environment**:
   - Search for:
      - Matching sender
      - Similar subject lines
      - Same URLs
      - Same attachment hashes

   - Determine:
      - Number of recipients
      - Delivery status
      - User interaction

3. **Identify Click Activity**
   - Review:
      - Email click logs
      - Proxy logs
      - DNS resolution events
   - Determine:
      - Which users accessed phishing infrastructure
      - Timestamp correlation


4. **Hunt for Credential Exposure**
   - Review IdP logs for:
      - Suspicious logins
      - Impossible travel
      - MFA anomalies
      - Unusual devices

5. **Hunt for Malware Execution (If Applicable)**
   - Search EDR telemetry for:
      - Hash execution
      - Process creation
      - Network connections
      - Child process behaviour

6. **Identify Campaign Scope**
   - Determine:
      - Total users targeted
      - Total users interacted
      - Departments impacted
      - Geographic spread (if relevant)


7. **Add Additional Detection Logic**
   - Deploy temporary detections for:
      - Domains
      - URLs
      - Hashes
      - IPs
      - Behaviour patterns

## 3. Post-Action
- Document all findings in the incident ticket

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
