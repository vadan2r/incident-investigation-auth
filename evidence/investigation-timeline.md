# Investigation Timeline

**Case ID:** NS-2026-001  
**Organization:** Northstar Solutions  
**Target Host:** ns-ubuntu-srv01  
**Evidence Source:** E-001 — Synthetic Linux Authentication Log  
**Date:** 2026-11-16  
**Timezone:** UTC-03:00

## Timeline of Events

| Time (UTC-03:00) | Event | Account | Source IP | Evidence Reference |
|---|---|---|---|---|
| 09:10:12–09:11:08 | Three failed SSH password authentication attempts | j.smith | 198.51.100.24 | E-001, lines 1–3 |
| 09:13:42–09:13:45 | Invalid user identification and failed password attempt | admin2 | 198.51.100.24 | E-001, lines 4–5 |
| 09:18:17–09:18:18 | Successful SSH authentication and session opening | j.smith | 203.0.113.45 | E-001, lines 6–7 |
| 09:23:04–09:23:05 | Sudo command request and privileged session opening/closing | j.smith / root | Not recorded | E-001, lines 8–10 |
| 09:31:22–09:31:23 | SSH session closure and disconnection | j.smith | 203.0.113.45 | E-001, lines 11–12 |

## Analytical Notes

### 1. Failed Authentication Activity

Three failed password authentication messages were recorded for the valid account `j.smith`, originating from `198.51.100.24`.

### 2. Invalid User Attempt

The logs record an invalid user identification for `admin2`, followed by a failed password message. These two records are associated with the same SSH process and should not automatically be counted as two separate login attempts.

### 3. Successful SSH Authentication

A successful authentication for `j.smith` was recorded from a different source IP, `203.0.113.45`. The SSH session was opened immediately afterward.

### 4. Privileged Activity

A sudo record shows a request to execute `/usr/bin/cat /etc/shadow`. The logs also record the opening and closing of a privileged session. They do not independently establish successful command completion or retrieval of file contents.

### 5. SSH Session Closure

The SSH session was recorded as closed, followed by a disconnection message. The records do not identify who initiated the disconnection.

## Duration and Activity Assessment

The interval between successful authentication (09:18:17) and the recorded disconnection (09:31:23) was approximately **13 minutes and 6 seconds**.

The logs record privileged activity during this interval. However, they do not establish continuous user activity or inactivity throughout the remaining time.

## Timeline Assessment

The timeline establishes the chronological sequence of authentication events, privileged activity records, and session closure.

The relationship between the failed authentication attempts from `198.51.100.24` and the successful login from `203.0.113.45` remains unconfirmed.

**Conclusion:** The observed sequence warrants further investigation, but the available synthetic records do not independently confirm unauthorized access or compromise.
