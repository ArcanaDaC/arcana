# RB-ANALYSIS-019: Data Staging Investigation

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Data Staging Investigation | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Suspected or confirmed data exfiltration incident
- Access to EDR telemetry
- Access to endpoint forensic tooling
- Access to file system artifacts
- Access to SIEM
- Access to operating system event logs
- Access to cloud workload telemetry (if applicable)
- Hostnames, usernames, and assets identified during triage
- Investigation timeline established

## 2. Step-by-Step Instructions

1. **Identify Potentially Impacted Assets**
   - Identify:
     - Workstations
     - Servers
     - Cloud workloads
     - File servers
     - SaaS-connected endpoints
   - Document all assets associated with the investigation.

2. **Review File Access Activity**
   - Identify:
     - Large-scale file access
     - Bulk file enumeration
     - Sensitive file access
     - Unusual access patterns
   - Determine whether activity aligns with normal business operations.

3. **Identify Archive Creation Activity**
   - Review execution and file creation activity for:
     - ZIP
     - RAR
     - 7z
     - TAR
     - GZIP
     - Other compression utilities
   - Identify newly created archive files.

4. **Investigate Staging Directories**
   - Review:
     - Temporary directories
     - User profile directories
     - Downloads folders
     - Shared folders
     - Cloud sync folders
   - Identify locations used to aggregate files prior to transfer.

5. **Review Command-Line Activity**
   - Investigate execution of:
     - Compression tools
     - File copy utilities
     - Synchronisation tools
     - Scripting engines
     - Automation utilities
   - Document suspicious commands and execution chains.

6. **Review Cloud Storage Usage**
   - Identify use of:
     - OneDrive
     - Google Drive
     - Dropbox
     - Box
     - Mega
     - Other cloud storage providers
   - Determine whether files were copied into synchronised directories.

7. **Review Removable Media Activity**
   - Investigate:
     - USB device insertions
     - External storage usage
     - Large file copy operations
   - Identify potential staging to removable media.

8. **Correlate with Outbound Traffic Analysis**
   - Compare identified staging activity against:
     - Network transfers
     - Cloud uploads
     - External communications
   - Determine whether staged data was subsequently transferred.

9. **Determine Scope of Staged Data**
   - Identify:
     - Number of files involved
     - File types involved
     - Data owners
     - Business units affected
     - Estimated data volume
   - Document findings and confidence level.

10. **Escalate and Hand Off**
    - Provide findings to the Incident Commander and Technical Lead.
    - Escalate to:
      - Sensitive Data Impact Assessment
      - Exfiltration Scoping Hunt
      - Containment activities
    - Update the incident record with all findings.

## 3. Post-Action

- Ensure all staging locations are documented.
- Preserve identified artifacts and forensic evidence.
- Document all archive files and associated metadata.
- Record all identified staging tools and techniques.
- Attach investigation findings to the incident record.
- Participate in subsequent containment and impact assessment activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
