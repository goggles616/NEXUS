# 🛰️ Home Network Intelligence System (HNIS)

> *Privacy-first. Local-first. Signal over noise.*

HNIS is a personal OSINT and safety monitoring platform that watches public surfaces, processes incoming signals, filters noise, and delivers actionable intelligence — all without sending sensitive data to the cloud.

Built by someone who depends on technology working reliably and privately, for people who feel the same way.

-----

## What Problem This Solves

Most monitoring and alerting tools require you to either trust a third-party cloud with your data, manually check sources yourself, or accept a flood of noise with no intelligent filtering.

HNIS solves all three. It runs locally, watches automatically, thinks before it alerts, and delivers only what actually matters — directly to your device.

-----

## What It Does

- **Monitors** public web surfaces, safety feeds, and configurable OSINT sources continuously
- **Processes** incoming signals through a local AI layer that understands context, not just keywords
- **Filters** aggressively — most noise never reaches you
- **Delivers** clean, actionable alerts locally to your device on your schedule
- **Visualizes** activity through a local dashboard designed with accessibility in mind

-----

## Architecture

HNIS is built around a deliberate hybrid AI routing strategy:

|Task                                                 |Model                |Reason                                              |
|-----------------------------------------------------|---------------------|----------------------------------------------------|
|Complex reasoning, summarization, contextual analysis|Claude API           |Accuracy and depth                                  |
|All sensitive/personal data processing               |Local Ollama instance|Privacy sovereignty — data never leaves your machine|

This means you get the capability of frontier AI where it counts, without sacrificing privacy where it matters.

-----

## Core Stack

- **Backend:** Python · FastAPI
- **AI Layer:** Claude API · Ollama (local)
- **Data:** PostgreSQL
- **Dashboard:** Local visual interface, screen reader accessible
- **Alerting:** Local delivery to iOS (iPhone)
- **Architecture:** Local-first · Privacy-first · No required cloud dependency

-----

## Design Principles

**Privacy sovereignty** — Sensitive data is processed exclusively on-device via local Ollama. Nothing personal touches an external API.

**Signal over noise** — The system is designed to be quiet. An alert means something. Noise is filtered before it reaches you.

**Accessibility by default** — The dashboard and alert delivery are built with screen reader compatibility from the ground up, not retrofitted.

**Self-contained operation** — Once deployed, HNIS runs without ongoing manual intervention. It watches so you don’t have to.

-----

## Security

- JWT authentication on all API endpoints
- CORS protection
- No hardcoded credentials — environment-based configuration via central `core/config.py`
- All sensitive processing air-gapped to local model layer
- XSS protections in dashboard layer

-----

## Status

🔧 **Active development** — Core pipeline, dashboard, and alert delivery operational. Ongoing refinement of signal filtering and source coverage.

-----

## Roadmap

- [ ] Expanded public source coverage
- [ ] Configurable alert thresholds per source type
- [ ] Enhanced dashboard accessibility features
- [ ] Self-healing pipeline recovery
- [ ] Packaged self-serve deployment option

-----

## Philosophy

Most people building monitoring tools are building them for organizations with security teams and budgets. HNIS is built for individuals — people who want to know what’s happening around them, protect what matters to them, and not hand that responsibility to a corporation.

Intelligence should be accessible to everyone, not just those who can afford an enterprise contract.

-----

*Built and maintained by [goggles616](https://github.com/goggles616)*
