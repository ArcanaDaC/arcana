# RB-CONTAIN-004: Host Isolation

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Host Isolation | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- Access to EDR platform
- Access to NAC platform
- Access to firewall management

## 2. Step-by-Step Instructions
1. **Validate Isolation Requirements**
   - Confirm reason for isolation
   - Assess propagation or impact risk if the host remains connected
   - Evaluate user impact
   - Assess critical business function dependency

2. **Isolate Host**
   - Choose one of the following
      - Perform EDR isolation (recommended)
      - Perform network disconnection
      - Perform VLAN quarantine
      - Perform NAC isolation

3. **Restrict Lateral Movement**
   - Block SMB access
   - Block remote admin protocols
   - Block peer-to-peer communication
   - Block unnecessary outbound traffic

4. **Validate Isolation Effectiveness**
   - Confirm host no longer communicating externally
   - Verify isolation remains enforced

## 3. Post-Action
- Document all actions taken within the incident ticket

---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.