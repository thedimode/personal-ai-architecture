# Personal AI Architecture · Roadmap

**Status as of 2026-05-21:** v0.9 (Draft). README scaffolding only. First specification sections target v0.10.

This roadmap is the source of truth for what is currently in this repository, what is in development, and what is planned. The README does not promise content that does not exist on disk; this file is where the schedule lives.

## What is in this repository today

- `README.md` — manifesto, three flags, prior-art acknowledgments, license rationale
- `LICENSE` — CC BY 4.0
- `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `CHANGELOG.md`, `ROADMAP.md` (this file)

## v0.10 target — first specification section ships

| Section | Description | Status |
|---|---|---|
| `01-identity-files` | `profile.md` and `persona_profile.md` schemas, sections, required fields, worked example, compliance test list | In progress, target Q3 2026 |

## v0.11 → v0.13 targets — remaining identity and state layers

| Section | Description |
|---|---|
| `02-state-files` | `decisions.md`, `current_state.md`, `session_log.md` schemas, append rules, retention |
| `05-autonomy-ladder` | Five-stage operator-defined autonomy levels, promotion and demotion rules |
| `06-recall-protocol` | Standardized retrieval invocation patterns |

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

Pre-1.0 ships at draft quality with potentially breaking schema changes between minor versions. v1.0 ships when all seven sections reach RC and at least one external compliant implementation exists.
