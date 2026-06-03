# RB-002.1 Rapid Containment & Network Segmentation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Rapid Containment & Network Segmentation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- EDR alerts
- Impacted host list
- Network telemetry
- SIEM alerts
- User reports
- Access to EDR platform
- Access to firewall management
- Access to NAC / segmentation platform
- Access to SIEM
- Access to Active Directory
- Access to virtualisation platform

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current network topology
   - Document active systems status

5. **Preserve Evidence (if applicable)**
   - Document current encryption and propagation status

6. **Execute Task Steps**
   - **6.1 Identify Actively Impacted Systems**
     - Determine currently encrypting systems
     - Identify systems communicating with ransomware infrastructure
     - Identify shared resources impacted

   - **6.2 Isolate Impacted Hosts**
     - Isolate hosts via EDR
     - Disconnect from network if EDR unavailable
     - Prevent SMB access

   - **6.3 Restrict Lateral Movement**
     - Temporarily restrict SMB
     - Temporarily restrict RDP
     - Temporarily restrict PsExec
     - Temporarily restrict WMI
     - Temporarily restrict WinRM
     - Temporarily restrict remote admin shares

   - **6.4 Segment Impacted Networks**
     - Isolate impacted VLANs/subnets
     - Block east-west traffic where feasible
     - Restrict server-to-server communications

   - **6.5 Protect Critical Infrastructure**
     - Prioritise protection for domain controllers
     - Prioritise protection for backup infrastructure
     - Prioritise protection for hypervisors
     - Prioritise protection for identity providers
     - Prioritise protection for critical business applications

   - **6.6 Preserve Evidence**
     - Where possible, capture memory
     - Preserve logs
     - Preserve ransom notes
     - Avoid unnecessary rebooting

7. **Verify Task Completion**
   - Confirm containment status
   - Verify isolated systems list
   - Validate segmentation actions completed
   - Confirm protected critical infrastructure

8. **Update Incident Documentation**
   - Record containment actions
   - Document network segmentation changes
   - Update incident timeline

9. **Escalate if Issues Arise**
   - Escalate if encryption ongoing
   - Escalate if critical infrastructure impacted
   - Escalate if hypervisors impacted
   - Escalate if containment failing

10. **Hand Off or Notify Next Responsible Party**
    - Notify network team of segmentation changes
    - Provide isolated host inventory

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Encryption ongoing | Expand containment scope |
| Critical infrastructure impacted | Escalate severity |
| Hypervisors impacted | Prioritise backup validation |
| Containment failing | Disconnect affected segments entirely |

---

## Output

- Containment status
- List of isolated systems
- Segmentation actions completed
- Protected critical infrastructure list

---

## Common Failure Modes

- Delayed isolation
- Reconnecting isolated systems too early
- Failing to isolate backup systems
- Ignoring east-west propagation

---

## Automation Hooks

- Auto-isolate endpoints
- Auto-disable SMB
- Auto-apply emergency firewall rules
- Auto-block malicious infrastructure

---

## Related

- Playbook: [PB-002 Ransomware](../../playbooks/PB-002-ransomware.md)
- Next: [RB-002.2 Identify Patient Zero](./RB-002.2-identify-patient-zero.md)
