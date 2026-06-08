# RB-RECOVERY-006 Service Availability Restoration

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Document Name | Service Availability Restoration | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- DDoS mitigation activities have been completed or stabilised
- Service impact assessment has been completed
- Service owners have been identified
- Infrastructure teams are engaged
- Network Operations teams are engaged
- Cloud providers have been engaged where applicable
- Incident ticket remains active

---

# 2. Step-by-Step Instructions

### Step 1 – Validate Attack Status

Review:

- Current traffic volumes
- Active mitigation status
- Service health metrics
- Error rates
- Availability metrics
- Infrastructure utilisation

Determine:

- Whether the attack is ongoing
- Whether attack activity has significantly reduced
- Whether restoration activities can safely begin

Document findings.

---

### Step 2 – Assess Service Health

Review:

- Application health
- API health
- Website availability
- Infrastructure health
- Network health
- Database health
- Cloud resource health

Identify:

- Remaining service degradation
- Failed components
- Resource exhaustion issues

Document findings.

---

### Step 3 – Verify Mitigation Effectiveness

Confirm:

- DDoS controls are functioning
- Traffic filtering remains effective
- Rate limiting remains effective
- CDN protections remain active
- Cloud mitigation services remain active

Determine whether additional protections should remain enabled during recovery.

Document decisions.

---

### Step 4 – Restore Critical Services

Prioritise restoration of:

- Customer-facing services
- Authentication services
- Revenue-generating services
- Regulatory-sensitive services
- Executive communication platforms
- Business-critical infrastructure

Validate functionality after restoration.

Document actions performed.

---

### Step 5 – Remove Temporary Controls

Review temporary controls implemented during containment.

Examples include:

- Emergency filtering rules
- Temporary rate limits
- Temporary routing changes
- Temporary service restrictions
- Temporary traffic controls

Remove controls only when:

- Risk is acceptable
- Services remain stable
- Business owners approve

Document all changes.

---

### Step 6 – Validate End-to-End Functionality

Test:

- User authentication
- Customer transactions
- API functionality
- Service integrations
- Third-party connectivity
- Administrative functions

Verify expected functionality.

Document test results.

---

### Step 7 – Monitor Service Stability

Monitor:

- Availability metrics
- Response times
- Error rates
- Infrastructure utilisation
- Customer support reports
- Business telemetry

Determine whether services remain stable under normal operating conditions.

Document observations.

---

### Step 8 – Confirm Customer Impact Resolution

Review:

- Customer complaints
- Support ticket volume
- Service desk reports
- Business owner feedback
- Service level indicators

Determine whether customer impact has been resolved.

Document findings.

---

### Step 9 – Obtain Restoration Approval

Obtain confirmation from:

- Service owners
- Infrastructure teams
- Network Operations
- Security leadership
- Incident Commander

Confirm:

- Recovery objectives achieved
- Services operating normally
- Monitoring remains active

Document approvals.

---

### Step 10 – Update Incident Record

Record:

- Restoration activities performed
- Services restored
- Temporary controls removed
- Validation results
- Monitoring outcomes
- Stakeholder approvals

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure service restoration activities are documented
- Ensure functionality validation is completed
- Ensure customer impact resolution is documented
- Ensure stakeholder approvals are recorded
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
