# Personal AI Architecture
**Specification v0.9 (Draft) · 2026**
**Maintainer:** Timothy Shin · [thedimode.com](https://thedimode.com)

---

> Personal AI Architecture is the discipline of building, owning, and operating your own AI as portable, file-based infrastructure calibrated to a specific person's working life.
>
> The practice is *Personal AI Operations*. The practitioner is an *AI Operator*. The artifact is *The Operator Stack*.

This repository is the formal specification. For the reference implementation, see [`thedimode/operator-stack`](https://github.com/thedimode/operator-stack). For the maintainer's own working stack as a proof artifact, see [`thedimode/thedimode`](https://github.com/thedimode/thedimode). For the workbook that teaches the discipline, see [thedimode.com/workbook](https://thedimode.com/workbook).

## Citation

> Shin, Timothy. *Personal AI Architecture: A Specification.* v0.9 (Draft), 2026. https://github.com/thedimode/personal-ai-architecture

---

## The Three Flags

Personal AI Architecture rests on three claims. Each addresses a specific, evidenced failure mode of platform-locked AI.

### Flag 1 · Your AI should remember who you are — and that memory should survive the vendor's next update.

Platform-managed memory (ChatGPT Memory, Claude Projects, Gemini Saved Info) has demonstrably failed this test. The Feb 5, 2025 OpenAI backend update silently wiped thousands of users' saved memories. Context resets between sessions remain a daily reality for paying users. The discipline requires that identity persistence be a property of the user's files, not the vendor's database.

### Flag 2 · You should own your AI's memory in files you can read, edit, and carry between models.

Vendor-managed memory creates three failure modes simultaneously: lock-in (memory does not export), silent corruption (compaction destroys project instructions without notice), and siloed visibility (Projects do not share with standalone chats). The discipline replaces all three by treating memory as plain text on the user's disk, structured by an open schema, version-controlled with git, and portable between models.

### Flag 3 · Your AI workflow should keep working when the vendor goes down, raises prices, or changes the model under you.

In 2025 alone: 294 documented OpenAI outages, a Nov 18 Cloudflare incident took ChatGPT and Claude offline for ~5.5 hours, a Dec 2 OpenAI outage hit 300M weekly users, simultaneous global outages of all four major providers in April. Subscription-tier creep (Anthropic testing removal of Claude Code from Pro; OpenAI's $100 tier). Model behavior shifts (GPT-4 → 4o → o1, Claude 3.5 → 3.7 → 4) that broke carefully tuned workflows. The discipline requires the operator's workflow to be vendor-resilient: portable identity, portable memory, portable skill definitions, and (optionally) local-model fallback for graceful degradation.

---

## What This Spec Defines

This specification standardizes the file formats, schemas, and protocols that make a Personal AI Architecture portable. It is intentionally **format-only**, not vendor-coupled. Any LLM platform (Claude, ChatGPT, Gemini, Llama, Mistral, Qwen, future models) that can read markdown can operate against a compliant stack.

| Section | What it standardizes | Status |
|---|---|---|
| `01-identity-files` | `profile.md`, `persona_profile.md` — schema, sections, required fields | Draft |
| `02-state-files` | `decisions.md`, `current_state.md`, `session_log.md` — schema, append rules, retention | Draft |
| `03-skill-schema` | Description-triggered auto-loading skill manifest format | Draft |
| `04-hook-lifecycle` | Standardized hook events (session start, user prompt submit, tool call, session stop) | Draft |
| `05-autonomy-ladder` | Five-stage operator-defined autonomy levels, promotion / demotion rules | Draft |
| `06-recall-protocol` | Standardized retrieval invocation: front-door, vault-only, conversation-only | Draft |
| `07-fact-capture` | Append-only fact buffer + nightly consolidation pattern | Draft |

Each section ships as a separate markdown file. Each file has a versioned schema, a worked example, and a compliance test list.

## What This Spec Does Not Define

- **Which LLM provider you use.** Anthropic, OpenAI, Google, Meta, Mistral, Qwen, Alibaba, DeepSeek, local 4-7B open-weight — all are valid runtimes.
- **Which editor / interface you use.** Claude Code, ChatGPT Desktop, Cursor, Continue, plain terminal — all are valid clients.
- **Which scheduler or orchestrator you use.** launchd, cron, systemd, manual — all are valid.
- **Whether you run locally, on a server, or in a container.** Compliance is about file format, not infrastructure.

This is a portable-format standard, like RSS or Markdown itself. Vendors can read it; the user owns it.

---

## Acknowledgments & Prior Art

This specification builds on, and is in conversation with, several adjacent strands of work:

- **Geoffrey Litt** (Ink & Switch, Notion) — local-first personal software, malleable software, "Stevens" (the SQLite family assistant). The closest intellectual neighbor in framing.
- **Mario Brcic** — "AI Memory Sovereignty Strategy" (May 2025), framing memory ownership as a sovereignty question.
- **Khoj** — self-hostable personal AI second brain (`khoj-ai/khoj`).
- **Letta, Mem0, Personal.ai** — commercial memory layers for AI agents. This spec differs by being format-only and worker-facing rather than framework or product.

Personal AI Architecture differs from each of the above by being (1) worker-facing rather than developer-or-enterprise-facing, (2) format-only rather than framework-or-product, (3) workbook-paired, (4) bilingual English / Korean as a first-class concern.

## Versioning

This specification follows semantic versioning at the document level. v1.0.0 ships when sections 01-07 reach RC status. Pre-1.0 sections are draft; reference implementations should pin to a specific draft SHA.

Changes between minor versions are documented in `CHANGELOG.md` at the root of this repository.

## License

This specification is published under **CC BY 4.0**. The reference implementation (`thedimode/operator-stack`) is published under **MIT**. The maintainer's personal proof artifact (`thedimode/thedimode`) is published under **CC BY-NC 4.0** (attribution, non-commercial; the personal artifact is reference material, not a template to commercially repackage).

## Status

**v0.9 (Draft).** Open for citation and reference. Not yet RC. Comments and issues welcome via GitHub Issues on this repository. The maintainer is the sole author at v0.9; contributor governance opens at v1.0.

---

*Built and maintained by Timothy Shin. California attorney. Korea digital-asset policy advisor. Operator of the system this specification describes.*
