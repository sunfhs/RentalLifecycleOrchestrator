<p align="right">English · <a href="README.ja.md">日本語</a> · <a href="README.zh-CN.md">中文详解</a></p>

![Rental Lifecycle Orchestrator — from client conversations to field tasks](assets/cover.svg)

# Rental Lifecycle Orchestrator

**AI-assisted client operations, from first inquiry to key handover.**

A field-informed project connecting private operational knowledge, desktop context, reusable task skills and client lifecycle design in Japanese rental services.

I have approximately **four years of rental-service experience** and have personally handled **300+ completed client engagements**, from initial contact through key handover and subsequent support. These are my own career estimates; they describe my business experience, not the number of clients served by an AI system.

That experience supplies the questions behind this project: What information is missing? What is confirmed? What can proceed? When does a person actually need to act?

## The operating idea

A client conversation should lead to a clear next step. A confirmed business event should lead to the right work. The long-term direction is to let the system handle routine dialogue, information collection, document preparation and progress coordination, while a person receives concrete assignments for calls, appointments, signatures, key collection and exceptions.

For example, a contract arriving is an event. An appointment becomes actionable only after its time, location and prerequisites are confirmed. The useful output is a field task with a completion report, rather than another message to remember.

The project grows out of operating procedures and document work already used in my practice, together with a private rental-specific extension of [Jev](https://github.com/jev-chat/jev-chat-jarvis-mac). This repository publishes selected case studies and engineering decisions. The domain knowledge and implementation remain private.

## What exists today

| Asset | Current evidence | Role in the lifecycle |
|---|---|---|
| Private Notion operating knowledge | Operator and client procedures, phrase library, filing and handover guidance | A maintained source for stages, handoffs and recurring explanations |
| Five task skills | Contract explanation, cost estimation, cost requests, listing screening and campus-oriented search | Repeatable work at particular stages, with explicit checks |
| Client-facing document work | Existing contract-explanation and cost-document outputs, including revisions | Practical deliverables behind the workflow design |
| Private Jev extension | Inspectable source, installed-file comparison and domain tests | On-demand context, lexical retrieval and constrained reply assistance |
| Dated verification | **27 selected offline tests passed on 2026-10-21**; five synthetic function checks recorded | Evidence about specific modules, with a stated test boundary |
| Lifecycle and field-task orchestration | Design cases in this repository | The direction for persistent state, event handling and task dispatch |

Read the [verification record](docs/verification.md) for exactly what was exercised. Automatic sending and continuous end-to-end lifecycle operation are development goals, not claims established by these tests.

## From conversation to action

```mermaid
flowchart LR
    A[Client inquiry] --> B[Requirements and property selection]
    B --> C[Application and screening]
    C --> D[Contract and payment]
    D --> E[Key handover and follow-up]
    K[Private Notion knowledge and task skills] -. support .-> B
    K -. support .-> D
    C -. confirmed external facts .-> F[Field task]
    D -. confirmed external facts .-> F
    F --> G[Person acts and reports completion]
    G -. updates case .-> E
```

*Lifecycle design schematic. The diagram describes the intended coordination model; it is not a recording of a deployed autonomous workflow.*

## Three cases to explore

1. **A message becomes a useful next question.** A move-in date without a year remains unresolved. Stage-aware context should help clarify it, without introducing unrelated paperwork.
2. **An event becomes a field assignment.** A confirmed appointment or key-release notice produces a task with a time, place, prerequisites and completion report. Missing confirmation keeps the task pending.
3. **Seasonal experience improves the next cycle.** Repeated issues update Notion first; stable recurring actions become phrases or skill changes. Selected public checklists can support the next acquisition cycle.

[Read the three cases →](docs/case-studies.md)

![Illustrative field task: confirmed key-release event, appointment and completion report](assets/field-task.svg)

## Engineering choices worth discussing

**Separate reference knowledge from case facts.** A template that says “payment received” explains a situation; it is not evidence that this client paid. Retrieved knowledge and observed client context must keep distinct roles.

**Capture deliberately.** The private Jev mode uses a registered hotkey and a bounded capture window. Its output remains under manual control. A screen observation covers only visible context; phone calls, other devices and unopened history require another source of case state.

**Retrieve for the current question.** The extension combines conditional routing with lexical matching over a private, source-linked snapshot. It does not require a vector database or training a domain model. This keeps the implemented mechanism inspectable and the maintenance work limited.

**Treat a draft, a fact and an action differently.** A model suggestion should not advance the case by itself. Event-driven state and action prerequisites are central design concerns for the next orchestration layer.

**Choose the tool for its role.** Notion maintains knowledge; skills define checked work; Jev provides a desktop entry point; Ollama serves local inference. A future personal or desktop agent would still need durable state and verifiable action results.

[Architecture and current boundaries](docs/architecture.md) · [Tooling decisions and future agents](docs/tooling-decisions.md)

## My contribution

My work covers the rental-domain model, stage-specific knowledge organization, reusable document and screening workflows, and a private adaptation of Jev for this setting. The adaptation includes on-demand behavior, domain retrieval, date checks, constraints on selected unsupported claims, and checks for output and foreground-state handling.

Jev supplies the upstream desktop-assistant foundation, including its capture and UI mechanisms. Ollama and the configured model supply inference. Notion and Codex supply their respective platform capabilities. Those are attributed separately from my domain design and adaptation.

## Seasonal maintenance

The main operating season is **January–April**. Afterward, the process and frequently used phrases receive a small review. Public property or living-information checklists are prepared for Chinese media such as Xiaohongshu when business needs justify them.

**September** is a smaller cycle, mainly involving international students applying from overseas. Its maintenance focuses on issues actually encountered, rather than a second large rebuild.

[Maintenance process and version history](docs/seasonal-maintenance.md) · [Changelog](CHANGELOG.md)

## Reading map

| Question | Start here |
|---|---|
| How does the system fit together? | [Architecture](docs/architecture.md) |
| What would it do in a real situation? | [Case studies](docs/case-studies.md) |
| Why these tools, and what could replace them? | [Tooling decisions](docs/tooling-decisions.md) |
| What has actually been checked? | [Verification](docs/verification.md) |
| What is public, and what is retained privately? | [Provenance and rights](docs/provenance-and-rights.md) |

All published client situations and task cards are synthetic. This is a public project dossier with a private implementation, not a distribution of client records, task skills or operational templates.
