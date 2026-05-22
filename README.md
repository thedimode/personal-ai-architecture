# Personal AI Architecture

**Status:** v0.9 (Draft) · See [ROADMAP.md](./ROADMAP.md)
**Maintainer:** Timothy Shin · [thedimode.com](https://thedimode.com)
**License:** [CC BY 4.0](./LICENSE)

Your AI does not remember you. It remembers what its vendor decided to let it remember, until the vendor changes its mind.

Personal AI Architecture is the discipline of owning your AI in files you control, in formats you can carry between models. This repository is its specification.

## The Personal AI Architecture project

- **thedimode/personal-ai-architecture** — the specification (this repo)
- [thedimode/operator-stack](https://github.com/thedimode/operator-stack) — reference implementation (MIT)
- [thedimode/thedimode](https://github.com/thedimode/thedimode) — the maintainer's personal proof artifact (CC BY-NC 4.0)
- [thedimode.com/handbook](https://thedimode.com/handbook) — the handbook that teaches the discipline

## The three flags

This specification rests on three claims. Each addresses a specific, evidenced failure mode of platform-locked AI.

### Flag 1 · Your AI should remember who you are, and that memory should survive the vendor's next update.

Platform-managed memory has demonstrably failed this test. Vendor backend updates have silently wiped many users' saved memories. Context resets between sessions remain a daily reality for paying users. The discipline requires identity persistence as a property of the user's files, not the vendor's database.

### Flag 2 · You should own your AI's memory in files you can read, edit, and carry between models.

Vendor-managed memory creates three failure modes simultaneously: lock-in (memory does not export), silent corruption (context compaction destroys project instructions without notice), and siloed visibility (projects do not share with standalone chats). The discipline replaces all three by treating memory as plain text on the user's disk, structured by an open schema, version-controlled with git, and portable between models.

### Flag 3 · Your AI workflow should keep working when the vendor goes down, raises prices, or changes the model under you.

Multi-hour outages, simultaneous multi-vendor incidents, subscription-tier reshuffles, and silent model behavior shifts have repeatedly broken carefully tuned workflows. The discipline requires the operator's workflow to be vendor-resilient: portable identity, portable memory, portable skill definitions, and (optionally) local-model fallback for graceful degradation.

## What this specification covers

This specification standardizes the file formats, schemas, and protocols that make a Personal AI Architecture portable. It is intentionally format-only, not vendor-coupled. Any LLM platform that can read markdown can operate against a compliant stack.

For what is currently specified, what is in draft, and what is on the roadmap, see [ROADMAP.md](./ROADMAP.md).

## What this specification does not cover

- Which LLM provider you use. Any frontier model or local open-weight model is a valid runtime.
- Which editor or interface you use.
- Which scheduler or orchestrator you use.
- Whether you run locally, on a server, or in a container.

Compliance is about file format, not infrastructure. This is a portable-format standard, like RSS or Markdown.

## Why three licenses

The Personal AI Architecture project ships three repositories under three different licenses, each chosen for what the artifact is rather than uniform convenience.

- **The specification** (this repo) is CC BY 4.0. A standard is most useful when it can be cited, reproduced, and built upon for any purpose, including commercial. Attribution preserves authorship and tells readers where the source of truth lives.
- **The reference implementation** ([operator-stack](https://github.com/thedimode/operator-stack)) is MIT. Code intended for forking should impose the lightest possible obligation on the forker.
- **The personal proof artifact** ([thedimode/thedimode](https://github.com/thedimode/thedimode)) is CC BY-NC 4.0. The maintainer's own running stack is reference material, not a template to be commercially repackaged.

## Acknowledgments and prior art

This specification builds on, and is in conversation with, several strands of work:

- **Geoffrey Litt** (Ink & Switch, Notion) — local-first personal software, malleable software, "Stevens" (the SQLite family assistant). The closest intellectual neighbor in framing.
- **Gordon Brander** ([Subconscious](https://subconscious.network)) — self-sovereign personal computing in the AI era. Flag 3 is downstream of Brander's noosphere framing applied to LLMs.
- **Andy Matuschak** — evergreen notes, working notes, public working-with-AI threads. The instinct that personal knowledge structures should be ones the user maintains, not consumes.
- **Maggie Appleton** — digital gardens, end-user AI essays.
- **Simon Willison** — public agentic-engineering patterns, the [LLM CLI tool](https://github.com/simonw/llm), the model of practitioner-publisher who ships what they actually use.
- **Mario Brcic** — "AI Memory Sovereignty Strategy" (2025), framing memory ownership as a sovereignty question.
- **Khoj, Letta, Mem0, Personal.ai** — open and commercial memory layers for AI agents. This specification is complementary: format-only and worker-facing, where they are framework-or-product.

Personal AI Architecture differs from these by being (1) worker-facing rather than developer-or-enterprise-facing, (2) format-only rather than framework-or-product, (3) bilingual English and Korean as a first-class concern, (4) paired with an [Operator's Handbook](https://thedimode.com/handbook) that teaches the discipline as guided practice (because the discipline cannot be acquired by reading a spec alone).

## How to cite

A `CITATION.cff` file will land at v1.0. For draft citations:

```
Shin, Timothy. Personal AI Architecture: A Specification.
v0.9 (Draft), 2026.
https://github.com/thedimode/personal-ai-architecture
```

## Contributing

Issues and pull requests welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md). For security disclosures, see [SECURITY.md](./SECURITY.md).

The maintainer is the sole author at v0.9. Contributor governance opens at v1.0.

---

Built and maintained by Timothy Shin · AI Operator.
