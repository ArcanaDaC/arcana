# RB-ANALYSIS-018: Outbound Traffic Analysis

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Outbound Traffic Analysis | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites

- Alert, incident, or investigation involving suspicious outbound network activity (e.g. C2 / beaconing, data exfiltration, unauthorised transfer, post-exploitation comms, reverse shell)
- Access to firewall logs
- Access to proxy logs
- Access to DNS logs
- Access to NetFlow or network telemetry
- Access to EDR telemetry
- Access to SIEM
- Source IP addresses, hostnames, or user accounts associated with the investigation
- Time window for suspected activity

## 2. Step-by-Step Instructions

1. **Identify Suspected Assets**
   - Identify affected:
     - Endpoints
     - Servers
     - User accounts
     - Cloud workloads
   - Document all known indicators associated with the investigation.

2. **Establish Investigation Timeline**
   - Determine:
     - Initial alert time
     - Earliest known suspicious activity
     - Last observed activity
   - Define the analysis window.

3. **Review Outbound Network Connections**
   - Review network telemetry for:
     - External IP addresses
     - Domains
     - URLs
     - Destination countries
   - Identify all outbound communication from affected assets.

4. **Identify Unusual Outbound Activity**
   - Look for:
     - Large data transfers (potential exfiltration)
     - Beaconing patterns - regular intervals, jitter, periodic callbacks (potential C2)
     - Long-lived or persistent outbound connections (potential reverse shell or C2)
     - Connections to newly registered or typosquatted domains
     - Transfers or callbacks outside business hours
     - Unusual destinations or destination countries
     - Rare protocols
     - New or previously unseen connections
   - Document suspicious findings.

5. **Analyse Protocols and Traffic Patterns**
   - Review use of:
     - HTTPS
     - DNS (including tunnelling patterns - high-volume, unusual TXT/NULL records)
     - SFTP / SCP / FTP
     - SMB over VPN
     - Cloud storage services
     - Remote administration tools
     - ICMP / unusual port usage
   - Determine whether the traffic pattern is consistent with:
     - Bulk data transfer (exfiltration)
     - Low-volume callback (C2 / beaconing)
     - Interactive session (reverse shell, remote admin)

6. **Review Destination Infrastructure**
   - Assess:
     - Reputation of destination IPs
     - Reputation of destination domains
     - Hosting providers
     - Geographic location
   - Identify indicators of malicious or suspicious infrastructure.

7. **Correlate with Endpoint Activity**
   - Review EDR telemetry for:
     - File access activity, archive creation, compression utilities, cloud sync tools (potential exfiltration staging)
     - Suspicious process execution, parent-child chains, command-line activity (potential C2 / post-exploitation)
     - Persistence mechanisms (scheduled tasks, services, run keys, cron, launch agents)
     - Process injection or in-memory execution indicators
   - Determine whether outbound traffic correlates with data collection / staging, C2 / beaconing, or post-exploitation activity.

8. **Determine the Nature and Impact of the Outbound Activity**
   - **If exfiltration suspected**, estimate:
     - Volume and duration of transferred data
     - Number of affected assets
     - Potential sensitivity of impacted data
   - **If C2 / beaconing suspected**, identify:
     - Attacker infrastructure (IPs, domains, ASNs)
     - Beaconing tempo and jitter
     - Persistence indicators
     - Likely malware family or implant based on traffic pattern
   - **If reverse shell / interactive access suspected**, identify:
     - Session duration and source
     - Commands executed during the session
     - Files accessed or transferred
   - Document findings and confidence level.

9. **Document Findings**
   - Record:
     - Source systems
     - Source users
     - Destination infrastructure
     - Transfer methods
     - Transfer volumes
     - Timeline of events
   - Preserve relevant evidence.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Escalate based on findings:
      - Exfiltration confirmed → Data Staging Investigation, Sensitive Data Impact Assessment, Outbound Transfer Blocking
      - C2 / beaconing confirmed → Malware Analysis, Persistence Mechanism Hunt, Host Isolation
      - Reverse shell / interactive access confirmed → Host Isolation, Session Token Revocation, Account Lockdown
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all identified destinations are documented.
- Ensure all evidence sources are preserved.
- Attach relevant logs and telemetry to the incident record.
- Provide a summary of suspected exfiltration activity, affected assets, and identified destinations.
- Participate in subsequent investigation and containment activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
