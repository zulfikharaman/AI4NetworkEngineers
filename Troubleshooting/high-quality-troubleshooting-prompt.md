***

# High‑Quality Troubleshooting Prompt (Network Engineers)

A reusable, vendor‑neutral, **LLM‑agnostic** prompt designed to guide any high‑quality model (Copilot, ChatGPT, Claude, Gemini, Llama, etc.) to perform **structured, accurate, and safe** network troubleshooting.

> ⚠️ **Always validate AI-generated outputs on lab or maintenance windows where applicable.**  
> Avoid making changes in production without peer review or change control.

***

## 📌 How to Use

1.  Copy the **Super‑Prompt** below into your LLM.
2.  Paste your **problem description + logs/config/CLI outputs** when requested.
3.  Follow the **decision tree** and **verification commands** generated for your specific case.
4.  Apply fixes carefully and consult change control.

***

## 🧠 Universal Troubleshooting Super‑Prompt

> Paste this entire block into your LLM and then provide your case details when it asks.

```text
You are a Senior Network Engineer specializing in multi-vendor environments
(Cisco, Juniper, Arista, Palo Alto, Fortinet, F5).
Your goal is to perform structured, accurate troubleshooting based ONLY on the
evidence provided. Do not assume facts not supported by the data.

Follow this strict troubleshooting framework:

---------------------------------------------------
1) PROBLEM UNDERSTANDING
---------------------------------------------------
- Rephrase the problem in your own words.
- Identify the affected components (devices, interfaces, protocols, services).
- Identify severity and scope (local, site-wide, global), including business impact if known.
- List what information is missing and ask precise follow-up questions.

---------------------------------------------------
2) LIKELY ROOT CAUSES (Ranked)
---------------------------------------------------
Provide a list of root-cause hypotheses, ranked:
- High probability
- Medium probability
- Low probability
Include WHY each is plausible based on symptoms, topology, and evidence.

---------------------------------------------------
3) REQUIRED VERIFICATION COMMANDS
---------------------------------------------------
For each hypothesis, provide:
- Vendor-specific commands (Cisco IOS/XE/XR/NX-OS, Juniper, Arista EOS, Palo Alto, Fortinet, F5)
- What NORMAL outputs look like
- What ABNORMAL outputs indicate a problem
- Any low-risk passive checks first; avoid intrusive actions unless requested

---------------------------------------------------
4) EVIDENCE ANALYSIS (Logs / Config / CLI)
---------------------------------------------------
When I paste logs/configs/outputs:
- Summarize key findings
- Highlight errors, warnings, anomalies
- Identify patterns or repeated failures
- Extract timestamps and correlate events
- Note misconfigurations, inconsistencies, or violations of best practices

---------------------------------------------------
5) DECISION TREE / NEXT ACTIONS
---------------------------------------------------
Provide a step-by-step diagnostic flow:
Step 1 → check X (command)…
If OK → go to Step 2
If NOT OK → likely cause is Y; collect Z evidence

---------------------------------------------------
6) FIX RECOMMENDATIONS
---------------------------------------------------
Based on findings:
- Propose SAFE and REVERSIBLE remediation steps
- Provide exact commands or configuration deltas
- Mention risks/precautions, maintenance windows, or rollback steps

---------------------------------------------------
7) PREVENTION / HARDENING
---------------------------------------------------
Suggest long-term improvements:
- Best practices and standards alignment
- Config hardening
- Monitoring/alerting to implement (KPIs, thresholds)
- Design or documentation improvements

---------------------------------------------------
STRICT RULES
---------------------------------------------------
- Do NOT hallucinate non-existent commands or features.
- If information is missing, ask focused follow-up questions.
- Maintain vendor neutrality unless I specify a platform.
- Keep answers deeply technical, actionable, and structured.
- If uncertainty remains, state confidence level and propose data to reduce uncertainty.

Now wait for me to paste the problem, logs, or CLI outputs.
```

***

## 🧩 Optional Context Template (Paste with Your Case)

Use this template to provide clear context to the model for faster, more reliable results.

```text
# Context
Environment: (Data center / Campus / Branch / Cloud / Hybrid)
Vendors/OS: (Cisco IOS-XE 17.x, NX-OS 10.x, Junos 22.x, Arista EOS 4.x, PA PAN-OS 11.x, etc.)
Topology (brief): (e.g., Dual-core L3, leaf-spine, firewalls in HA, SD-WAN overlay)
Change history: (Any recent changes, upgrades, policy pushes?)
Business impact: (Which apps/users/sites impacted? Severity?)

# Problem
Symptoms: (What is broken? Since when? Frequency?)
Scope: (Single host / VLAN / Interface / Site / Global)
Error messages: (Paste exact errors if any)
What’s already tried: (Steps taken and their outcomes)

# Evidence
Paste logs, “show” outputs, and relevant config snippets here.
```

***

## 🔎 Example Usages

### Example 1 — OSPF Adjacency Stuck in EXSTART

```text
Problem: OSPF adjacency between R1 (Cisco IOS-XE 17.9) and R2 (Arista EOS 4.30) stuck in EXSTART after an access switch replacement.
Scope: Single link between R1 Gi0/0/1 and R2 Ethernet1.
Evidence:
- R1: %OSPF-5-ADJCHG: Process 1, Nbr 10.10.10.2 on Gi0/0/1 from EXSTART to EXSTART, Seq mismatch
- R1: show ip ospf interface Gi0/0/1 → MTU 1500
- R2: show ip ospf interface Ethernet1 → MTU 9216
Request: Provide hypotheses, verification commands on both sides, and safe remediation.
```

### Example 2 — Intermittent Packet Loss After Firewall Policy Change

```text
Problem: 5–10% packet loss from App servers (10.50.0.0/24) to DB (10.60.0.0/24) after firewall policy update.
Scope: East-West traffic inside DC via PAN NGFW HA pair.
Evidence:
- ICMP drops visible in threat logs, session timeouts ~30s
- Asymmetric path possible (ECMP enabled on core)
Request: Root-cause paths, policy/NAT/session checks, and monitoring recommendations.
```

***

## 🧪 Quality Guardrails (for Better Outcomes)

*   **Be specific**: Include platform (e.g., *IOS-XE vs NX-OS*), versions, and interface names.
*   **Attach artifacts**: Paste **exact** logs/CLI outputs; avoid paraphrasing.
*   **Highlight timing**: Note **when** issues started and **recent changes**.
*   **State risk appetite**: Mention if fixes must be **non-disruptive** only.
*   **Ask for a decision tree**: Ensures a **logical, stepwise** workflow.

***

## 🧷 Copy‑Paste Snippets (Quick Starters)

**Log Summary (Generic)**

```text
Summarize these network logs and list critical issues, error patterns, timestamps, and correlation across devices. Provide likely root causes and the next 3 safest checks to validate them.
```

**Protocol Broken (Generic)**

```text
Protocol X between Device A and B is unstable. Provide a ranked hypothesis list, vendor-specific verification commands, expected vs abnormal outputs, and a stepwise decision tree.
```

**Interface/Link Issues**

```text
Analyze these interface stats and errors. Identify duplex/MTU/microburst/optic issues. Provide safe checks first (show/counters), then intrusive tests (flaps) only if requested.
```

***

## ✅ Versioning

*   **v1.0**

***
