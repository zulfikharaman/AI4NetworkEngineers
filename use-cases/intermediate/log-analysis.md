# AI-Assisted Log Analysis for Network Incidents

This use case demonstrates how a **Network Engineer can use AI**
to analyze large volumes of network logs and gain quick situational
awareness during an incident.

AI is used to **summarize, correlate, and highlight patterns** —
not to make configuration changes or final decisions.

---

## 🔴 Problem Statement

A monitoring system reports **intermittent packet loss**
affecting multiple users.

The network devices are generating a **large volume of syslog messages**,
making it difficult to quickly identify what is relevant.

---

## 📌 Network Context (Simplified)

- Device Type: Layer‑3 Switch
- Environment: Enterprise Network
- Log Source: Syslog
- Issue Window: Last 30 minutes

---

## 📟 Sample Log Output Provided to AI

```text
Mar 10 10:21:12 SW1 %LINK-3-UPDOWN: Interface Gi0/1, changed state to down
Mar 10 10:21:14 SW1 %LINK-3-UPDOWN: Interface Gi0/1, changed state to up
Mar 10 10:22:05 SW1 %LINEPROTO-5-UPDOWN: Line protocol on Interface Gi0/1, changed state to down
Mar 10 10:22:07 SW1 %LINEPROTO-5-UPDOWN: Line protocol on Interface Gi0/1, changed state to up
Mar 10 10:23:45 SW1 %PM-4-ERR_DISABLE: loopback error detected on Gi0/1
Mar 10 10:24:10 SW1 %LINK-3-UPDOWN: Interface Gi0/1, changed state to down
Mar 10 10:24:12 SW1 %LINK-3-UPDOWN: Interface Gi0/1, changed state to up
