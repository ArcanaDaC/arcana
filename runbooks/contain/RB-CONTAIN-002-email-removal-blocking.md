# RB-001.6 Email Removal & Blocking

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Email Removal & Blocking | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Sender domains
- Email subjects
- URLs
- Attachment hashes
- Message IDs
- Campaign indicators
- Access to Microsoft 365
- Access to Google Workspace
- Access to Secure Email Gateway (SEG)
- Access to DNS / proxy platform
- Access to SIEM / logging platform

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Identify all matching emails in the environment

5. **Preserve Evidence (if applicable)**
   - Document email metadata before removal

6. **Execute Task Steps**
   - **6.1 Identify All Matching Emails**
     - Locate delivered messages
     - Locate quarantined messages
     - Locate forwarded copies
     - Locate internal relay copies

   - **6.2 Remove Emails from Mailboxes**
     - Perform tenant-wide remediation
     - Delete phishing emails
     - Purge from inboxes
     - Remove from deleted items if required
     - Validate removal success

   - **6.3 Block Sender Infrastructure**
     - Block sender domains
     - Block reply-to domains
     - Block sending IPs
     - Block known malicious infrastructure

   - **6.4 Block URLs**
     - Add blocks at Secure Email Gateway
     - Add blocks at DNS filtering
     - Add blocks at proxy
     - Add blocks at browser isolation platform (if applicable)

   - **6.5 Block Attachments / Hashes**
     - Prevent delivery of malicious hashes
     - Prevent delivery of file types associated with campaign

   - **6.6 Deploy Temporary Detections**
     - Add detections for similar subjects
     - Add detections for similar domains
     - Add detections for similar URLs
     - Add detections for behavioural patterns

   - **6.7 Validate Effectiveness**
     - Confirm no remaining emails exist
     - Verify blocks are active
     - Confirm users cannot access malicious infrastructure

7. **Verify Task Completion**
   - Confirm all emails removed
   - Verify blocks deployed
   - Validate detection updates applied

8. **Update Incident Documentation**
   - Record removal actions
   - Document blocks deployed
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if new campaign variants identified
   - Escalate if internal forwarding continues

10. **Hand Off or Notify Next Responsible Party**
    - Notify security team of block status
    - Provide list of deployed blocks

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| New campaign variants identified | Expand blocks/detections |
| Internal forwarding observed | Expand remediation scope |
| Users still accessing URLs | Escalate user notification |

---

## Output

- Emails removed
- Blocks deployed
- Detections updated
- Validation completed

---

## Automation Hooks

- Auto-delete phishing emails
- Auto-block domains/URLs
- Auto-update SEG rules
- Auto-create temporary detections

---

## Notes

- Validate remediation success — deletion jobs can fail silently
- Avoid over-blocking legitimate infrastructure
- Monitor for attacker domain rotation

---

## Related

- Playbook: [PB-001 Phishing](../../playbooks/PB-001-phishing.md)
- Previous: [RB-001.5 Phishing Retro Hunt](./RB-001.5-phishing-retro-hunt.md)
- Next: [RB-001.7 User Notification](./RB-001.7-user-notification.md)
