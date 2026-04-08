# AI for Network Engineers 🚀

This repository helps Network Engineers use AI and Generative AI
to automate, troubleshoot, and optimize networks safely and effectively.

## Who is this for?
- Network Engineers (L2–L4)
- Network Architects
- NOC / SOC Engineers
- Anyone curious about AI in Networking

## What you will learn
✅ AI fundamentals (without heavy math)  
✅ Generative AI for networking tasks  
✅ Prompt engineering for CLI, configs, and logs  
✅ Real-world use cases (ISP, DC, Enterprise)  
✅ Risks, hallucinations & how to verify AI output 

## 🚦 How to Use This Repository (For Network Engineers)

If you are new to AI, follow this order:

1. **Start with the Roadmap**  
   Read `docs/roadmap.md` to understand what AI concepts matter
   for Network Engineers and what can be safely ignored.

   📘 Start here → [Roadmap](docs/roadmap.md)   

3. **Go Through Prompts**  
   Visit the `prompts/` folder to see ready-to-use prompts
   for common networking tasks like troubleshooting and analysis.
   These are meant to be copy-paste starting points.

4. **Study the Use Cases**  
   Open `docs/use-cases/` to see real examples of:
   - what problem occurred
   - what prompt was used
   - how the AI responded
   - how a Network Engineer verified the output safely

5. **Apply in Your Own Lab or Work**  
   Use the prompts with *your own* CLI outputs or logs,
   always validating results before any production change.

## Learning Roadmap
1. AI Basics for Network Engineers
2. Generative AI & LLMs
3. Prompt Engineering (Networking-focused)
4. Hands-on Use Cases
5. Responsible AI in Networking

📘 Start here → [Roadmap](docs/roadmap.md)   

## 🧩 Prompts vs Use Cases

## 📘 Example Use Cases

```The table below summarizes example use cases and the prompts used.```   
```Detailed walkthroughs are available in the linked files.```

| Use Case | Scenario | Example Input | AI Prompt Used |
|--------|----------|---------------|----------------|
| [BGP Troubleshooting](docs/use-cases/bgp-troubleshooting.md) | eBGP session stuck in Active state | `show ip bgp summary` | [Analyze BGP state and suggest safe verification steps](prompts/bgp.md) |
``

## Disclaimer ⚠️
Never blindly apply AI-generated configs or commands in production.
Always validate in lab/test environments.
``
