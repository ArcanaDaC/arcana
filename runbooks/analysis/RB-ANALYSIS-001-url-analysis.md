# RB-ANALYSIS-001: URL Analysis

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | URL Detonation & Analysis | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- URLs extracted from email
- Attachments (if present)
- Email timestamp
- User interaction data (if available)
- Access to Sandbox: 
   - AnyRun / Hybrid Analysis / Joe Sandbox
- Access to URL analysis tools: 
   - URLScan
   - VirusTotal
- Isolated VM for browser testing (never direct browsing)
- Threat intel platforms
- Proxy logs (optional)

## 2. Step-by-Step Instructions

1. **Normalize & Expand URLs**
   - Extract all URLs from email
      - Raw links
      - Obfuscated links (HTML encoded, shortened)
   - Expand URL shorteners (bit.ly, tinyurl, etc.)
   - Decode Base64 / URL encoding if present

2. **Passive Reputation Check**
   - Check each URL/domain:
      - VirusTotal
      - URLScan (previous scans)
      - Domain age (WHOIS)
   - Identify indicators: 
      - Newly registered domains
      - Low reputation / flagged URLs
      - Domains mimicking legitimate services

3. **Detonate URL in Sandbox**
   - Open URL in sandbox environment
   - Observe:
      - redirect chain
      - final landing page
      - network calls
      - file downloads
      - script execution

4. **Analyse Redirect Behaviour**
   - Track: 
      - Initial URL → intermediate redirects → final destination
   - Indicators: 
      - multiple redirects (especially through legit services)
      - redirect to credential harvesting page
      - Geo/IP-based conditional redirects

5. **Identify Credential Harvesting**
   - Look for: 
      - Fake login pages (O365, Google, Okta, etc.)
      - Form fields capturing username and password
      - POST requests to attacker-controlled domains
   - Compare HTML structure vs real login page and check for domain mismatch

6. **Analyse Attachments (if present)**
   - Upload to sandbox
      - Extract file hash (MD5/SHA256)
      - Analyze behaviour: process execution, network calls, persistence
   - Indicators: 
      - Macro execution (Office docs)
      - Droppers / loaders
      - Suspicious child processes

7. **Check for Payload Delivery**
   - Determine if URL 
      - Directly downloads file
      - Triggers drive-by download
      - Drops secondary payload


8. **Correlate with Internal Logs (Optional)**
   - Proxy logs:
      - Did users access final URL?
   - EDR
      - Any file execution tied to URL

## 3. Post-Action
- Document findings within the incident ticket
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.