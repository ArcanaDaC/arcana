# RB-CONTAIN-010 Traffic Filtering & Rate Limiting

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Document Name | Traffic Filtering & Rate Limiting | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- DDoS activity has been confirmed
- Incident ticket has been created
- Traffic analysis has been completed
- Affected services have been identified
- Network Operations team is engaged
- Infrastructure teams are engaged
- Appropriate change approvals have been obtained where required

---

# 2. Step-by-Step Instructions

### Step 1 – Review Traffic Analysis Findings

Review:

- Attack type
- Source IP distribution
- Geographic distribution
- Traffic volume
- Protocols involved
- Targeted services
- Attack signatures

Determine:

- Filtering opportunities
- Rate limiting opportunities
- Potential business impact of mitigation actions

Document findings.

---

### Step 2 – Identify Filtering Locations

Determine where controls can be applied:

- CDN
- WAF
- Load balancer
- Reverse proxy
- Firewall
- Router
- Cloud-native protection services
- ISP mitigation services

Document available enforcement points.

---

### Step 3 – Implement Source-Based Filtering

Where appropriate:

- Block malicious source IPs
- Block malicious IP ranges
- Block known botnet infrastructure
- Block malicious ASNs
- Apply geolocation restrictions

Validate that legitimate traffic is not significantly impacted.

Document actions taken.

---

### Step 4 – Implement Protocol Filtering

Review and restrict malicious traffic patterns such as:

- UDP floods
- SYN floods
- ICMP floods
- DNS abuse
- Reflection traffic
- Amplification traffic

Apply protocol-specific protections where appropriate.

Document changes.

---

### Step 5 – Implement Application-Layer Filtering

Where application-layer attacks are identified:

- Block malicious user agents
- Block malicious request patterns
- Block known attack signatures
- Restrict abusive API usage
- Restrict excessive requests

Validate application functionality after implementation.

Document actions.

---

### Step 6 – Apply Rate Limiting Controls

Implement rate limiting where appropriate:

- Requests per second
- Connections per second
- Authentication requests
- API requests
- Session creation
- Resource-intensive operations

Apply limits that minimise business impact.

Document configuration changes.

---

### Step 7 – Validate Effectiveness

Review:

- Traffic reduction
- Service availability
- Error rates
- Application response times
- Customer impact

Determine whether mitigation actions are reducing attack effectiveness.

Document findings.

---

### Step 8 – Monitor for Evasion

Review for:

- Source rotation
- Protocol switching
- Attack pattern changes
- New infrastructure
- Multi-vector attacks

Adjust filtering controls where required.

Document observations.

---

### Step 9 – Coordinate Operational Communications

Notify:

- Incident Commander
- Network Operations
- Infrastructure teams
- Service owners
- Security leadership

Communicate:

- Controls implemented
- Expected impact
- Current effectiveness
- Remaining risks

Document communications.

---

### Step 10 – Update Incident Record

Record:

- Filtering controls implemented
- Rate limits applied
- Affected services
- Validation results
- Evasion attempts observed
- Communications performed

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure filtering actions are documented
- Ensure rate limiting actions are documented
- Ensure mitigation effectiveness has been validated
- Ensure operational communications are recorded
- Ensure supporting evidence is attached
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
