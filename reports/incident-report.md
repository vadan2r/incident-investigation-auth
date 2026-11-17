# Incident Investigation Report

**Case ID:** NS-2026-001  
**Organization:** Northstar Solutions  
**Target Host:** ns-ubuntu-srv01  
**Investigation Date:** November 16, 2026  
**Evidence Type:** Synthetic Linux Authentication Log  
**Investigation Status:** Completed — No Confirmed Compromise

---

## 1. Executive Summary

This investigation examined suspicious SSH authentication activity involving the account `j.smith` on the fictional server `ns-ubuntu-srv01`.

The synthetic authentication records show multiple failed login attempts, an invalid user attempt, a subsequent successful authentication from a different IP address, and a privileged command request involving `/etc/shadow`.

These events represent potentially suspicious activity and warrant security attention. However, the available evidence does not establish that the successful login was unauthorized, that the account was compromised, or that the contents of `/etc/shadow` were successfully retrieved.

**Conclusion:** Suspicious authentication and privileged activity were identified, but a security compromise cannot be confirmed based on the available evidence.

## 2. Incident Overview

The investigation focused on a fictional authentication incident at Northstar Solutions, involving one Ubuntu server using OpenSSH.

**Investigation objectives:**

- Examine failed and successful SSH authentication events.
- Correlate authentication events by account, IP address, timestamp, and process identifier where available.
- Examine recorded privileged activity.
- Identify potential security concerns and evidence gaps.
- Assess relevant behaviors against the MITRE ATT&CK framework.

**Scope:** The investigation was limited to the synthetic authentication dataset provided for this project.

No production systems, third-party infrastructure, or real user credentials were involved.

## 3. Evidence Sources

The primary evidence source was:

| Identifier | Description | Location |
|---|---|---|
| E-001 | Synthetic Linux Authentication Log | `evidence/sanitized/authentication.log` |

E-001 contains 12 log records covering the period from 09:10:12 to 09:31:23 (UTC-03:00) on November 16, 2026.

The dataset includes failed authentication attempts, an invalid user attempt, a successful SSH authentication, sudo activity, and session closure records.

The SHA-256 hash recorded during evidence inventory is:

`8d176d8905ae03b4c8608caf9d0bb8bbfa6c45c6d0087badcb3d4596d27abe3d`

The dataset is synthetic and does not represent an original forensic acquisition from a production server. Its integrity hash identifies the recorded file content but does not establish independent authenticity or collection history.

The hash was calculated during evidence inventory and is used to identify the recorded dataset content. It does not independently establish the authenticity of the original source.

## 4. Investigation Timeline

All timestamps are presented in UTC-03:00.

| Time | Event | Evidence Reference |
|---|---|---|
| 09:10:12–09:11:08 | Three failed SSH password authentication messages for `j.smith` from `198.51.100.24` | E-001, lines 1–3 |
| 09:13:42–09:13:45 | Invalid user `admin2` identified, followed by a failed password message from the same IP | E-001, lines 4–5 |
| 09:18:17 | Successful SSH password authentication for `j.smith` from `203.0.113.45` | E-001, line 6 |
| 09:18:18 | SSH session opened for `j.smith` | E-001, line 7 |
| 09:23:04 | Sudo command request involving `/usr/bin/cat /etc/shadow`; privileged session opened | E-001, lines 8–9 |
| 09:23:05 | Privileged session closed | E-001, line 10 |
| 09:31:22–09:31:23 | SSH session closed and disconnection recorded | E-001, lines 11–12 |

The interval between successful authentication and recorded disconnection was approximately 13 minutes and 6 seconds.

The records do not establish who initiated the disconnection or what activity occurred throughout the entire session.

## 5. Technical Analysis

### 5.1 Authentication Pattern

Three failed password authentication messages for `j.smith` originated from `198.51.100.24`.

An invalid user attempt involving `admin2` was also recorded from that address. The invalid user identification and subsequent failed password message are separate log records associated with the same process; they should not automatically be counted as two independent attempts.

