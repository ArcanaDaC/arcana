# RB-003.4 Host Isolation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Host Isolation | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Impacted endpoint list
- EDR telemetry
- Network telemetry
- Business criticality information
- Access to EDR platform
- Access to NAC platform
- Access to firewall management
- Access to SIEM

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current endpoint status
   - Document network connectivity

5. **Preserve Evidence (if applicable)**
   - Capture volatile telemetry before isolation
   - Preserve logs
   - Preserve suspicious binaries

6. **Execute Task Steps**
   - **6.1 Validate Isolation Requirements**
     - Determine active malware status
     - Assess propagation risk
     - Evaluate user impact
     - Assess critical business function dependency

   - **6.2 Isolate Endpoint**
     - Perform EDR isolation
     - Perform network disconnection
     - Perform VLAN quarantine
     - Perform NAC isolation

   - **6.3 Restrict Lateral Movement**
     - Block SMB access
     - Block remote admin protocols
     - Block peer-to-peer communication
     - Block unnecessary outbound traffic

   - **6.4 Preserve Evidence**
     - Where feasible, capture volatile telemetry
     - Preserve logs
     - Preserve suspicious binaries
     - Avoid unnecessary rebooting

   - **6.5 Validate Isolation Effectiveness**
     - Confirm endpoint no longer communicating externally
     - Verify malware activity reduced/stopped
     - Verify isolation remains enforced

7. **Verify Task Completion**
   - Confirm isolation status
   - Verify impacted system inventory
   - Validate containment timeline
   - Verify evidence preservation status

8. **Update Incident Documentation**
   - Record isolation actions
   - Document evidence collected
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if malware still beaconing
   - Escalate if additional hosts identified
   - Escalate if business-critical endpoint impacted

10. **Hand Off or Notify Next Responsible Party**
    - Notify endpoint team of isolation status
    - Provide evidence information

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Malware still beaconing | Expand network containment |
| Additional hosts identified | Broaden isolation scope |
| Business-critical endpoint | Coordinate controlled containment |

---

## Output

- Isolation status
- Impacted system inventory
- Containment timeline
- Evidence preservation status

---

## Common Failure Modes

- Delayed isolation
- Disconnecting without evidence preservation
- Reconnecting hosts too early

---

## Automation Hooks

- Auto-endpoint isolation
- Auto-network quarantine
- Auto-lateral movement blocking

---

## Related

- Playbook: [PB-003 Endpoint Malware Infection](../../playbooks/PB-003-endpoint-malware.md)
- Previous: [RB-003.3 Persistence Mechanism Hunt](./RB-003.3-persistence-mechanism-hunt.md)
- Next: [RB-003.5 Malware Payload Analysis](./RB-003.5-malware-payload-analysis.md)
