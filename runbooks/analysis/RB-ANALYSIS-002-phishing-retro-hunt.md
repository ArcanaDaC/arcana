# RB-ANALYSIS-002 Phishing Retro Hunt

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Phishing Retro Hunt | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Sender addresses/domains
- Subject lines
- URLs
- Attachment hashes
- Email timestamps
- Threat intel indicators
- Access to email platform (Microsoft 365, Google Workspace)
- SIEM / log platform access
- EDR platform access
- Proxy / DNS logs access
- Threat intel platform access

## 2. Step-by-Step Instructions
1. **Identify Core Indicators**
   - Collect:
      - Sender domains
      - Reply-To addresses
      - URLs
      - Attachment hashes
      - IP addresses
      - Subjects


6.2. **Search Email Environment**
- Search for matching sender
- Search for similar subject lines
- Search for same URLs
- Search for same attachment hashes
- Determine number of recipients, delivery status, and user interaction

6.3. **Identify Click Activity**
- Review email click logs
- Review proxy logs
- Review DNS resolution events
- Determine which users accessed phishing infrastructure
- Correlate timestamp activity

6.4. **Hunt for Credential Exposure**
- Review IdP logs for suspicious logins
- Identify impossible travel activity
- Flag MFA anomalies
- Detect unusual device registrations

6.5. **Hunt for Malware Execution (If Applicable)**
- Search EDR telemetry for hash execution
- Identify process creation events
- Review network connections
- Analyze child process behaviour

6.6. **Identify Campaign Scope**
- Count total users targeted
- Count total users who interacted
- Identify departments impacted
- Determine geographic spread (if relevant)

6.7. **Add Additional Detection Logic**
- Deploy temporary detections for domains
- Deploy temporary detections for URLs
- Deploy temporary detections for hashes
- Deploy temporary detections for IPs
- Deploy behaviour pattern detection

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Additional impacted users identified | Expand incident scope |
| Malware execution observed | Escalate to PB-003 |
| Multiple departments impacted | Increase severity |
| Privileged accounts targeted | Immediate escalation |

---

## Output

- Campaign scope assessment
- List of impacted users
- Additional indicators discovered
- Detection rules deployed

---

## Automation Hooks

- Auto-retro search across tenant
- Auto-hunt URL/domain usage
- Auto-correlate IdP anomalies
- Auto-generate impacted user list

---

## Common Failure Modes

- Assuming phishing is isolated to a single user
- Failing to conduct historical searches where possible
- Leaving temporary detections active after incident closure

---

## Notes

- Phishing is rarely isolated to a single user
- Retro hunts should include historical searches where possible
- Temporary detections should be reviewed after incident closure

---

## Related

- Playbook: [PB-001 Phishing](../../playbooks/PB-001-phishing.md)
- Previous: [RB-001.4 Account Lockdown](./RB-001.4-account-lockdown.md)
- Next: [RB-001.6 Email Removal & Blocking](./RB-001.6-email-removal-blocking.md)
