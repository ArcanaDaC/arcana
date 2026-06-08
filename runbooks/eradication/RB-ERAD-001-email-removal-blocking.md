# RB-ERAD-001: Email Removal & Blocking

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Email Removal & Blocking | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- IOCs identified during triage and analysis:
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

## 2. Step-by-Step Instructions

1. **Identify All Matching Emails**
	- Locate delivered messages
	- Locate quarantined messages
	- Locate forwarded copies
	- Locate internal relay copies

2. **Remove Emails from Mailboxes**
	- Perform tenant-wide remediation:
		- Delete phishing emails
		- Purge from inboxes
		- Remove from deleted items if required
	- Validate removal success.


3. **Block Sender Infrastructure**
	- Block:
		- Sender domains
		- Reply-To domains
		- Sending IPs
		- Known malicious infrastructure


4. **Block URLs**
	- Add blocks at:
		- Secure Email Gateway
		- DNS filtering
		- Proxy
		- Browser isolation platform (if applicable)


5. **Block Attachments / Hashes**
	- Prevent delivery or execution of:
		- Malicious hashes
		- File types associated with campaign

6. **Deploy Temporary Detections**
	- Add detections for:
		- Similar subjects
		- Similar domains
		- Similar URLs
		- Behavioural patterns

7. **Validate Effectiveness**
	- Confirm:
		- No remaining emails exist
		- Blocks are active
		- Users cannot access malicious infrastructure

## 3. Post-Action
- Note down time of email removals and blocking in the incident ticket

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
