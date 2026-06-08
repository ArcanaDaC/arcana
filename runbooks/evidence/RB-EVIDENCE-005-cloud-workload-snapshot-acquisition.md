# RB-EVIDENCE-005: Cloud Workload Snapshot Acquisition

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Cloud Workload Snapshot Acquisition | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Identifier of the workload to snapshot (instance ID, container/pod ID, function name, service ID)
- Authorisation to snapshot the workload (workload owner notified or break-glass authority)
- Write access to the cloud account / subscription / project / tenancy hosting the workload
- A dedicated forensic destination (account / project / region) where snapshots will be stored - must not be the same account / project that hosts the impacted workload
- Cloud provider console or CLI for the impacted account
- Hashing tool (e.g. `sha256sum`) for any snapshots exported outside the cloud

## 2. Step-by-Step Instructions

> **Common Failure Modes**
> - Snapshotting after the workload is terminated - most providers cannot snapshot a terminated workload, and ephemeral state is lost the moment it stops
> - Letting auto-scaling replace or terminate the workload mid-snapshot
> - Storing snapshots in the same compromised account / project where they can be modified or deleted by the attacker
> - Capturing disk only and skipping memory where the provider supports memory capture - volatile evidence is lost
> - Forgetting to record snapshot IDs and hashes, breaking chain of custody

1. **Confirm Workload Identity and Authorisation**
    - Verify you are taking the snapshot of the right workload
    - Confirm authorisation from the workload owner or Incident Commander
    - Confirm the forensic destination is ready to receive snapshots

2. **Identify What to Snapshot**
    - For VMs: all attached disks / volumes; memory if provider supports live capture
    - For containers / pods: the container filesystem (commit the running container to an image); the pod's writable layer; mounted volumes
    - For serverless functions: the deployed package / image; any attached storage (EFS, persistent volumes); recent invocation logs
    - For managed services: provider-specific snapshot or export (e.g. RDS snapshot, managed disk snapshot)

3. **Suspend Auto-Replacement**
    - If the workload is in an auto-scaling group, detach it or suspend the group's launch/terminate processes
    - If it's a Kubernetes pod, cordon the node and patch the controller (Deployment / StatefulSet) to prevent re-scheduling
    - If it's a serverless function, throttle concurrency to zero or disable the function trigger
    - This prevents the workload being destroyed mid-snapshot

4. **Take Snapshots**
    - Trigger snapshots via the cloud provider console or CLI
    - For memory: use the provider's live-capture mechanism if available (e.g. Azure VM live snapshot, GCP VM serial console capture)
    - For containers: commit the container to an image; export the image
    - For functions: download the function's deployment package or container image
    - Confirm each snapshot completes successfully before moving on

5. **Copy to Forensic Destination and Record Metadata**
    - Copy or share each snapshot to the dedicated forensic destination
    - Record for each snapshot: snapshot ID, source workload ID, source region, size, timestamp, SHA-256 hash (where supported), and the responder who captured it
    - Confirm snapshots in the destination are read-only or write-protected
    - Verify snapshot integrity in the destination before considering acquisition complete

## 3. Post-Action

- Record snapshot IDs, hashes, timestamps, and destination location in the incident record
- Notify the Incident Commander that snapshots are complete and ready for analysis

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
