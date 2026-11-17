# Incident Investigation — Suspicious Authentication Activity

**Status:** Completed
**Project Type:** Hands-on Cybersecurity Investigation
**Environment:** Ubuntu Linux
**Case ID:** NS-2026-001
**Organization:** Northstar Solutions (Fictional)

## Overview

This project is a hands-on cybersecurity investigation focused on suspicious SSH authentication activity on a fictional Linux server.

The investigation examined synthetic authentication records, identified potentially suspicious patterns, correlated events, reconstructed an incident timeline, assessed privileged activity, and documented the findings in a technical incident report.

The project was designed as a safe, reproducible learning exercise using fictional scenarios and synthetic evidence. No production systems or real user credentials were involved.

## Scenario

Northstar Solutions is a fictional technology services company with approximately 30 employees.

The investigation focused on suspicious authentication activity involving an Ubuntu server:

- Multiple failed SSH password authentication messages.
- An invalid user attempt.
- A subsequent successful authentication for an existing account from a different IP address.
- A privileged command request involving `/etc/shadow`.
- Subsequent session closure records.

The investigation did not assume that an intrusion had occurred. Its purpose was to determine what the available evidence could establish and identify the remaining uncertainties.

## Objectives

The project aimed to develop practical skills in:

- Linux authentication log analysis.
- Identification and interpretation of failed and successful SSH authentication events.
- Correlation of users, source IP addresses, timestamps, and process identifiers.
- Incident timeline reconstruction.
- Evidence-based security analysis and hypothesis development.
- Basic MITRE ATT&CK mapping.
- Technical incident reporting and documentation.
- Recognition of evidence limitations and investigative gaps.

## Scope

The investigation included:

- Examination of a synthetic Linux authentication log.
- Identification and interpretation of relevant authentication events.
- Event correlation and timeline reconstruction.
- Analysis of privileged activity.
- Assessment of alternative explanations and potential security implications.
- Identification of findings, limitations, and evidence gaps.
- MITRE ATT&CK behavioral mapping.
- Preparation and validation of a technical incident investigation report.

The project did not include production-system investigation, enterprise SIEM deployment, real attack simulation, or unauthorized testing against third-party systems.

## Methodology

The investigation followed a structured process:

1. Define the incident scenario and investigation objectives.
2. Inspect the available Linux environment and establish the evidence approach.
3. Prepare and validate a synthetic authentication dataset.
4. Inventory and examine the evidence.
5. Correlate events and reconstruct the investigation timeline.
6. Document findings, hypotheses, and evidence gaps.
7. Perform technical analysis and cautious MITRE ATT&CK mapping.
8. Prepare and validate the final incident investigation report.

## Tools and Technologies

Tools and commands used during the project included:

- **Ubuntu Linux:** working environment.
- **Linux Terminal:** command-line investigation workflow.
- **grep:** filtering and examining relevant log entries.
- **wc:** counting records.
- **file:** identifying file format.
- **sha256sum:** calculating the evidence file hash.
- **Git and GitHub:** version control and project documentation.

The investigation prioritized simple, transparent, and reproducible command-line procedures rather than introducing unnecessary infrastructure.

## Key Findings

The synthetic evidence showed:

- Three failed password authentication messages for `j.smith` from `198.51.100.24`.
- An invalid user attempt involving `admin2` from the same IP address.
- A successful SSH authentication for `j.smith` from `203.0.113.45`.
- A sudo command request targeting `/etc/shadow`.
- Subsequent privileged and SSH session closure records.

The authentication sequence and privileged command request were considered suspicious and worthy of further investigation.

However, the available evidence did not establish:

- The identity of the human operator.
- Whether the successful authentication was authorized.
- Whether the failed and successful authentication events involved the same operator.
- Whether the requested command completed successfully.
- Whether sensitive information was retrieved or exfiltrated.

**Final Assessment:** Suspicious activity was identified, but unauthorized access and security compromise could not be confirmed based on the available synthetic evidence.

## MITRE ATT&CK Mapping

The investigation compared observed behaviors with:

- **T1110 — Brute Force:** repeated failed authentication messages were behaviorally compatible with this technique, but adversarial intent was not established.
- **T1548.003 — Sudo and Sudo Caching:** sudo activity was recorded, but abuse of the privilege-escalation mechanism was not confirmed.

These mappings are analytical references, not confirmation of adversarial activity.

## Repository Structure

```text
incident-investigation-auth/
├── README.md
├── .gitignore
├── docs/
│   └── project-brief.md
├── evidence/
│   ├── sanitized/
│   │   └── authentication.log
│   ├── evidence-inventory.md
│   ├── event-correlation.md
│   ├── investigation-timeline.md
│   ├── findings-and-gaps.md
│   ├── authentication-pattern-analysis.md
│   ├── privileged-activity-analysis.md
│   └── mitre-attack-mapping.md
└── reports/
    └── incident-report.md
```

## Final Report

The complete technical investigation report is available at:

`reports/incident-report.md`

It consolidates the investigation context, evidence sources, timeline, technical analysis, MITRE ATT&CK mapping, findings, recommendations, and limitations.

## Safety and Ethical Considerations

- All scenarios and log data are fictional or synthetic.
- No unauthorized access or testing against third-party systems was performed.
- No real user credentials or production evidence were used.
- The project was designed around safe evidence examination and documentation.
- The limitations of the synthetic dataset are explicitly documented.

## Learning Outcomes

This project provided practical experience in:

- Examining and interpreting Linux authentication records.
- Correlating events and reconstructing timelines.
- Distinguishing observed facts from hypotheses.
- Assessing privileged activity without assuming successful execution.
- Applying MITRE ATT&CK cautiously.
- Documenting evidence limitations and investigative gaps.
- Producing a structured technical incident investigation report.
- Maintaining a reproducible project through Git and GitHub.

The project follows an MVP-oriented approach, prioritizing practical understanding, evidence-based reasoning, and technical defensibility over unnecessary complexity.
