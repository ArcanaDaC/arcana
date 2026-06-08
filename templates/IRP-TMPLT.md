# Incident Response Plan (IRP) Template

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | [Enter KB title] | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

### Purpose

> **Guidance:** A statement explaining why the IRP exists and what it aims to achieve. 

**Example:**

This Incident Response Plan (IRP) establishes the policies and procedures to ensure that [Organisation Name] can timely and effectively address computer security incidents that may compromise sensitive data or personally identifiable information (PII), or result in disruption to business operations or the achievement of organisational objectives.
### Scope

> **Guidance:** Defines what this IRP applies to and what it does NOT cover. Clearly delineate the systems, environments, and organisational boundaries that fall under this plan.

**Example:**

This IRP applies to all information systems classified within the organisation's operational boundary. It covers:
* All production and corporate environments
* Cloud-hosted and on-premises infrastructure
* Third-party integrations and services within scope

This IRP does **not** cover:
* Reliability Incidents
* Physical Security Incidents
* Fraud Investigations
* General Crisis Management and Non-Security PR Crises (Note: While the IRP includes steps for communicating about a cyber breach, this does not include non-cyber public relations crises).


## 2. Security Incident Response Team (SIRT) Mission & Constituency

### 2.1 Mission Statement

> **Guidance**: Define the primary goal of the IR team. Explain why the team exists, whom it serves and the core outcomes it is accountable for. 

**Example**:

The mission of the [Organisation Name] Security Incident Response Team (SIRT) is to defend the organisation, its employees, and its customers from security threats. This is achieved by maintaining a high state of operational readiness, coordinating swift responses to manage risk and minimise customer impact, and driving continuous improvement through thorough post-incident reviews designed to identify corrective actions and prevent future incidents.

### 2.2 Constituency
> **Guidance**: Clearly define the group of users, systems, and entities that the Security Incident Response Team is mandated to protect.

The [Organisation Name] SIRT serves a dual constituency which includes:
* [Organisation Name]'s internal constituency which consist of all [Organisation Name] departments, employees and internal systems
* [Organisation Name]'s external constituency which consist of [Organisation Name]'s customers

## 3. Incident Response Policy
> **Guidance**: Link to your organisation's governing Incident Response 
> Policy document. The IR Policy is the executive-approved document that 
> establishes the organisational mandate, authority, and governance 
> structure for incident response. This IRP serves as the operational 
> implementation of that policy.
>
> If your organisation does not yet have a standalone IR Policy, 
> reference the relevant section of your broader Information Security 
> Policy or Security Program Charter that authorises security incident response 
> activities.

**Example**:
[Organisation Name]'s Security Incident Response Policy, created on [creation date], can be found at [IR Policy URL]

## 4. Definitions

> **Guidance:** Define key terms used throughout the plan to establish a shared vocabulary across all stakeholders. This eliminates ambiguity during high-stress incident situations. 

| Term | Definition |
| --- | --- |
| Security Incident Response Team (SIRT) | The dedicated team responsible for detecting, responding to, and recovering from security incidents on behalf of the organisation |
| Incident Response Plan (IRP) | This document; the formal plan that defines the SIRT's processes, roles, and procedures for managing security incidents |
| Event | An occurrence in an information system or network that may negatively affect operations but has not yet been confirmed as an incident |
| Security Incident | A confirmed or suspected event that results in an intentional negative impact on confidentiality, integrity, or availability of organisational data or services |
| Attack Vector | The method or means by which a threat actor gains unauthorised access |
| Indicators of Compromise (IOC) | Artifacts or evidence that indicate an incident may have occurred or is currently occurring |
| Vulnerability | A weakness in a system, process, or control that could be exploited by a threat source |
| Threat | Any circumstance, event, or actor with the potential to adversely impact operations, assets, or personnel |
| Threat Source | The intent and method targeted at exploiting a vulnerability |

## 5. Roles & Responsibilities

> **Guidance:** Define the organisational structure of the SIRT during both the preparation phase and during active incidents. For each role, describe the responsibilities, authority, and escalation paths. Include both primary and alternate personnel to ensure continuity. This section should cover two contexts:
>
> 1. **Preparation phase** – Who maintains readiness, training, tools, and the plan itself
> 2. **During an incident** – Who manages, investigates, communicates, and makes decisions

### 5.1 SIRT Structure
> **Guidance:** Insert or reference organisational chart showing the IR team hierarchy.

### 5.2 Preparation Phase Roles

