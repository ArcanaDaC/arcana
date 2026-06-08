# RB-ANALYSIS-016: Memory Analysis
## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Memory Analysis | |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites
- Acquired memory image with verified hash 
- Acquisition metadata: host, OS, OS version, capture time, tool, tool version
- Forensic workstation with appropriate analysis tooling
- Known IOCs or hypotheses from the investigation to guide analysis

**Required Tools:**
- Memory analysis framework (e.g. Volatility, Rekall, MemProcFS)
- YARA with relevant rule sets
- Threat intelligence platform access (for IOC lookups)

## 2. Step-by-Step Instructions
> Common Failure Modes
> - Analysing without acquisition metadata (wrong OS profile → unreliable results)
> - Treating in-memory artefacts as ground truth without corroboration
> - Missing memory-only malware due to scoped queries
> - Failing to record findings against the source image hash

1. Confirm Image Integrity
	- Verify the SHA-256 hash matches the acquisition record
	- Confirm the correct OS profile / symbol set is loaded for the image

2. Analyse Active Processes
	- Identify:
		- Suspicious processes
		- Hidden processes
		- Injected processes
		- Unsigned modules loaded into processes
		- Parent–child anomalies (unexpected lineage)
3. Extract In-Memory Credential Artefacts
	- LSASS process contents (NTLM hashes, plaintext credentials, Kerberos tickets, cached secrets)
	- Windows access tokens (primary and impersonation)
	- Authentication tokens (OAuth, session cookies, API tokens)
	- DPAPI master keys
	- SSH keys / agent contents (Linux/macOS hosts)
	- Cloud / SaaS credentials cached in process memory (AWS, Azure, GCP, OAuth refresh tokens)
	- Browser-resident session data (cookies, decrypted passwords)
	- Evidence of credential dumping tooling (mimikatz, procdump targeting LSASS, secretsdump, lsassy)

4. Identify In-Memory Persistence
	- Review:
		- Reflective DLL loading
		- Process hollowing
		- APC injection
		- Memory-only payloads
		- Kernel callbacks / driver injection

## 3. Post-Action
- Document findings and new IOCs in the incident ticket
- Share IOCs and TTPs with threat intelligence and detection engineerin
- Retain the memory image per evidence retention policy

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.