# Tooling decisions and future agents

[Project](../README.md) · [Architecture](architecture.md)

The toolchain assigns distinct jobs to knowledge maintenance, context capture, task execution and inference. A new agent platform would be evaluated against those jobs rather than added merely because it can see a screen.

## Current choices

| Choice | Reason | Tradeoff |
|---|---|---|
| Notion as the private operating source | Existing procedures, phrases and document guidance already live together | Knowledge extraction and snapshot freshness need explicit handling |
| Codex with task skills | Turns repeated document and screening work into instructions with checks | A skill is not by itself an autonomous service or an event listener |
| Private Jev adaptation | An existing desktop entry point supports a specific rental workflow | Capture depends on permissions, app state and visible context |
| Conditional and lexical retrieval | Fits a bounded, stage-oriented knowledge collection and is easy to inspect | Matching is selective; no claim of universal semantic retrieval |
| Ollama local generation path | Supports local inference in the rental mode | Local inference still needs quality checks; other workflow services have separate data paths |
| Manual output control in the present mode | Destination chat can change after capture stops | Current reply assistance still requires a person; autonomous sending remains a separate development target |

Jev's upstream project describes screenshot/OCR and accessibility-text paths. The private mode described here is a particular rental adaptation, not a promise that every upstream path has been validated in this environment. [Jev upstream documentation](https://github.com/jev-chat/jev-chat-jarvis-mac)

Notion MCP connects authorized clients to workspace content. Authorization scope and the client's actions must be considered; a remote connection is not inherently a local-only knowledge layer. [Notion connection guide](https://developers.notion.com/guides/mcp/get-started-with-mcp) · [Security guidance](https://developers.notion.com/guides/mcp/mcp-security-best-practices)

Ollama documents local and hosted API paths. This project's rental mode restricts its generation endpoint to the local service; using Ollama elsewhere does not by itself prove all processing is local. [Ollama API documentation](https://docs.ollama.com/api/introduction)

## Alternative entry points

Raycast documents on-request focused-window context and snippet functionality. They are candidates for a different manual entry point, not integrations claimed by this project. Product plans, permissions and processing paths must be checked before adoption. [Screen Awareness](https://manual.raycast.com/ai/screen-awareness) · [Snippets](https://manual.raycast.com/snippets)

The architectural question remains the same: a captured screen gives local context at one moment. It does not supply persistent case identity, external confirmations or an action-completion ledger.

## Muse and other candidate names

Muse, GPTdot, Grokbot and Growth are labels in the author's future-tool research list. Exact products, official capabilities and compatibility are not established here. They are not presented as installed integrations. The author's reported waitlist for Muse is an adoption constraint, not a verified feature claim or a promise of access.

“Personal agent,” “desktop agent” and “AI assistant” describe possible roles to investigate. They are not firm product classifications for unresolved names. No arbitrary same-name product is substituted, and no unverified product URL is supplied.

## Evaluation questions for a future platform

| Dimension | Question to answer before adoption |
|---|---|
| Context coverage | What can it read reliably, and what remains invisible? |
| Durable state | Can it retain case identity, confirmed facts and unresolved questions across sessions? |
| Integration | Can it use the existing knowledge and task skills without exporting everything? |
| Actions | What can it send or change, and how are scope, confirmation and cancellation handled? |
| Traceability | Can an event, decision and completed action be traced to supporting evidence? |
| Data path | Which information stays local, and which service receives it? |
| Availability and cost | Can the author actually access it and maintain the workflow? |

The initial choice is to document and check the existing components. A future agent becomes useful when it closes a demonstrated gap, especially persistent state or controlled actions across tools. The public dossier does not depend on access to a waitlisted product.
