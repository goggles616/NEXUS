# 🧠 Project Nexus

> *Multi-agent autonomous planning. Built for durability, not demos.*

Nexus is a LangGraph-based multi-agent autonomous planning system designed for real-world reasoning workloads. It coordinates a team of specialized AI agents through structured, self-correcting pipelines — built around the principle that a system that catches its own mistakes is worth more than one that never admits to making them.

-----

## What Problem This Solves

Most AI implementations are single-model, single-prompt, single-shot. They work in controlled conditions and fail quietly in production. They hallucinate without correction. They have no memory of what they’ve done or why.

Nexus is built differently. It distributes reasoning across specialized agents, each with a defined role and scope. It routes work intelligently, corrects errors in-loop, and maintains persistent memory of decisions and context across sessions.

-----

## The Agent Team

|Agent         |Role                                                                             |
|--------------|---------------------------------------------------------------------------------|
|**Auditor**   |Validates inputs, outputs, and intermediate reasoning for quality and accuracy   |
|**Strategist**|High-level planning, goal decomposition, and task routing                        |
|**Critic**    |Challenges assumptions, identifies weaknesses, prevents overconfident conclusions|
|**Archivist** |Manages persistent memory, context retrieval, and long-term knowledge storage    |

Each agent has a defined responsibility. No single agent controls the full pipeline. The Critic exists specifically to challenge the Strategist. The Auditor exists to catch what both miss.

-----

## Architecture

```
User Input
    │
    ▼
Strategist ──────────────────────────────┐
    │                                     │
    ▼                                     ▼
Critic ◄──── feedback loop ────── Auditor
    │
    ▼
Archivist (persistent memory read/write)
    │
    ▼
Output + Decision Record
```

The system uses a QA routing layer built in LangGraph that governs agent transitions, prevents infinite loops, and ensures every output passes a validation checkpoint before delivery.

-----

## Core Stack

- **Orchestration:** Python · LangGraph
- **API Layer:** FastAPI
- **Primary AI:** Claude API (complex reasoning, agent logic)
- **Vector Memory:** Qdrant
- **Relational Storage:** PostgreSQL
- **Configuration:** Centralized `core/config.py` — single source of truth for all environment variables and LLM clients

-----

## Design Principles

**Near-zero hallucination tolerance** — The Auditor and Critic agents exist specifically to challenge and validate reasoning at every step. Trust is earned inside the pipeline, not assumed.

**Self-correcting loops** — Nexus doesn’t fail silently. When an agent produces output below threshold, the pipeline routes back for correction before proceeding.

**Long-term durability** — Decisions, reasoning chains, and context are persisted via the Archivist. The system learns from its own history across sessions.

**Privacy-aware by design** — Sensitive context stays within defined boundaries. The hybrid routing strategy keeps appropriate data local when needed.

**Separation of concerns** — Each agent does one thing well. The architecture resists the temptation to build one all-knowing agent and instead distributes responsibility intentionally.

-----

## Security & Stability

- JWT authentication on all FastAPI endpoints
- CORS protection configured
- No hardcoded credentials — all secrets via environment configuration
- Pydantic validation throughout the agent pipeline
- LangGraph QA router with loop prevention safeguards
- Async handling implemented correctly throughout

-----

## Status

🔧 **Active development** — Core agent team, LangGraph orchestration, and persistence layer operational. Ongoing work on agent communication protocols and Archivist retrieval optimization.

-----

## Roadmap

- [ ] Enhanced Critic feedback specificity
- [ ] Archivist semantic retrieval improvements
- [ ] Expanded agent roles for domain-specific workloads
- [ ] Monitoring and observability dashboard
- [ ] Configurable agent confidence thresholds

-----

## Philosophy

Most AI systems are built to impress in a pitch deck. Nexus is built to be useful in six months when no one is watching. That means catching errors, persisting memory, questioning its own conclusions, and running without hand-holding.

The measure of a good autonomous system isn’t what it does when everything goes right. It’s what it does when something goes wrong.

-----

*Built and maintained by [goggles616](https://github.com/goggles616)*
