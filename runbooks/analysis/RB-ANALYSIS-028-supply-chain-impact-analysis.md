# RB-ANALYSIS-028 Supply Chain Impact Analysis

## Document Control

| Attribute | Value | Date |
|------------|------------|------------|
| Runbook ID | RB-ANALYSIS-028 | 2026-06-04 |
| Runbook Name | Supply Chain Impact Analysis | 2026-06-04 |
| Owner | Arcana Framework | 2026-06-04 |
| Version | 1.0 | 2026-06-04 |
| Status | Live | 2026-06-04 |

---

# 1. Prerequisites

Before starting this runbook, ensure the following:

- Supply chain compromise has been identified or reported
- Incident ticket created
- Impacted vendor, software, or dependency identified
- Asset inventory available
- Software inventory available
- Cloud and SaaS inventories available
- Business owner identified

---

# 2. Step-by-Step Instructions

### Step 1 – Identify the Affected Supply Chain Component

Determine:

- Vendor name
- Product name
- Product version
- Dependency name
- Integration type
- Deployment model

Identify whether the issue involves:

- Software supplier
- SaaS provider
- Cloud provider
- Managed service provider
- Open-source dependency
- Hardware supplier

Document findings.

---

### Step 2 – Collect Publicly Available Details

Gather:

- Vendor advisory
- Security bulletin
- CVE references
- Vendor communications
- Threat intelligence reporting
- Known indicators of compromise

Determine:

- Nature of compromise
- Attack vector
- Known attacker activity
- Published impact guidance

Document findings.

---

### Step 3 – Identify Organisational Exposure

Review:

- Asset inventory
- Endpoint inventory
- Server inventory
- Cloud inventory
- SaaS inventory
- Development environments

Identify:

- Affected systems
- Affected business units
- Affected users
- Affected environments

Document all impacted assets.

---

### Step 4 – Determine Version Exposure

Review:

- Installed versions
- Running versions
- Deployment dates
- Update history
- Configuration details

Determine:

- Vulnerable versions
- Supported versions
- Patched versions
- Unsupported versions

Document findings.

---

### Step 5 – Review Trust Relationships

Assess:

- API integrations
- Service accounts
- Federation relationships
- OAuth integrations
- Vendor access paths
- Administrative access

Identify:

- Direct trust relationships
- Indirect trust relationships
- Privileged access paths

Document findings.

---

### Step 6 – Assess Potential Impact

Determine whether compromise could result in:

- Remote code execution
- Credential theft
- Data exposure
- Privilege escalation
- Malware deployment
- Supply chain malware propagation
- Administrative access abuse

Assign impact rating.

---

### Step 7 – Review Available Telemetry

Review:

- Authentication logs
- EDR telemetry
- Cloud audit logs
- SaaS audit logs
- Administrative activity
- Network activity

Look for:

- Indicators of compromise
- Suspicious access
- Unexpected changes
- Suspicious execution

Document findings.

---

### Step 8 – Determine Scope Expansion Requirements

Assess whether additional investigation is required for:

- Downstream dependencies
- Connected vendors
- Partner environments
- Shared infrastructure
- Shared credentials
- Shared integrations

Expand investigation scope where necessary.

---

### Step 9 – Recommend Response Actions

Determine whether to:

- Disable integrations
- Restrict vendor access
- Patch affected systems
- Rotate credentials
- Revoke tokens
- Isolate systems
- Activate additional playbooks

Document recommendations.

---

### Step 10 – Update Incident Record

Record:

- Affected products
- Impacted assets
- Exposure assessment
- Trust relationship review
- Telemetry findings
- Recommended actions
- Escalation decisions

Attach supporting evidence.

---

# 3. Post-Action

Upon completion:

- Ensure affected assets have been identified
- Ensure vulnerable versions have been documented
- Ensure trust relationships have been reviewed
- Ensure impact assessment has been completed
- Ensure response recommendations are documented
- Ensure incident ticket is updated

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
