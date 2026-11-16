# Event Correlation Matrix

**Case ID:** NS-2026-001  
**Organization:** Northstar Solutions  
**Target Host:** ns-ubuntu-srv01  
**Evidence Source:** E-001 — Synthetic Linux Authentication Log

## Correlation C-001 — Failed Authentication Attempts

| Field | Description |
|---|---|
| Related Events | Log lines 1–5 |
| Account(s) | j.smith, admin2 |
| Source IP | 198.51.100.24 |
| Time Range | 09:10:12–09:13:45 |
| Supporting Evidence | Repeated authentication failures; same source IP; same PID (1901) for the two admin2 messages |
| Classification | Confirmed event grouping |
| Limitations | The records do not identify the human operator or establish intent |

## Correlation C-002 — Successful SSH Session

| Field | Description |
|---|---|
| Related Events | Log lines 6–7, 11–12 |
| Account | j.smith |
| Source IP | 203.0.113.45 |
| Time Range | 09:18:17–09:31:23 |
| Supporting Evidence | Successful authentication, session opening and closing; same SSH PID (2012) |
| Classification | Confirmed event grouping |
| Limitations | The account identity does not establish the human operator's identity or authorization |

## Correlation C-003 — Privileged Activity

| Field | Description |
|---|---|
| Related Events | Log lines 8–10 |
| Account | j.smith |
| Privileged User | root |
| Time Range | 09:23:04–09:23:05 |
| Supporting Evidence | Sudo command record and privileged session opening and closing |
| Classification | Plausibly associated with C-002 |
| Limitations | No direct PID linkage to the SSH session; command completion and file access are not independently verified |

## Correlation C-004 — Relationship Between Failed and Successful Authentication

| Field | Description |
|---|---|
| Related Events | Log lines 1–7 |
| Account | j.smith |
| Source IPs | 198.51.100.24 and 203.0.113.45 |
| Time Range | 09:10:12–09:18:18 |
| Supporting Evidence | Failed authentication attempts followed by successful authentication for the same account |
| Classification | Plausible relationship, not confirmed |
| Limitations | Different source IPs; no evidence establishes a common operator, causal relationship, or credential compromise |

## Overall Assessment

The available records establish two distinct groups of authentication activity and a subsequent privileged activity record associated with the same account.

The relationship between the failed authentication attempts and the successful SSH session remains unconfirmed. The available evidence does not establish unauthorized access, the identity of the human operator, or successful extraction of sensitive information.
