# Project Brief
## Incident Investigation — Suspicious Authentication Activity

**Project ID:** NS-2026-001  
**Project Status:** In Progress  
**Project Type:** Hands-on Cybersecurity Investigation  
**Primary Environment:** Ubuntu Linux  
**Repository:** `incident-investigation-auth`

---

## 1. Project Overview

This project consists of a practical cybersecurity incident investigation focused on suspicious SSH authentication activity on a Linux server.

The project simulates a real-world investigation scenario in which an analyst must examine authentication events, identify potentially suspicious behavior, correlate available evidence, reconstruct an incident timeline, evaluate possible security implications, and document the findings in a professional technical report.

The investigation will use a fictional organization and synthetic log data to provide a safe, controlled, reproducible, and practical learning environment.

The primary goal is to develop practical incident investigation skills while building a documented cybersecurity portfolio project.

## 2. Problem Statement

Repeated failed authentication attempts, followed by a successful login under circumstances that require further investigation, may indicate suspicious access activity.

However, failed authentication attempts alone do not confirm an intrusion.

The investigation must determine:

- What happened?
- Which accounts and source IP addresses were involved?
- When did the relevant events occur?
- Is there evidence of unauthorized access?
- Did any potentially suspicious activity occur after authentication?
- What impact, if any, can be supported by the available evidence?

The investigation must distinguish confirmed facts from assumptions and hypotheses.

## 3. Incident Scenario

### 3.1 Fictional Organization

**Organization:** Northstar Solutions

Northstar Solutions is a fictional technology services company with approximately 30 employees.

The company operates a small IT environment with a Linux server used to support internal services.

### 3.2 Target System

| Attribute | Description |
|---|---|
| Case ID | NS-2026-001 |
| Hostname | ns-ubuntu-srv01 |
| Operating System | Ubuntu Server |
| Remote Access | OpenSSH / SSH |
| Environment | Small business IT infrastructure |
| User Accounts | Individual user accounts |
| Administration | Small IT administrator group |

### 3.3 Incident Description

The server has recorded multiple failed SSH authentication attempts associated with a user account.

A subsequent successful login occurred under circumstances that require further examination.

The investigation will also consider whether any potentially suspicious administrative or post-authentication activity occurred.

At the beginning of the investigation, unauthorized access is a hypothesis, not a confirmed conclusion.

The analyst must evaluate the evidence before determining whether the activity represents a security incident.

## 4. Project Objectives

The project aims to develop five practical competencies.

### 4.1 Log Analysis

- Locate and inspect Linux authentication logs.
- Identify failed and successful SSH authentication events.
- Interpret timestamps, usernames, source IP addresses, and event context.
- Apply basic filtering and text-processing commands.

### 4.2 Incident Investigation

- Identify relevant events.
- Correlate authentication records.
- Reconstruct the sequence of activities.
- Build an evidence-based incident timeline.

### 4.3 Security Analysis

- Develop and evaluate investigation hypotheses.
- Recognize potentially suspicious authentication patterns.
- Assess possible impact based on available evidence.
- Distinguish facts, assumptions, and unknown information.

### 4.4 Security Frameworks

- Understand the basic purpose of MITRE ATT&CK.
- Identify relevant techniques when supported by the evidence.
- Avoid assigning techniques without sufficient justification.

### 4.5 Technical Reporting

- Document the investigation methodology.
- Present relevant evidence and findings.
- Explain conclusions and limitations.
- Produce a professional technical incident report in English.

## 5. Project Scope

### 5.1 In Scope

The initial MVP includes:

- Analysis of synthetic Linux authentication logs.
- Identification and interpretation of relevant SSH events.
- Filtering and correlation of authentication records.
- Analysis of users, IP addresses, timestamps, and event context.
- Incident timeline reconstruction.
- Development and evaluation of investigation hypotheses.
- Basic MITRE ATT&CK mapping when appropriate.
- Technical reporting and recommendations.

### 5.2 Out of Scope

The following activities are excluded from the initial MVP:

- Full enterprise infrastructure deployment.
- Enterprise-scale SOC or SIEM implementation.
- Splunk, Elastic Stack, or Wazuh deployment.
- Complex offensive security tooling.
- Attacks against third-party systems.
- Real unauthorized access or account compromise.
- Windows event investigation in this first project.

Additional technologies may be considered in future extensions if they provide clear practical value.

## 6. Environment and Tools

The project will follow a Linux-first approach using the existing Ubuntu environment.

### 6.1 Initial Tools

| Tool | Intended Purpose |
|---|---|
| Ubuntu Linux | Primary operating environment |
| Linux Terminal | Command execution and investigation |
| `journalctl` | Inspection of system journal logs |
| `grep` | Searching and filtering log content |
| `awk` | Basic text processing and extraction |
| Git | Version control |
| GitHub | Project documentation and portfolio |

