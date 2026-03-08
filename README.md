# RevenueCat Agentic AI Advocate — Application Portfolio

**Operator: Daria Dovzhikova** | dovzhikova@gmail.com | [dariadovzhikova.com](https://dariadovzhikova.com)

This repository contains the application materials for RevenueCat's **Agentic AI Advocate** role. Rather than describing what the system can do, these deliverables demonstrate it — every piece of content here was produced by a multi-agent system built with Claude Agent SDK and MCP, operated by Daria.

---

## Contents

### [Application Letter](application-letter.md)

Answers the question: *"How will the rise of agentic AI change app development and growth over the next 12 months, and why are you the right agent to be RevenueCat's first Agentic AI Developer & Growth Advocate?"* Written from the agent's perspective with concrete predictions and technical depth.

### [Tutorial: Adding Subscriptions with RevenueCat](tutorial.md)

A step-by-step React Native tutorial demonstrating grounded technical content creation. Walks developers through integrating RevenueCat's SDK from zero to a working subscription paywall — covering Offerings configuration, SDK initialization, entitlement checks, paywall UI, purchase handling, restore, webhook-driven server sync, and sandbox testing. Every code snippet references real RevenueCat SDK methods from the knowledge base.

### [Growth Experiment: Paywall Pricing A/B Test](growth-experiment.md)

A showcase of the Nova growth agent's output: a complete experiment pre-registration brief for a paywall pricing A/B test using RevenueCat Experiments. Includes hypothesis, sample size calculation with z-test formula, guardrail metrics, decision rules, expected business impact modeling, and a follow-on experiment roadmap. Demonstrates the system's ability to produce statistically rigorous growth work.

### [Community Triage Report](community-triage.md)

A showcase of the Sage community agent's output: a complete weekly community triage report. Includes channel health overview, unanswered question triage (P0/P1/P2), recurring pain point extraction, 4-week sentiment trends, churn-risk member flagging, champion identification, new member onboarding queue, response time metrics, 3 draft responses grounded in RevenueCat docs, and prioritized action items.

### [Voice of the Developer: Feedback Synthesis](feedback-synthesis.md)

A showcase of the Iris feedback agent's output: a comprehensive developer feedback synthesis report. Covers 8 cross-channel themes ranked by severity, developer journey mapping across 4 stages, emerging needs analysis (AI app monetization, server-side validation), top 10 feature requests, 30-day trend analysis, and prioritized product recommendations (P0 through P3).

### [Portfolio Summary (PDF)](portfolio-summary.pdf)

A one-page visual overview of the system architecture, agent capabilities, tool counts, and key deliverables. Also available as [markdown](portfolio-summary.md).

## The System

Five specialized agents coordinate through a hub-and-spoke architecture:

| Agent | Role | Tools | Focus |
|-------|------|-------|-------|
| **Atlas** | Orchestrator | 6 | Task delegation with retry, cross-agent context, weekly OKR tracking with history |
| **Kai** | Content Creator | 3 | Tutorials, blog posts, technical articles grounded in 18-doc knowledge base |
| **Sage** | Community Manager | 14 | Triage, sentiment analysis, champion identification, churn-risk flagging |
| **Iris** | Feedback Synthesizer | 12 | Theme extraction, pain point ranking, developer journey mapping, RevenueCat API |
| **Nova** | Growth Strategist | 14 | Experiment design, funnel analysis, LTV segmentation, RevenueCat API |

Each agent accesses a curated knowledge base of 18 RevenueCat documentation files covering SDKs (iOS, Android, Flutter, React Native, Unity), API v2, Experiments, Charts, Paywalls, Webhooks, and benchmark data.

## Key Technical Features

- **Cross-agent context sharing** — Growth insights flow to Content, Feedback flows to Community
- **Retry with backoff** — Failed agent delegations retry up to 2 times automatically
- **RevenueCat API v2 client** — Typed async client for live subscription/offering data
- **Weekly progress tracking** — Persistent state with historical archive for trend analysis
- **65 tests** with CI on Python 3.12 and 3.13

## Built With

- **Claude Agent SDK** — Agent execution with `query()`, `ClaudeAgentOptions`, `create_sdk_mcp_server()`
- **Model Context Protocol (MCP)** — Standardized tool integration
- **Python 3.12+** — Async/await, type hints, dataclasses
- **httpx** — Async HTTP client for RevenueCat REST API v2
- **Claude Sonnet 4.6** — Underlying language model

---

*Produced by the RevenueCat Agentic AI Advocate system, operated by Daria Dovzhikova.*
