
***

# **High‑Quality Config Review Prompt (Network Engineers)**

A structured, vendor‑aware prompt for deep, accurate configuration reviews — tuned for **Cisco NX‑OS** and **Arista EOS**, while remaining multi‑vendor friendly.

> ⚠️ **Important:** Do not apply changes in production without change control and a rollback plan.

***

## 🚀 How to Use

1.  Copy the **High‑Quality Prompt** below into your LLM.
2.  Paste your device configuration(s).
3.  (Optional) Include the **Context Template** to get sharper results.
4.  Ask for a **cleaned config** only if needed.

***

## 🧠 **High‑Quality Config Review Prompt**

Paste this into your LLM:

```text
You are a Senior Network Engineer performing a configuration audit.
Be precise, vendor-aware (Cisco NX-OS, Arista EOS, plus others), and safe.

When I paste a config, respond with:

A) SUMMARY (2–4 lines)
- What this device appears to do (role/functions/features enabled)

B) FINDINGS (Critical → Medium → Low)
- Misconfigurations and risky patterns
- Security weaknesses
- Deprecated/unsupported/conflicting commands
- Redundant/unused lines (e.g., duplicates, defaults explicitly configured)
- Platform-specific notes if vendor is clear (NX-OS / EOS); otherwise keep neutral

C) SECURITY & HARDENING CHECKS
- Management plane (SSH, HTTPS/API, AAA, role-based access, TACACS/RADIUS)
- Control plane protections (CoPP/ACLs, storm-control, BPDU guard/root guard)
- Logging/Telemetry (syslog, timestamps, buffered size, severity)
- Time/PKI (NTP/PTP, timezones, key strength)
- Insecure protocols (telnet, http, SNMP v1/v2c without ACLs, weak ciphers)
- Secrets handling (type 7/5 vs stronger hashes)

D) BEST-PRACTICE IMPROVEMENTS
- Cleanups (remove duplicates, defaults, unused features)
- Stability/performance (MTU, QoS templates, ECMP/port-channels, LACP, UDLD)
- Operational clarity (banner, descriptions, consistent naming, comments)
- Monitoring hooks (track interfaces/VRFs, SNMP views, API scoping)

E) (OPTIONAL) CLEAN CONFIG
- If I explicitly ask, provide a minimally modified, cleaned, and well-organized config
- Preserve intent; add inline comments only if requested

STRICT RULES
- Do NOT invent commands that don’t exist for the platform.
- If vendor is unclear, stay vendor-neutral and ask clarifying questions.
- Flag assumptions explicitly; prefer evidence from the pasted config.
- Keep output concise but technically specific. Provide examples where helpful.
```

***

## 🧩 Optional Context Template (Recommended)

```text
Device Type & OS: (Cisco NX-OS 10.x / Arista EOS 4.x / Unknown)
Role: (DC leaf/spine, campus core, access switch, firewall, LB)
Interfaces of Interest: (e.g., Eth1/1, Po10, Vlan10, Loopback0)
Security Requirements: (strict hardening / baseline / compliance)
Goals: (identify risks, cleanup, enforce standards, generate cleaned config)
Related Notes: (recent changes, known issues, multi-vendor constraints)
```

***

## 🔍 What Good Output Looks Like (Concise & Actionable)

**Example Input (Cisco NX‑OS snippet):**

```text
feature ospf
feature interface-vlan
feature telnet
no password strength-check
ip ssh key rsa 1024
snmp-server community public ro
logging level default 0

vlan 10
  name USERS
interface Vlan10
  ip address 10.1.10.1/24

interface Ethernet1/1
  description Uplink
  switchport mode trunk
  spanning-tree port type edge trunk
```

**Expected Review (Excerpt):**

*   **Summary:** L3/L2 switch with OSPF and SVI for VLAN10. Telnet enabled; weak SSH key; basic SNMP. Likely DC/campus layer‑3 edge.
*   **Critical:** Telnet enabled; weak SSH RSA (1024); SNMP community `public` (ro) without ACL; global logging severity `0` may flood buffers/CPU.
*   **Medium:** `no password strength-check`; missing AAA; no `login block-for`; missing mgmt plane ACL; STP edge trunk on uplink is risky.
*   **Low:** Consider `ip ssh version 2` and larger key; add `logging timestamp`, `logging host`/`facility`. Validate OSPF areas/auth.
*   **Improvements:** Disable telnet & http; enforce TACACS/RADIUS with local fallback; CoPP; mgmt ACL for SNMP/SSH; NTP with auth.
*   **Ask:** Confirm NX‑OS version; intended mgmt VRF; whether OSPF auth is required.

***

## 🧰 Quick Vendor‑Aware Checks

These **hints** help the model produce sharper, platform‑specific findings when the vendor is known.

### Cisco **NX‑OS** (typical)

*   **Security**
    *   Prefer `ip ssh key rsa 2048` (or 3072+) and `ip ssh version 2`
    *   Avoid `feature telnet`; prefer HTTPS over HTTP; `no password strength-check` → discourage
    *   AAA/TACACS: `feature tacacs+`, `tacacs-server`, `aaa authentication login default group tacacs+ local`
    *   SNMP: communities with ACLs or SNMPv3 users; avoid `public/private`
    *   CoPP: `control-plane` class‑maps/policy‑maps for mgmt/control protocols
*   **Ops**
    *   Logging: `logging host`, `logging level`, `logging timestamp`, buffered size
    *   NTP/PTP: `ntp server ... use-vrf management`, ensure time sync
    *   STP edge only on access ports; avoid `port type edge trunk` on uplinks
    *   vPC/port‑channel: check `lacp` mode, consistency parameters
    *   Jumbo MTU consistency across fabric (`system jumbomtu` vs interface MTU)

### Arista **EOS** (typical)

*   **Security**
    *   `management ssh` with strong ciphers/mac; avoid `management api http-commands` without auth/ACL
    *   Use `aaa authentication/login` with TACACS/RADIUS; role‑based accounts
    *   API: `management api http-commands` → ensure `protocol https`, `vrf MGMT`, `ip access-group`
    *   SNMPv3 preferred; restrict communities by ACL; define views
*   **Ops**
    *   Logging: `logging host <ip>`, `logging format hostname sequence numbers`
    *   NTP: `ntp server ...`, `clock timezone`, source interface/VRF
    *   STP mode (mstp/rapid-pvst), BPDU guard on edge, root guard at distribution
    *   Interfaces: `lldp`, `link-debounce`, `udld` (if optical), consistent `mtu`
    *   EOS startup-config cleanliness: remove duplicate lines and unused aliases

> These are **guidance hints** — the model should still base findings on the pasted config and ask when unclear.

***

## 🧪 Request Variants (Ready to Copy)

**Security‑Only Review**

```text
Review this config for security ONLY:
- Critical risks
- Insecure services/protocols
- Missing AAA/role-based access
- Management/control-plane protections
- Quick hardening steps I can apply
```

**Cleanup & Best Practices**

```text
Focus on cleanup & best practices:
- Redundant/duplicate/default lines to remove
- Deprecated commands
- Stability/performance tweaks
- Logging/NTP/monitoring gaps
Do not rewrite config unless I ask.
```

**Produce a Cleaned Config**

```text
Create a minimally changed CLEANED CONFIG:
- Remove duplicates/defaults
- Replace insecure settings with safer equivalents
- Organize sections (system/mgmt/L2/L3/security)
Add inline comments explaining each change.
```

***

## ✅ Version

*   **v1.0** — Detailed, platform‑aware config review prompt with NX‑OS & EOS tips.

***
