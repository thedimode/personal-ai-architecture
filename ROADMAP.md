# Personal AI Architecture · Roadmap

**Status as of 2026-05-24:** v0.9 (Draft). Section 01 (Identity files) shipped at draft v0.1 on 2026-05-22. Remaining sections in development.

This roadmap is the source of truth for what is currently in this repository, what is in development, and what is planned. The README does not promise content that does not exist on disk; this file is where the schedule lives.

## What is in this repository today

- `README.md` — manifesto, three flags, prior-art acknowledgments, license rationale
- `LICENSE` — CC BY 4.0
- `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `CHANGELOG.md`, `ROADMAP.md` (this file)
- **`sections/01-identity-files/`** — shipped at draft v0.1:
  - `README.md` — normative overview
  - `profile-schema.md` — `profile.v1` schema (frontmatter + required body sections + length bounds + compliance rules)
  - `persona-profile-schema.md` — `persona-profile.v1` schema
  - `worked-example-profile.md` — a worked example of a compliant `profile.md`
  - `compliance-tests.md` — 13 compliance tests (T01.1 through T01.13)

## v0.10 target — remaining identity and state layers begin

| Section | Description | Status |
|---|---|---|
| `02-state-files` | `decisions.md`, `current_state.md`, `session_log.md` schemas, append rules, retention | Spec drafting · target Q3 2026 |
| `05-autonomy-ladder` | Five-stage operator-defined autonomy levels, promotion and demotion rules | Design phase |
| `06-recall-protocol` | Standardized retrieval invocation patterns | Design phase |

## v0.11+ candidates (added 2026-05-24)

| Section | Description | Why it's a candidate |
|---|---|---|
| `08-meeting-intelligence` | Capture-surface pattern for meeting transcripts: archive schema, counterparty extraction, project threading, commitment ledger, decision enrichment, coactivation with vault embeddings | A documented working layer in the maintainer's stack since 2026-05-23 ([reference implementation](https://github.com/thedimode/thedimode/blob/main/architecture/meeting-intelligence.md)). Surfaces enough that other operators with similar workflows would benefit from a standard schema. |

A section is promoted from candidate to roadmap when there is at least one running implementation and the abstraction is stable enough to standardize.

## v1.0 RC targets

| Section | Description |
|---|---|
| `03-skill-schema` | Description-triggered auto-loading skill manifest format |
| `04-hook-lifecycle` | Standardized hook events (session start, prompt submit, tool call, session stop) |
| `07-fact-capture` | Append-only fact buffer plus nightly consolidation pattern |

## Out of scope (intentional)

This specification is format-only. It does not standardize:

- Which LLM provider you use
- Which editor or interface you use
- Which scheduler or orchestrator you use
- Whether you run locally, on a server, or in a container

These are runtime decisions left to the implementer. The reference implementation ([operator-stack](https://github.com/thedimode/operator-stack)) demonstrates one set of choices; others are equally valid.

## Versioning

Pre-1.0 ships at draft quality with potentially breaking schema changes between minor versions. v1.0 ships when all seven core sections (01-07) reach RC and at least one external compliant implementation exists. v0.11+ candidates may merge into the v1.0 set or remain as supplemental schemas depending on adoption.
