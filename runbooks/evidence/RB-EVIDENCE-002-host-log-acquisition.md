# RB-EVIDENCE-002: Host-Based Log Acquisition

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Host-Based Log Acquisition | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- Impacted host identifier (hostname, asset ID, IP, instance ID)
- Authorisation to collect logs from the host, from the EDR platform, and from any cloud provider covering it
- Access to:
    - The host (local, remote, EDR live-response, or cloud console)
    - The EDR platform used to manage the host
    - The SIEM / central log platform
    - The cloud provider console / API (AWS, Azure, GCP) if the host is cloud-hosted

**Required Tools:**
- EDR platform / live-response capability for the relevant agent (e.g. CrowdStrike RTR, SentinelOne, Defender for Endpoint, Carbon Black)
- OS-native log collection tooling:
    - Windows: `wevtutil`, PowerShell `Get-WinEvent`, KAPE, or equivalent triage collector
    - Linux: `journalctl`, `tar`/`gzip` over `/var/log`, or equivalent triage collector
    - macOS: `log collect`, `sysdiagnose`, or equivalent triage collector
- Cloud provider CLI / log export tooling (AWS CLI, Azure CLI, `gcloud`)
- Hashing utility (SHA-256)
- Secure transfer path to evidence storage

## 2. Step-by-Step Instructions
> Common Failure Modes
> - Rebooting or reimaging the host before logs are collected (clears volatile and rolling logs)
> - Collecting from only one source (e.g. EDR telemetry) and missing categories that only exist in OS-native or application logs
> - Allowing log rotation to overwrite relevant entries during the response window
> - Forgetting cloud control-plane logs for cloud-hosted instances (CloudTrail, Azure Activity, GCP Admin Activity)
> - Failing to capture acquisition metadata or hashes
> - Losing chain of custody during transfer

1. Validate Need and Scope of Log Acquisition
    - Confirm the host is in scope for the incident and identify the time window of interest
    - Determine whether the host is on-premises, virtual, or cloud-hosted (this dictates whether Step 4 applies)
    - Where possible, preserve logs centrally first (EDR console, SIEM, cloud logging) to guard against on-host tampering or rotation

2. Collect Relevant Host Activity Logs
    - Identify which categories of activity are relevant to the incident and collect them from whichever source on the host carries them (EDR agent telemetry, OS-native logs, application logs, SIEM export). Common categories and where they typically live per OS:
        - **Process execution** (process create, command line, parent process, user context)
            - Windows: EDR telemetry, Sysmon Event ID 1, Security log 4688
            - Linux: EDR telemetry, auditd `execve` records, `/var/log/audit/audit.log`
            - macOS: EDR telemetry, Endpoint Security framework events, unified log (`log collect`)
        - **File system events** (write, rename, delete - especially in user profile, temp, and system directories)
            - Windows: EDR telemetry, Sysmon Event IDs 11/23/26, Security log 4663
            - Linux: EDR telemetry, auditd file watches, `/var/log/audit/audit.log`
            - macOS: EDR telemetry, Endpoint Security file events, FSEvents
        - **Network connections** (outbound connections, DNS lookups, listening ports)
            - Windows: EDR telemetry, Sysmon Event IDs 3/22, Windows Firewall log, DNS Client log
            - Linux: EDR telemetry, `/var/log/syslog` or `journalctl`, conntrack, resolver logs
            - macOS: EDR telemetry, unified log network subsystem, pf firewall log
        - **Module / library load events**
            - Windows: EDR telemetry, Sysmon Event ID 7
            - Linux: EDR telemetry, auditd module load records, `/var/log/kern.log`
            - macOS: EDR telemetry, Endpoint Security library load events
        - **Configuration / persistence changes**
            - Windows: EDR telemetry, Sysmon Event IDs 12/13/14 (registry), Task Scheduler log, Services event log
            - Linux: EDR telemetry, auditd watches on `/etc/`, cron logs, systemd journal
            - macOS: EDR telemetry, unified log, LaunchAgent/LaunchDaemon plist changes
        - **Script and interpreter activity** (PowerShell, WMI, cmd, bash, zsh, python)
            - Windows: EDR telemetry, PowerShell Operational log (4103/4104), WMI-Activity log, Security log 4688
            - Linux: EDR telemetry, shell history (`.bash_history`, `.zsh_history`), auditd `execve`
            - macOS: EDR telemetry, shell history, unified log
        - **Authentication and logon events**
            - Windows: EDR telemetry, Security log (4624/4625/4634/4672), RDP/TerminalServices logs
            - Linux: EDR telemetry, `/var/log/auth.log` or `/var/log/secure`, `journalctl _COMM=sshd`, `last`/`wtmp`
            - macOS: EDR telemetry, unified log auth subsystem, `/var/log/asl/`
        - **Detections, preventions, and quarantine actions** raised on the host by EDR or built-in protection (Defender, XProtect, ClamAV, etc.)
        - **Relevant application / service logs** for the incident (web server, database, identity agent, backup agent, custom application)
    - For each relevant category, prefer querying or exporting from your SIEM/EDR where the data is already centralised; fall back to on-host collection when it isn't
    - If collecting on-host, avoid rebooting, shutting down, or running unnecessary tools on the host during collection
    - Record the query, time range, and export/access location for each category collected

3. Collect Centralised Logs from the SIEM
    - Export matching events from the SIEM or central log platform for the host over the incident window
    - Include any enriched or correlated alerts associated with the host
    - Record the query, time range, and export location

4. Collect Cloud Provider Logs (Cloud-Hosted Instances Only)
    - For the impacted instance, export control-plane and data-plane logs covering the incident window from the relevant provider:
        - **AWS:** CloudTrail (management + data events), VPC Flow Logs, GuardDuty findings, EC2 instance metadata service (IMDS) access logs, CloudWatch Logs streams from the instance (system + application), Systems Manager session/run-command history
        - **Azure:** Azure Activity Log, Microsoft Entra ID sign-in and audit logs, NSG Flow Logs, Microsoft Defender for Cloud alerts, Azure Monitor / Log Analytics workspace data for the VM (system + application), Run Command / Serial Console history
        - **GCP:** Cloud Audit Logs (Admin Activity, Data Access, System Event, Policy Denied), VPC Flow Logs, Security Command Center findings, Cloud Logging entries for the instance (system + application), OS Login / serial console / `gcloud compute ssh` history
    - Scope queries to the instance ID, private/public IPs, and any associated service accounts or instance roles
    - Record the query, time range, and export location for each extract

5. Package and Hash the Collected Logs
    - Combine the collected logs into a single compressed archive per host, organised by source (EDR, OS, application, SIEM, cloud)
    - Generate a SHA-256 hash of the archive
    - Verify the archive opens and is not zero-bytes before releasing the host

## 3. Post-Action
- Transfer the archive to the designated evidence storage location via a secure path
- Verify the SHA-256 hash matches before and after transfer
- Record acquisition metadata: operator, timestamp, host, sources collected, time range, tools and tool versions used, and the SHA-256 hash of the resulting archive
- Confirm chain of custody is recorded end-to-end (collection → transfer → storage)
- Hand off to the analyst responsible for log review and update the incident ticket with the evidence reference

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