Python may be introduced later if it provides a meaningful improvement to the investigation workflow.

The actual logging configuration will be verified before selecting the appropriate log sources. The project will not assume that a particular authentication log file or logging service is available.

## 7. Investigation Methodology

The investigation will follow six main stages.

### Stage 1 — Project Definition

- Define the investigation scenario.
- Establish objectives and scope.
- Identify expected deliverables.
- Define success criteria and safety constraints.

### Stage 2 — Lab Preparation

- Verify the existing Linux logging configuration.
- Select the simplest suitable environment.
- Prepare synthetic authentication evidence.
- Validate that the evidence can be inspected and analyzed.
- Document the environment and procedures.

### Stage 3 — Evidence Investigation

- Examine authentication records.
- Identify relevant events.
- Apply filtering and search techniques.
- Correlate timestamps, users, and source IP addresses.
- Build the incident timeline.

### Stage 4 — Technical Analysis

- Develop investigation hypotheses.
- Evaluate suspicious patterns.
- Identify possible attack techniques when justified.
- Assess potential impact and evidence limitations.
- Separate confirmed facts from assumptions.

### Stage 5 — Reporting and Validation

- Prepare the technical incident report.
- Document methodology and evidence.
- Present findings and conclusions.
- Provide justified recommendations.
- Review the investigation for accuracy and reproducibility.

### Stage 6 — Portfolio Preparation

- Organize the GitHub repository.
- Prepare an English README.
- Include sanitized evidence and documentation.
- Ensure that the investigation can be reproduced.
- Review the project from a SOC analyst or recruiter perspective.

## 8. Safety and Ethical Constraints

The project must comply with the following principles:

- Use only fictional scenarios and synthetic or legitimately provided training data.
- Do not perform unauthorized activity against real systems.
- Begin with read-only analysis whenever possible.
- Do not modify the host authentication configuration during the initial investigation.
- Perform any controlled event generation only in an isolated and authorized environment.
- Review and sanitize evidence before publishing it.
- Do not present assumptions as confirmed findings.

## 9. Expected Deliverables

The project is expected to produce:

1. Synthetic Linux authentication log dataset.
2. Documented investigation commands and procedures.
3. Evidence-based incident timeline.
4. Technical analysis and investigation hypotheses.
5. Basic MITRE ATT&CK mapping, when supported by evidence.
6. Professional incident investigation report in English.
7. Organized and reproducible GitHub repository.
8. Sanitized evidence suitable for portfolio presentation.

## 10. Success Criteria

The project will be considered successful when the following criteria are met.

| ID | Criterion | Expected Result |
|---|---|---|
| SC-01 | Evidence collection and interpretation | Relevant log events are identified and explained. |
| SC-02 | Suspicious behavior identification | Potentially suspicious events are listed and justified. |
| SC-03 | Event correlation and timeline | A coherent chronology is supported by evidence. |
| SC-04 | Technical analysis | Hypotheses, facts, assumptions, and unknowns are clearly distinguished. |
| SC-05 | Tool usage | Commands and procedures are documented and reproducible. |
| SC-06 | Professional reporting | A complete and coherent technical report is produced. |
| SC-07 | Portfolio presentation | The repository is organized, documented, and reproducible. |

## 11. Learning and Autonomy Assessment

The project is designed to evaluate both technical understanding and the ability to conduct an investigation.

Three autonomy levels will be considered:

- **Guided:** The activity can be completed with step-by-step guidance.
- **Assisted:** The activity can be performed with documentation or AI support, while the analyst understands the decisions and procedures.
- **Independent:** The analyst can explain and execute the main activities autonomously.

Full independence is not a requirement for every competency in this initial project.

The final assessment will identify demonstrated strengths, remaining knowledge gaps, and areas requiring further practice.

## 12. Learning and Execution Approach

The project will follow a practical, incremental, MVP-oriented approach.

Each stage will include:

- A clear objective.
- Relevant technical concepts.
- Practical execution.
- Explanation of what, how, and why.
- Verification of results.
- Evidence of completion.
- Suggestions for improvement.

AI assistance and technical documentation may be used as learning resources. However, the analyst must understand the purpose, operation, output, and limitations of the tools and commands used.

The emphasis is on developing investigative reasoning rather than simply executing commands.

## 13. Portfolio Presentation

The GitHub repository will serve as the central location for project documentation, evidence, and deliverables.

The repository will initially remain private during development.

Before any public release, all materials must be reviewed to ensure that they contain no sensitive information, personal data, or unintended system details.

The final project should demonstrate practical investigation skills, analytical reasoning, evidence handling, technical documentation, and the ability to explain investigative decisions.

---

**Document Status:** Initial Project Brief — Approved  
**Project Case:** NS-2026-001