| Role | Responsibilities |
| --- | --- |
| Executive Sponsor / CISO | Strategic ownership, funding, escalation authority, board-level reporting |
| IR Program Manager | Maintains the IRP, coordinates exercises, ensures compliance, manages team readiness |
| IR Team Leads | Develop and maintain playbooks, assign work, conduct quality assurance, mentor analysts |
| IR Analysts (On-Call) | Monitor alerts, perform initial triage, escalate confirmed incidents, document findings |
| IR Analysts (Dedicated) | Develop and maintain playbooks, work investigations, develop automations, improve tooling, execute projects |
| Security Operations (SOC) | 24/7 triage of alerts, phishing reports; escalate events to IR |
| System Administrators | Perform directed mitigation actions, provide SME knowledge, cooperate with IR |
| All Users | Report suspicious activity, cooperate with IR, follow security policies |

### 5.3 During-Incident Roles

| Role | Responsibilities |
| --- | --- |
| Incident Manager | Manages the overall incident response, delegates streams, tracks workloads, makes key decisions, drives communications |
| IR Analysts | Complete investigation and remediation tasks, document progress, contribute to post-incident review |
| Legal Counsel | Assesses reporting obligations, reviews external communications, engages external counsel as needed |
| Communications Team | Drafts internal/external communications, coordinates with legal and leadership |
| Product/Engineering Teams | SMEs for affected systems, implement containment/eradication/recovery actions |
| Executive Leadership | Business impact SME, consulted on large-impact decisions |

### 5.4 Line of Succession

> **Guidance:** Document the order of succession for key decision-makers to ensure continuity if primary personnel are unavailable. Alternates should be trained and notified of their standby role.

## 6. Applicable Laws, Regulations, and Standards

> **Guidance:** List all laws, regulations, frameworks, and organisational policies that govern or inform your incident response activities. This section ensures the IRP is aligned with compliance requirements and provides auditors with traceability. Tailor to your jurisdiction and industry.

**Examples of applicable laws:**
* General Data Protection Regulation (GDPR)
* Health Insurance Portability and Accountability Act (HIPAA)
* Federal Information Security Modernisation Act (FISMA)
* Payment Card Industry Data Security Standard (PCI DSS)
* Applicable state/national breach notification laws

**Examples of applicable standards and guidance:**
* NIST SP 800-61, Rev. 2 – Computer Security Incident Handling Guide
* NIST SP 800-37 – Risk Management Framework
* NIST SP 800-53 – Security and Privacy Controls
* ISO/IEC 27001 – Information Security Management
* ISO/IEC 27035 – Incident Management
* NIST SP 800-86 – Guide to Integrating Forensic Techniques into Incident Response


## 7. Incident Response Lifecycle

### 7.1 Preparation

> **Guidance:** Describe how the organisation prepares for incidents before they occur. This includes training programs, exercises, tool acquisition, team structure, and preventive controls. The goal is to minimise the number and impact of incidents while ensuring readiness.

#### Personnel Training

> **Guidance:** Detail the training requirements for IR personnel. Examples include:
> * Role-specific IR training (within first 30-90 days)
> * Security incident management training
> * Shadowing and mentorship for new hires
> * Security awareness training for all staff
> * Professional certifications funded through the organisation's annual training budget

#### Tests and Exercises

> **Guidance:** Describe the types and frequency of IR exercises the organisation conducts. Include at minimum one exercise per year. Types may include:
> * **Red Team Operations** – Full-scope adversary simulations testing detection and response
> * **Tabletop Exercises** – Facilitated scenario-based discussions to test decision-making and coordination
> * **Purple Team Exercises** – Collaborative attack/defense exercises to improve detections
>
> Document how deficiencies found during exercises are tracked and remediated.

#### Incident Response Retainer

> **Guidance:** Describe any third-party IR retainer agreements. Include the provider, coverage period, prepaid hours, activation process, expected response SLAs, and authorised personnel who can invoke the retainer.

---

### 7.2 Detection & Reporting

> **Guidance:** Describe how potential incidents are detected and reported to SIRT. Cover automated detection systems, manual reporting channels, and external reporting mechanisms.

#### Sources of Events

> **Guidance:** List all channels through which security events may be identified. Examples include:
> * SIEM alerts and automated detections
> * Findings from hunts
> * Internal employee reports (chat channels, service desk tickets, email)
> * Customer reports via support portals
> * External partner/vendor notifications
> * Vulnerability disclosure programs (bug bounty)
> * Threat intelligence feeds and public domain research

#### Internal Reporting Procedures

> **Guidance:** Describe how all personnel are expected to report suspected security events. Include the reporting channels (e.g., dedicated Slack channel, ticketing system, email address) and examples of reportable events:
> * Automated alerts or error messages indicating potential compromise
> * Observations of anomalous or unexpected system behavior
> * Indications of malware, phishing, or unauthorised access
> * Reports received from external parties

