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
| Change Summary | Initial creation | |

## 1. Prerequisites

- Alert, incident, or investigation involving suspected data exfiltration
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

4. **Identify Unusual Transfer Activity**
   - Look for:
     - Large data transfers
     - Transfers outside business hours
     - Unusual destinations
     - Rare protocols
     - New or previously unseen connections
   - Document suspicious findings.

5. **Analyse Transfer Protocols**
   - Review use of:
     - HTTPS
     - SFTP
     - SCP
     - FTP
     - SMB over VPN
     - Cloud storage services
     - Remote administration tools
   - Determine whether the protocol could support bulk data transfer.

6. **Review Destination Infrastructure**
   - Assess:
     - Reputation of destination IPs
     - Reputation of destination domains
     - Hosting providers
     - Geographic location
   - Identify indicators of malicious or suspicious infrastructure.

7. **Correlate with Endpoint Activity**
   - Review EDR telemetry for:
     - File access activity
     - Archive creation
     - Compression utilities
     - Cloud synchronisation tools
     - Command-line activity
   - Determine whether outbound traffic correlates with data collection or staging activity.

8. **Determine Potential Data Exposure**
   - Estimate:
     - Volume of transferred data
     - Duration of transfers
     - Number of affected assets
     - Potential sensitivity of impacted data
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
    - Escalate to:
      - Data Staging Investigation
      - Sensitive Data Impact Assessment
      - Containment activities
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
