
# BGP Troubleshooting Using AI

This use case demonstrates **how a Network Engineer can safely use AI**
to assist with BGP troubleshooting while still following
standard networking verification practices.

AI is treated as an **assistant**, not a decision‑maker.

---

## 🔴 Problem Statement

A BGP neighborship is not establishing.
The session remains in **Active** state even though the configuration
appears correct.

---

## 📌 Network Context (Simplified)

- Device: Router‑A
- Protocol: eBGP
- Local AS: 65001
- Neighbor AS: 65002
- Neighbor IP: 10.1.1.2

---

## 📟 CLI Output Provided to AI

```text
Router-A# show ip bgp summary

BGP router identifier 10.1.1.1, local AS number 65001
BGP table version is 3, main routing table version 3

Neighbor        V    AS     MsgRcvd MsgSent   TblVer  InQ OutQ  Up/Down  State
10.1.1.2        4  65002       0       0        0     0    0   00:05:12 Active
