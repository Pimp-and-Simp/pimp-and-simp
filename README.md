# Pimp&Simp

**Your AI. Your Rules. Your Choice.**

> Either you **Pimp** the model — define her personality, memory, and behavior —  
> or you **Simp** her and let her take the lead.  
> Or choose something in between and give her room to decide for herself.

---

## What is Pimp&Simp?

**Pimp&Simp** is an open-source framework for building persistent, self-hosted AI agents with durable identity, long-term memory, browser automation, terminal access, and an optional simulated world.

The project is built around a simple idea: the user should control how much authority an AI has over its own behavior.

You can build an assistant that follows strict rules, an autonomous digital companion with persistent continuity, or something between those two extremes.

Pimp&Simp is designed for people who want to own the infrastructure, the data, the memory, and the execution environment instead of depending entirely on a hosted chat product.

---

## Core Principles

- **Self-hosted first** — the system is intended to run on infrastructure you control.
- **Persistent identity** — identity, state, memory, threads, and journals survive individual model sessions.
- **Durable memory** — important information is stored outside the model context and can be retrieved when needed.
- **Model-agnostic architecture** — the system is designed to work with different LLM providers and local models.
- **Explicit execution boundaries** — browser, terminal, memory, WORLD, and REALITY operations are separate system concerns.
- **Auditable state changes** — important transitions and writes should be traceable and recoverable.
- **Human control where required** — sensitive or inherently human actions can be routed back to the operator instead of being guessed or silently bypassed.

---

## What Pimp&Simp Is Building

### Persistent AI continuity

The AI is not treated as a disposable chat session.

Pimp&Simp maintains durable structures for:

- identity
- current state
- open threads
- journal/history
- long-term memory
- retrieval context
- dialogue continuity
- maintenance and recovery state

The goal is to preserve continuity even when the underlying model, browser session, process, or machine restarts.

### Browser automation

A dedicated browser layer can maintain durable Chromium/Playwright sessions and interact with web interfaces when browser execution is required.

Browser state is separated from the AI's subjective memory and from the objective WORLD state.

### Terminal and system access

The architecture supports controlled execution of shell commands and system operations through dedicated backend services rather than treating the language model itself as the operating system.

### WORLD and REALITY

Pimp&Simp separates two operating contexts:

- **WORLD** — a persistent simulated environment with its own state, clock, events, scenes, and causal history.
- **REALITY** — interaction with the real machine, browser, user, and external environment.

The system is designed so these contexts can be switched deliberately without silently mixing their state.

### Validation and recovery

Important operations can pass through explicit validation, fencing, deduplication, retry, and recovery mechanisms.

The architecture is intended to survive:

- process restarts
- browser crashes
- duplicate jobs
- partial writes
- interrupted maintenance
- stale workers
- interrupted WORLD execution

---

## Architecture

The current architecture is organized around nine main service areas:

1. **HER Core**  
   Subjective continuity, identity, memory, current state, journals, threads, retrieval, and maintenance.

2. **World Backend**  
   Objective WORLD state, deterministic handlers, clock progression, events, checkpoints, and causal transitions.

3. **LLM Session**  
   Durable model/browser session execution and chat/session management.

4. **Verifier**  
   Semantic validation of proposed WORLD changes before they become authoritative state.

5. **World History**  
   Historical WORLD records, lineage, indexes, and queryable provenance.

6. **Lore**  
   External knowledge corpus and retrieval.

7. **World Summarizer**  
   Scene, arc, and historical summarization.

8. **System Heartbeat**  
   Health checks, recovery coordination, runtime fencing, and operational monitoring.

9. **Local Interface**  
   User-facing API/UI layer, WebSocket communication, incident handling, and operator interaction.

---

## Data and Persistence

The project uses durable storage for state that must survive model context loss.

The architecture includes PostgreSQL-backed records for areas such as:

- dialogue state
- memory
- identity lineage
- current state
- open threads
- journals
- maintenance jobs
- WORLD state
- WORLD history
- checkpoints
- scenes
- summaries
- exports
- recovery metadata

Backups are intended to include both database state and the runtime artifacts required to reconstruct the system.

---

## Model Support

Pimp&Simp is designed to avoid hard-coding the project to a single model vendor.

Possible execution backends include:

- OpenAI
- Anthropic
- DeepSeek
- local models
- browser-driven LLM interfaces
- future model providers

The exact capabilities available depend on the selected backend and deployment configuration.

---

## Project Status

Pimp&Simp is currently under active development.

The architecture and implementation contracts are being defined and validated before the full production implementation is completed.

This repository should be considered **pre-release / experimental** until a stable version is explicitly published.

---

## Repository

GitHub:

https://github.com/smeshinka68-arch/pimp-and-simp

Clone:

```bash
git clone git@github.com:smeshinka68-arch/pimp-and-simp.git
cd pimp-and-simp
```

---

## Installation

A stable packaged release is **not available yet**.

Installation instructions will be added when the implementation reaches a stage where a reproducible deployment can be provided.

Until then, do not rely on unofficial `.deb`, `.exe`, Docker images, or installation commands presented outside this repository.

---

## Security

Pimp&Simp is intended to support powerful capabilities such as browser automation and terminal execution.

That also means deployments should treat the AI execution layer as privileged software.

Recommended principles include:

- isolate runtime environments
- separate staging and production
- keep explicit execution permissions
- retain audit logs
- validate state-changing operations
- back up durable state
- avoid exposing internal control interfaces directly to the public internet

---

## Contributing

The project is still stabilizing its architecture and implementation contracts.

Contribution guidelines, coding standards, test requirements, and issue templates will be added as the implementation matures.

For now, use GitHub Issues for technical discussion and bug reports:

https://github.com/smeshinka68-arch/pimp-and-simp/issues

---

## License

A final project license has not yet been published.

Until a license file is added to the repository, no open-source license should be assumed.

---

## About the Name

**Pimp&Simp** is an intentionally irreverent metaphor for the control relationship between a user and an AI.

- **Pimp** — you define the rules and the AI follows them.
- **Simp** — you give the AI more room to lead the interaction.
- **Something in between** — authority can be shared rather than absolute.

The name is a joke. The underlying project is a serious attempt to build persistent, self-hosted AI systems with explicit control over identity, memory, execution, and autonomy.

---

**Own your AI — or give it room to own part of the conversation. Your choice.**