#### Incident Classification and Severity Matrix

> **Guidance:** Define how events are triaged and classified into severity levels. Provide a matrix that maps incident characteristics to severity ratings. The matrix should consider:
> * Security attributes impacted (Confidentiality, Integrity, Availability)
> * Affected surface (customer impact, corporate impact)
> * Observed threat actor actions (recon, exploitation, persistence, lateral movement, exfiltration)
> * Privacy/legal implications
> * Reputational impact

**Example Severity Matrix:**
| Severity | Description | Characteristics |
| :--- | :--- | :--- 
| **0**| A critical security incident with maxium organisational impact | <ul><li>High Impact on C, I, A</li><li>High Customer Impact</li><li>High Corporate Impact</li><li>Has Privacy Impact</li><li>May have Reputation Impact</li><li>Observed Actions<ul><li>lateral movement</li><li>data exfiltration</li><li>data destruction</li></ul></ul>|
| **1** | A major security incident with very high impact | <ul><li>Medium - High Impact on C, I, A</li><li>Medium - High Customer Impact</li><li>Medium - High Corporate Impact</li><li>May have Privacy Impact</li><li>May have Reputation Impact</li><li>Observed Actions<ul><li>persistence</li><li>C&C Activity</li><li>data exfiltrations</li><li>lateral movement</li></ul></ul>|
| **2** | A major security incident with moderate impact | <ul><li>Low - High Impact on C, I, A</li><li>Low - Medium Customer Impact</li><li>Low - Medium Corporate Impact</li><li>May have Privacy Impact</li><li>May have Reputation Impact</li><li>Observed Actions<ul><li>exploitation</li><li>persistence</li><li>C&C activity</li><li>data exfiltration</li><li>data exposure</li></ul></ul>  |
| **3** | A minor security incident with low impact | <ul><li>Low - High Impact on C, I, A</li><li>No Customer Impact</li><li>No/Low Corporate Impact</li><li>No Privacy Impact</li><li>No Reputation Impact</li><li>Observed Actions<ul><li>recon</li><li>delivery</li><li>exploitation</li><li>data exposure</li></ul></ul> 


### 7.3 Analysis & Triage

> **Guidance:** Describe the analysis process once an event is triaged and assigned. This section covers how the team investigates, determines scope, identifies root cause, and classifies the incident. Key activities include:
> * Hypothesis-based investigation approach
> * Identification of TTPs, root cause, and attribution
> * Documentation of all analysis in the incident tracking system
> * Escalation of significant findings to the Incident Manager
> * Classification of events (false positive, confirmed incident, privacy incident, etc.)

#### Evidence Collection and Preservation

> **Guidance:** Describe requirements for collecting and preserving evidence during analysis. Include:
> * Chain of custody requirements
> * Evidence logging (what was collected, by whom, when, from where)
> * Forensic imaging and memory capture procedures
> * Legal admissibility considerations

#### Information Spillage Response

> **Guidance:** Describe how the organisation handles information spillage (classified or sensitive data transferred to unauthorised systems). Include steps for:
> * Gathering information about the spillage
> * Coordinating with legal, engineering, and relevant teams
> * Removing leaked information and fixing the root cause
> * Investigating whether the leaked information was accessed or exploited


### 7.4 Containment, Eradication & Recovery

> **Guidance:** Describe how confirmed incidents are contained, threats are eliminated, and normal operations are restored. All actions taken against affected systems must be coordinated through the Incident Manager to avoid destroying evidence or alerting threat actors. Define SLAs for containment where applicable.

#### Containment

> **Guidance:** Actions taken to prevent further adverse impact. Include:
> * Short-term (immediate) containment – emergency actions to stop active damage
> * Long-term containment – sustained measures while investigation continues
> * Evidence preservation during containment
> * Coordination with system owners before taking action

#### Eradication

> **Guidance:** The complete removal of attacker artifacts and access from the environment. Include:
> * Removal of malware, backdoors, unauthorised accounts
> * Patching exploited vulnerabilities
> * Credential resets for compromised accounts
> * Validation that all attacker footholds are eliminated

#### Recovery

> **Guidance:** Restoration of affected systems and services to normal operations. Include:
> * System restoration and rebuild procedures
> * Validation of system integrity before returning to production
> * Enhanced monitoring for recurrence
> * Communication of service restoration to stakeholders


### 7.5 Post-Incident Activities

#### Post-Incident Review (PIR)

