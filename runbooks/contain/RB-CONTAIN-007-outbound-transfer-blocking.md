# RB-CONTAIN-007: Outbound Transfer Blocking

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Outbound Transfer Blocking | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites

- Confirmed or suspected active data exfiltration activity
- Completion of Outbound Traffic Analysis
- Access to firewall management platforms
- Access to proxy management platforms
- Access to DNS filtering platforms
- Access to cloud security tooling
- Access to network security tooling
- Access to SIEM
- List of identified:
  - Destination IP addresses
  - Domains
  - URLs
  - Cloud storage providers
  - SaaS platforms
- Incident Commander approval for containment actions (if required)

## 2. Step-by-Step Instructions

1. **Identify Active Exfiltration Paths**
   - Review investigation findings.
   - Identify:
     - Destination IP addresses
     - Domains
     - URLs
     - Cloud storage services
     - SaaS applications
     - Transfer protocols
   - Document all identified transfer paths.

2. **Validate Containment Scope**
   - Determine:
     - Affected users
     - Affected systems
     - Business impact of blocking actions
   - Confirm containment scope with the Incident Commander.

3. **Block Network Destinations**
   - Implement blocks for identified:
     - IP addresses
     - Domains
     - URLs
   - Use:
     - Firewalls
     - Secure Web Gateways
     - Proxies
     - DNS filtering solutions
   - Validate successful deployment.

4. **Block Cloud Storage Services**
   - Restrict access to identified cloud storage providers.
   - Block:
     - Upload functionality
     - Synchronisation services
     - Web-based transfer mechanisms
   - Validate enforcement across affected assets.

5. **Restrict SaaS-Based Transfers**
   - Disable or restrict:
     - External sharing
     - Public links
     - Guest access
     - Unauthorised file transfers
   - Document all changes made.

6. **Disable Unauthorised Transfer Mechanisms**
   - Restrict:
     - FTP
     - SFTP
     - SCP
     - Remote administration tools
     - File synchronisation utilities
   - Remove or disable unauthorised transfer channels where possible.

7. **Monitor for Continued Transfer Attempts**
   - Review:
     - Firewall logs
     - Proxy logs
     - DNS logs
     - Cloud audit logs
   - Identify continued attempts to communicate with blocked destinations.

8. **Validate Containment Effectiveness**
   - Confirm:
     - Active transfers have ceased
     - Destinations are unreachable
     - Upload attempts are blocked
     - Sharing restrictions are functioning correctly
   - Document validation results.

9. **Document Containment Actions**
   - Record:
     - Blocks implemented
     - Systems affected
     - Services restricted
     - Time of implementation
     - Validation results
   - Preserve supporting evidence.

10. **Escalate and Hand Off**
    - Provide containment status to the Incident Commander.
    - Coordinate with:
      - Recovery activities
      - Sensitive Data Impact Assessment
      - Regulatory and Legal Coordination
    - Update the incident record with all actions performed.

## 3. Post-Action

- Ensure all implemented blocks are documented.
- Ensure all containment actions are recorded in the incident record.
- Preserve logs demonstrating successful containment.
- Continue monitoring for attempted bypass activity.
- Coordinate with recovery teams before removing temporary restrictions.
- Participate in post-incident review activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
