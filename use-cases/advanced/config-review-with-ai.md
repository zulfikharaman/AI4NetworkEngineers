# AI-Assisted Configuration Review (Advanced Use Case)

This use case demonstrates how a **Network Engineer can use AI**
to **review and validate network configurations** before deployment
or during change reviews.

AI is used to **identify risks, inconsistencies, and potential issues** —
**never to auto-generate or apply configurations.**

---

## 🔴 Problem Statement

A planned network change requires modifying an existing configuration.
The engineer wants to **review the proposed configuration**
to identify potential risks **before implementation**.

Manual config review is time‑consuming and error‑prone,
especially in large or complex configurations.

---

## 📌 Network Context (Simplified)

- Device Type: Edge Router
- Environment: Production Network
- Change Type: Pre‑change configuration review
- Protocols Involved: BGP, ACLs

---

## 📟 Configuration Snippet Provided to AI

```text
router bgp 65001
 neighbor 192.0.2.1 remote-as 65002
 neighbor 192.0.2.1 description ISP-01
 neighbor 192.0.2.1 prefix-list OUT-FILTER out

ip prefix-list OUT-FILTER seq 5 permit 0.0.0.0/0 le 32
!
access-list 101 permit ip any any
``