> **Guidance:** Describe the process for conducting post-incident reviews. PIRs should follow a blameless approach and aim to understand contributing root causes, document the incident, and implement actions that improve detection, response, prevention, and overall readiness. Define:
> * Which severity levels require a PIR (recommend mandatory for Sev 2 or greater)
> * Timeline SLAs for drafting and approving the PIR
> * Who is responsible for authoring and approving

**PIR Content Requirements:**
* Incident summary
* Lead-up and contributing factors
* Impact assessment (quantitative where possible)
* Detection, response, and recovery narrative
* Timeline of events
* Root cause analysis (e.g., Five Whys)
* Lessons learned
* Corrective actions with owners and priority

## 8. Communication & Notification

> **Guidance:** Define how the organisation communicates internally and externally during incidents. Separate internal coordination from regulated external notifications.

### Internal Communication

> **Guidance:** Describe the protocols for communicating incident status within the organisation. Include:
> * Who is notified at each severity level
> * Communication channels used (war room, chat, email, bridge calls)
> * Frequency of status updates
> * Information classification (need-to-know basis)

### External Notification

> **Guidance:** Describe obligations and procedures for notifying external parties. Include:
> * Regulatory notification requirements and timelines (e.g., 72 hours for GDPR, 1 hour for FedRAMP)
> * Customer notification criteria and channels
> * Law enforcement engagement criteria
> * CERT/CSIRT reporting requirements
> * Public relations and media handling

### Engagement of External Teams

> **Guidance:** Provide a table of commonly engaged internal and external teams with their contact methods. This enables rapid engagement during an active incident.

| Team / Contact | How to Engage |
| --- | --- |
| Legal Counsel | [Channel/method] |
| Communications/PR | [Channel/method] |
| IT/Infrastructure | [Channel/method] |
| Product Engineering | [Channel/method] |
| HR / Employee Relations | [Channel/method] |
| External IR Retainer | [Hotline/method] |
| Regulatory Bodies | [Reporting portal/method] |


## 9. Documentation & Evidence Handling

> **Guidance:** Define requirements for documenting all incident-related actions, decisions, and communications. Specify how evidence is handled to maintain integrity and support potential legal proceedings. Include:
> * Incident ticket/record content requirements (status, summary, indicators, actions, impact, communications, next steps)
> * War-room tracking document structure (timeline, evidence log, indicators, systems of interest, compromised accounts)
> * Chain of custody procedures
> * Evidence retention periods
> * Digital forensic standards followed


## 10. Metrics & Incident Classification for Reporting

### 10.1 Metrics

> **Guidance:** Define the metrics collected from incident data to measure the IR program's effectiveness. Metrics should be used to justify resources, identify trends, and drive improvement. Examples:
> * Number of alerts, investigations, and confirmed incidents
> * Mean time to detect (MTTD)
> * Mean time to contain (MTTC)
> * Mean time to resolve (MTTR)
> * Incidents by discovery method, severity, and control failure category
> * PIR completion rates and corrective action closure rates

### 10.2 Incident Classification for Reporting
> **Guidance:** Define how incidents are classified for internal and external reporting. This feeds metrics, trend analysis, and compliance reporting. Include categories such as:
> * **Confidence level** – Confirmed / Suspected 
> * **Targeting** – Opportunistic / Targeted / Unknown
> * **Threat actor type** – External / Internal  / Other
> * **Control failure** – Account compromise / Malware / Vulnerability / Data exposure / Social engineering / Third-party incident / etc.
> * **Discovery method** – SIEM alert / Internal report / Customer report / Bug bounty / External source / Hunt
> * **Attack technique** – Map to MITRE ATT&CK where applicable
> * **Key dates** – Identification, compromise, containment, notification


## 11. Review & Maintenance

> **Guidance:** Define how the IRP itself is kept current. Include:
> * Annual review cycle and responsible owner
> * Triggers for ad-hoc updates (major incidents, org changes, new regulations)
> * Audit procedures and automation
> * Change log and approval process
> * Distribution list for updated versions


## 12. Coordination & Information Sharing

> **Guidance:** Describe how the organisation collaborates with external entities for threat intelligence sharing and mutual support. Include:
> * Industry information sharing groups (ISACs, ISAOs)
> * Trusted partner relationships
> * Government and law enforcement coordination
> * Rules for sharing threat/vulnerability information externally


## 13. Plan Distribution & Availability

> **Guidance:** Describe how the IRP is distributed and made accessible to authorised personnel. Include:
> * Where the plan is stored (secure wiki, document management system)
> * Who has access
> * Offline/backup availability for major outages
> * Classification level of the document


## 14. Appendices
