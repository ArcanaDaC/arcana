# RB-CONTAIN-011: Remote Device Lock & Wipe

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Remote Device Lock & Wipe | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- Lost or stolen device incident
- Completion of Lost & Stolen Device Validation
- Device identifier available:
  - Hostname
  - Serial number
  - Asset tag
  - Mobile device identifier
- Access to MDM platform
- Access to EDR platform
- Access to asset inventory
- Access to Identity Provider (IdP)
- Approval from Incident Commander (if required)
- Incident ticket created

## 2. Step-by-Step Instructions

1. **Confirm Device Details**
   - Verify:
     - Device ownership
     - Assigned user
     - Device type
     - Device management status
   - Confirm the correct device has been identified.

2. **Review Current Device Status**
   - Determine:
     - Last check-in time
     - Current connectivity status
     - Last known location
     - Device health status
   - Document findings.

3. **Assess Containment Requirements**
   - Determine whether:
     - Remote lock is sufficient
     - Remote wipe is required
     - Additional account containment is required
   - Confirm containment scope with the Incident Commander.

4. **Revoke Active Access**
   - Revoke:
     - Active user sessions
     - Authentication tokens
     - VPN access
     - Device trust relationships
   - Confirm successful revocation.

5. **Execute Remote Device Lock**
   - Initiate device lock through the approved management platform.
   - Validate:
     - Lock request submission
     - Successful execution status
   - Record all actions taken.

6. **Execute Remote Device Wipe**
   - Initiate remote wipe where authorised and required.
   - Confirm:
     - Wipe request submission
     - Wipe acknowledgement
     - Wipe completion status (if available)
   - Document results.

7. **Remove Device Access**
   - Remove:
     - Device registrations
     - Certificates
     - Managed application access
     - Conditional access trust
   - Validate removal.

8. **Monitor Device Status**
   - Continue monitoring:
     - Device check-ins
     - Authentication attempts
     - Location updates
     - Connectivity status
   - Escalate unexpected activity.

9. **Validate Containment Effectiveness**
   - Confirm:
     - Device access has been revoked
     - Lock or wipe actions completed successfully
     - User sessions have been terminated
     - Device can no longer access corporate resources
   - Document validation results.

10. **Escalate and Hand Off**
    - Provide containment status to the Incident Commander.
    - Coordinate with:
      - Recovery activities
      - Asset Management
      - Physical Security (if applicable)
    - Update the incident record with all actions performed.

## 3. Post-Action

- Ensure all containment actions are documented.
- Preserve logs and screenshots supporting lock or wipe actions.
- Record timestamps for all actions performed.
- Verify device trust relationships have been removed.
- Attach validation results to the incident record.
- Participate in recovery activities as required.

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
