# RB-EVIDENCE-001: Memory Acquisition
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Memory Acquisition | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | [Draft/Approved/Retired] | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | [Brief summary of changes] | |

## 1. Prerequisites
- Impacted host identifier (hostname, asset ID, IP, instance ID)
- Authorisation to capture memory from the host
- Access to the host (local, remote, EDR live-response, or cloud console)
- Sufficient storage destination for the resulting image (size of physical RAM)

**Required Tools:**
- Memory acquisition tool appropriate for the OS (e.g. WinPMEM, DumpIt, Magnet RAM Capture, AVML, EDR live-response)
- Hashing utility (SHA-256)
- Secure transfer path to evidence storage

## 2. Step-by-Step Instructions
> Common Failure Modes
> - Rebooting or shutting down the host before acquisition
> - Running unnecessary tools that modify memory state
> - Failing to capture acquisition metadata or hashes
> - Losing chain of custody during transfer

1. Validate Need for Memory Acquisition
	- Confirm at least one of:
		- Active threat activity suspected on the host
		- In-memory execution suspected
		- Credential theft or process injection suspected
		- Host required for forensic preservation regardless of current state
	- Confirm acquisition will not destroy more evidence than it preserves (e.g. if the tool requires reboot/install, weigh trade-offs)

2. Acquire Memory Safely
	- Avoid rebooting, shutting down, or running unnecessary tools on the host prior to acquisition
	- Perform a full physical memory acquisition using an approved tool
	- Verify the resulting image is complete and not zero-bytes before releasing the host

## 3. Post-Action
- Transfer the image to the designated evidence storage location via a secure path
- Verify the SHA-256 hash matches before and after transfer
- Record acquisition metadata: operator, timestamp, host, tool, tool version, and the SHA-256 hash of the resulting image
- Confirm chain of custody is recorded end-to-end (capture → transfer → storage)

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.