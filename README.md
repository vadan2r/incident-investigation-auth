# Incident Investigation — Suspicious Authentication Activity

**Status:** In Progress  
**Project Type:** Hands-on Cybersecurity Investigation  
**Environment:** Ubuntu Linux  
**Case ID:** NS-2026-001

## Overview

This project simulates a cybersecurity incident investigation involving suspicious SSH authentication activity on a Linux server.

The investigation focuses on analyzing authentication logs, identifying potentially suspicious patterns, correlating events, reconstructing an incident timeline, and documenting findings in a professional technical report.

The project uses a fictional organization and synthetic log data to provide a safe, reproducible, and practical learning environment.

## Scenario

Northstar Solutions is a fictional technology services company with approximately 30 employees.

Its Ubuntu server has experienced repeated failed SSH authentication attempts, followed by a successful login under circumstances that require further investigation.

The objective is to determine what happened, assess whether the available evidence suggests unauthorized access, and identify any potential impact.

An intrusion is not assumed or considered confirmed at the beginning of the investigation.

## Objectives

This project aims to develop practical skills in:

- Linux authentication log analysis.
- Identification and interpretation of failed and successful SSH logins.
- Correlation of users, source IP addresses, timestamps, and related events.
- Incident timeline reconstruction.
- Evidence-based security analysis and hypothesis development.
- Basic MITRE ATT&CK mapping, when supported by evidence.
- Technical incident reporting and documentation.

## Scope

The investigation includes:

- Analysis of synthetic Linux authentication logs.
- Identification of relevant authentication events.
- Event filtering and correlation.
- Timeline development.
- Investigation hypotheses and potential impact assessment.
- Technical findings and recommendations.

The initial project does not include enterprise-scale SIEM deployment, complex infrastructure, or testing against third-party systems.

## Methodology

The investigation follows a structured approach:

1. Define the incident scenario and investigation objectives.
2. Prepare a controlled environment and synthetic evidence.
3. Examine and filter relevant authentication events.
4. Correlate evidence and reconstruct the timeline.
5. Evaluate hypotheses and possible security implications.
6. Document findings in a technical incident report.
7. Organize the work for reproducibility and portfolio presentation.

## Tools and Technologies

The initial MVP may include:

- Ubuntu Linux
- Linux Terminal
- `journalctl`
- `grep`
- `awk`
- Git and GitHub

Additional tools, such as Python, may be introduced when they provide clear practical value.

## Safety and Ethical Considerations

- All scenarios and log data are fictional or synthetic.
- No unauthorized access or testing against third-party systems is performed.
- Initial analysis is designed to be read-only.
- Any controlled event generation will take place in an isolated and authorized environment.
- Evidence published in this repository will be reviewed and sanitized.

## Expected Deliverables

- Synthetic authentication log dataset.
- Documented investigation commands and procedures.
- Evidence-based incident timeline.
- Technical analysis and investigation hypotheses.
- Professional incident investigation report.
- Reproducible project documentation.

## Learning Approach

This project follows a practical, incremental, MVP-oriented approach.

The focus is not only on using tools, but also on understanding the evidence, explaining technical decisions, recognizing limitations, and developing an investigative mindset.

## Repository Status

The project is currently in its initial documentation and preparation stage.

Further investigation materials and deliverables will be added as the project progresses.
