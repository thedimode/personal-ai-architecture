# Schema · persona-profile.v1

**Status:** Draft (v0.1)
**Last updated:** 2026-05-21
**Section:** [01 · Identity files](./README.md)

The schema for a compliant `persona_profile.md` file. Where `profile.md` answers "who is the operator?" at the level of ground rules, `persona_profile.md` answers it at the level of voice, judgment, and observed working pattern.

## Relationship to profile.md

- `profile.md` is loaded into **every** session. Constraint: must stay small.
- `persona_profile.md` is loaded **selectively**, when the task requires deep voice or judgment fidelity. Constraint: must be deep enough to actually move AI behavior.

If `profile.md` is the operator's identity card, `persona_profile.md` is the operator's voice corpus distilled into an AI-readable profile.

## Frontmatter (required)

```yaml
---
spec: <URL or repo path>
schema: persona-profile.v1
last_updated: <ISO 8601 date>
last_meaningful_refresh: <ISO 8601 date>
canonical: true
source: <e.g. voice-extraction-session, or voice-corpus-synthesis>
---
```

| Field | Type | Required | Description |
|---|---|---|---|
| `spec` | string | yes | URL or repo path to the active specification version. |
| `schema` | string | yes | `persona-profile.v1`. |
| `last_updated` | date | yes | ISO 8601 date of last edit. |
| `last_meaningful_refresh` | date | yes | ISO 8601 date of last deep refresh (not minor edits). |
| `canonical` | boolean | yes | Must be `true` for the active persona. |
| `source` | string | yes | How the file was generated (`voice-extraction-session`, `voice-corpus-synthesis`, `manual`). |
| `language` | string | no | BCP 47 language tag. |
| `salience` | float | no | Decimal 0.0 to 1.0 indicating priority weight if multiple persona files exist. |

## Body sections (required and ordered)

| Section heading | Purpose | Length target |
|---|---|---|
| `## One sentence` | A single-sentence self-description. Quoted from the operator. | 1 sentence |
| `## Identity and background` | Bullet-list of identity facts: nationality, training, languages, profession, family role, faith stance (if relevant), age band. | 100-300 words |
| `## True north` | The operator's identity anchor or guiding metaphor. | 50-200 words |
| `## Core message` | The operator's public-facing thesis, in their own voice. | 50-200 words |
| `## Confidence map` | A three-tier classification of observed patterns: **strongly grounded** (observed many times), **reasonable inference** (consistent but limited observation), **observed live** (recent additions, watching for confirmation). Each pattern is one bullet. | 500-2,000 words |
| `## Executive summary` | A one-paragraph synthesis the AI can use as a quick-load when full file is not needed. | 100-300 words |
| `## Voice characteristics` | How the operator writes and speaks. Cadence, register, vocabulary, what they avoid. | 200-500 words |
| `## Operating patterns` | When and how the operator works. Time-of-day windows, energy patterns, context-switching tolerance, sleep patterns if relevant. | 100-300 words |
| `## Decision-making patterns` | How the operator makes calls. Risk tolerance, what they need to commit, what triggers pause. | 100-300 words |
| `## Relational patterns` | How the operator works with collaborators. Trust criteria, push-back posture, what causes loss of trust. | 100-300 words |

## Body sections (optional)

- `## Failure modes I am known for` — self-described patterns the operator does not want to repeat
- `## Open questions about myself` — patterns the operator is still observing and uncertain about
- `## Reference materials` — pointers to voice corpus, prior persona snapshots, voice-extraction session transcripts

## What MUST NOT appear in persona_profile.md

- Client names or client-privileged information.
- Authentication credentials.
- Family members' identifying information beyond what they themselves have made public.

Unlike `profile.md`, `persona_profile.md` MAY contain more sensitive identity material because it is loaded selectively, not on every session. But the operator's discretion governs.

## Length constraints

`persona_profile.md` SHOULD be between 4,000 and 8,000 words. Files under 4,000 words underspecify voice and fail to move AI behavior beyond what `profile.md` provides. Files over 8,000 words exceed practical context-loading thresholds for many runtimes and should be split into a base file plus selectively-loaded subsections.

## Update protocol

- Updates MUST be either operator-direct or via an AI tool call the operator explicitly authorized.
- The `last_meaningful_refresh` field MUST be updated on every deep refresh; minor edits update `last_updated` only.
- The "not silently mutated" rule from the section-level overview applies with extra force here. Persona files that are updated silently drift from the operator's actual voice without the operator's knowledge. The [thedimode failure-cases file](https://github.com/thedimode/thedimode/blob/main/architecture/failure-cases.md) documents an instance.

## Update cadence (recommended, non-normative)

The reference implementation uses:

- **Weekly:** observation accumulation in a `persona_deltas/` directory (separate file per delta, never written silently — operator runs a deliberate `persona-delta-capture` ritual)
- **Monthly:** review deltas, promote high-confidence ones into the canonical persona_profile.md
- **Quarterly:** deep voice-extraction session refresh

Implementations MAY use any cadence that maintains fidelity. The constraint is not the cadence; it is that updates are deliberate and visible.

## Compliance

A `persona_profile.md` file is compliant with `persona-profile.v1` if and only if:

1. Frontmatter contains all required fields with valid values.
2. All required H2 body sections are present, in order, and meet length minima.
3. The Confidence Map distinguishes strongly grounded / reasonable inference / observed live tiers.
4. The file is UTF-8 encoded markdown.
5. The file contains no forbidden content.

Compliance tests are in [compliance-tests.md](./compliance-tests.md).