A successful authentication for `j.smith` was subsequently recorded from `203.0.113.45`, approximately 4 minutes and 32 seconds after the last recorded failed attempt.

This sequence warrants investigation. However, the different source IP addresses do not establish that the events involved different people or that the successful login was unauthorized.

Possible explanations include a change of network, device, VPN connection, or unrelated activity by different operators. None can be confirmed from the available records.

### 5.2 Privileged Activity

At 09:23:04, a sudo record shows that `j.smith` requested execution of:

`/usr/bin/cat /etc/shadow`

The logs also record the opening and closing of a privileged session for `root`.

The requested command targets a sensitive Linux system file containing password-related information.

Although `j.smith` is identified as an administrative account, this does not establish that the activity was legitimate or authorized.

The available records do not independently confirm successful command execution, retrieval of file contents, copying, or data exfiltration.

### 5.3 Overall Technical Assessment

The evidence identifies two relevant areas for further examination:

- An authentication sequence involving repeated failures followed by successful access from a different IP address.
- A privileged command request involving a sensitive system file.

These observations justify further investigation, but they are insufficient to establish account compromise, unauthorized access, or data theft.

## 6. MITRE ATT&CK Mapping

The observed behaviors were compared with the following MITRE ATT&CK techniques.

### T1110 — Brute Force

**Tactic:** Credential Access

Multiple failed SSH password authentication messages are compatible with behavior associated with brute-force attempts.

However, the available records do not establish the intent behind the attempts or confirm a successful brute-force attack.

**Assessment:** Behavioral similarity observed; adversarial technique not confirmed.

### T1548.003 — Sudo and Sudo Caching

**Tactic:** Privilege Escalation

The logs record a sudo command request targeting a sensitive system file.

However, they do not establish abuse of the sudo mechanism or unauthorized privilege escalation.

**Assessment:** Sudo activity observed; technique abuse not confirmed.

These mappings are analytical references, not confirmation that an adversary performed the corresponding techniques.

References:

- https://attack.mitre.org/techniques/T1110/
- https://attack.mitre.org/techniques/T1548/003/

## 7. Findings and Recommendations

### 7.1 Key Findings

| Finding | Assessment |
|---|---|
| Multiple failed authentication messages | Observed |
| Invalid user attempt | Observed |
| Successful authentication from a different IP | Observed |
| Privileged command request involving `/etc/shadow` | Observed |
| Unauthorized access | Not established |
| Account compromise | Not established |
| Successful retrieval of `/etc/shadow` | Not established |
| Data exfiltration | Not established |

### 7.2 Recommendations

If this were a real incident, the following actions would be appropriate:

1. Review identity provider and MFA records, if available, to assess the legitimacy of the successful authentication.
2. Compare the source IP and device information with the user's legitimate access history.
3. Examine endpoint and system audit records to determine whether the requested command executed and whether sensitive file access occurred.
4. Review additional authentication, network, and system logs for related activity.
5. Preserve relevant evidence and maintain appropriate documentation of its origin and integrity.

These recommendations are investigative actions, not assertions that the suggested records exist or that compromise occurred.

## 8. Conclusion and Limitations

The investigation identified suspicious authentication activity and a privileged command request involving `/etc/shadow`.

The evidence supports the conclusion that:

- Multiple failed authentication messages were recorded.
- A successful SSH authentication for `j.smith` occurred from a different IP address.
- A sudo command request involving a sensitive system file was recorded.
- The associated SSH session was subsequently closed.

However, the available evidence does not establish:

- The identity of the human operator.
- Whether the successful authentication was authorized.
- Whether the failed and successful authentication events involved the same operator.
- Whether the requested command completed successfully.
- Whether sensitive information was retrieved or exfiltrated.

The investigation is limited by the use of synthetic data and the absence of independent identity, endpoint, network, and system audit records.

**Final Assessment:** Suspicious activity was identified, but unauthorized access and security compromise remain unconfirmed. Additional independent evidence would be required to support a stronger conclusion.

---

**Report prepared for:** Northstar Solutions — Case NS-2026-001  
**Project:** Incident Investigation — Suspicious Authentication Activity
