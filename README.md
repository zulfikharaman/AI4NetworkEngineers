# AI for Network Engineers 🚀

This repository helps Network Engineers use AI and Generative AI
to automate, troubleshoot, and optimize networks safely and effectively.

## Who is this for?
- Network Engineers 
- Network Architects
- NOC / SOC Engineers
- Anyone curious about AI in Networking

## What you will learn
✅ AI fundamentals (without heavy math)  
✅ Generative AI for networking tasks  
✅ Prompt engineering for CLI, configs, and logs  
✅ Real-world use cases (ISP, DC, Enterprise)  
✅ Risks, hallucinations & how to verify AI output 

## Learning Roadmap
1. AI Basics for Network Engineers
2. Generative AI & LLMs
3. Prompt Engineering (Networking-focused)
4. Hands-on Use Cases
5. Responsible AI in Networking

## 🚦 How to Use This Repository (For Network Engineers)

If you are new to AI, follow this order:

1. **Start with the Roadmap**  
   Read `docs/roadmap.md` to understand what AI concepts matter
   for Network Engineers and what can be safely ignored.   
      📘 Start here → [Roadmap](docs/roadmap.md)   

2. **Study the Use Cases**  
   Open `docs/use-cases/` to see real examples of:
   - what problem occurred
   - what prompt was used
   - how the AI responded
   - how a Network Engineer verified the output safely  
      📘 Click here → [Use-Cases](use-cases/)   

3. **Go Through Prompts**  
   Visit the `prompts/` folder to see ready-to-use prompts
   for common networking tasks like troubleshooting and analysis.
   These are meant to be copy-paste starting points.   
      📘 Click here → [Prompts](prompts/)  

5. **Apply in Your Own Lab or Work**  
   Use the prompts with *your own* CLI outputs or logs,  
   ⚠️ always validating results before any production change.

## 🧩 Use Cases To Prompt Mapping

```The table below summarizes example use cases and the prompts used for easy reference```   

| Use Case | Scenario | Example Input | AI Prompt Used |
|--------|----------|---------------|----------------|
| [BGP Troubleshooting](use-cases/basic/bgp-troubleshooting.md) | eBGP session stuck in Active state | `show ip bgp summary` | [Analyze BGP state and suggest safe verification steps](prompts/basic/bgp-ts-prompt.md) |
| [Log Analysis using AI](use-cases/intermediate/log-analysis.md) | Intermittent packet loss with noisy syslogs | Sample syslog messages | [Analyze logs, identify patterns, and suggest safe verification steps](prompts/intermediate/log-analysis-prompt.md) |
| [Config Review with AI](use-cases/advanced/config-review-with-ai.md) | Pre-change review of routing and ACL configuration | Router configuration snippet | [Review configuration for risks and validation points - no changes](prompts/advanced/config-review-with-ai-prompt.md) |
``

## Disclaimer ⚠️
Never blindly apply AI-generated configs or commands in production.
Always validate in lab/test environments.
``

## 💬 Feedback & Improvements

This repository is evolving based on real Network Engineer feedback.

If you are a Network Engineer, your input matters:
- Was the learning flow clear?
- Did any section feel confusing or unnecessary?
- Did the use cases feel realistic?

Please open an Issue or start a discussion.
Even simple feedback is extremely valuable.  

**Current Version:** v1.0.0
