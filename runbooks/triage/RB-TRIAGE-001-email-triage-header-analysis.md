# RB-TRIAGE-001 Email Triage & Header Analysis
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Email Triage & Header Analysis | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Full email headers (raw)
- Email body (raw + rendered)
- Sender address
- Attachments (if any)
- Embedded URLs
- Email security alert (if triggered)

**Required Tools:**
- Email platform: Microsoft 365 (Message Trace, Defender), Google Workspace (Email Log Search)
- Header analysis tools:
   - Built-in analyzers / MXToolbox
- Threat intel: 
   - VirusTotal
   - URLScan
- Internal logging: 
   - SIEM / log platform

## 2. Step-by-Step Instructions
1. **Collect Full Email Data**
   - Retrieve full email headers (not partial)
   - Capture:
      - Sender (From, Reply-To)
      - Subject
      - Timestamp
      - Message-ID
2. **Analyse Authentication Results - Check:** 
   - SPF → pass/fail
   - DKIM → pass/fail 
   - DMARC → pass/fail/alignment. 
   - Indicators: 
      - SPF fail or softfail
      - DKIM missing or invalid 
      - DMARC fail
3. **Validate Sender Identity**
   - Compare: 
      - Display Name vs Actual Email Address
      - Domain similarity (typosquatting, homoglyphs)
   - Check: 
      - Newly registered domains
      - External sender spoofing internal user
4. **Review Email Routing**
   - Analyse `Received:` headers:
      - Originating IP
      - Sending infrastructure
      - Unusual relays or geolocation anomalies
5. **Extract Indicators**
   - Pull out:
   - All URLs (including obfuscated URLs)
   Attachment names + hashes
   - Reply-To domain (often different)
6. **Perform Initial Reputation Checks**
   - URLS → VirusTotal/URLScan
   - Domains → passive DNS / reputation
   - File hashes → malware databases
7. **Assess Email Content:**
   - Look for: 
      - urgency/pressure tactics
      - credential prompts
      - financial requests
      - suspicious attachments
      - link text vs actual destination mismatch

## 3. Post-Action
- Ensure all analysed headers, extracted IOCs, and initial verdict are documented in the incident ticket
## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.