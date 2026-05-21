# Schema · profile.v1

**Status:** Draft (v0.1)
**Last updated:** 2026-05-21
**Section:** [01 · Identity files](./README.md)

The schema for a compliant `profile.md` file. This is a markdown-with-frontmatter schema, not a JSON-only schema, because the file is read by both humans and LLMs.

## Frontmatter (required)

```yaml
---
spec: <URL or repo path to the active Personal AI Architecture specification version>
schema: profile.v1
last_updated: <ISO 8601 date, e.g. 2026-05-21>
canonical: true
---
```

| Field | Type | Required | Description |
|---|---|---|---|
| `spec` | string | yes | URL or repo-relative path to the specification version this file conforms to. |
| `schema` | string | yes | The schema identifier and version, currently `profile.v1`. |
| `last_updated` | date | yes | ISO 8601 date of the last meaningful update. |
| `canonical` | boolean | yes | Must be `true` for the active profile. Multiple profiles may exist; only one is canonical at a time. |
| `language` | string | no | BCP 47 language tag (e.g. `en`, `ko`). Defaults to `en` if absent. |
| `derived_from` | string | no | Source of the profile (e.g. `voice_corpus`, `interview_session_001`). |
| `prior_snapshot` | string | no | Path to the previous version, if archived. |

## Body sections (required and ordered)

The body MUST contain the following H2 sections in this order. Each section MUST contain at least one sentence.

| Section heading | Purpose | Length target |
|---|---|---|
| `## Who I am` | One- to three-paragraph identity statement. Includes location, profession, family role, and the working surfaces being run in parallel. | 50-200 words |
| `## What I am working on right now` | Bulleted or paragraph list of the operator's currently active projects, with status. Updated on every meaningful change. | 50-200 words |
| `## How I think` | The operator's cognitive style. How they reason, what they trust, what they distrust. | 50-200 words |
| `## How I want AI to work with me` | The operator's stated preferences for AI behavior. Tone, register, push-back posture, delivery patterns. | 100-300 words |
| `## What I am not` | Negative-space identity. Disclaimers about expertise, posture, personality that the AI should not assume. | 30-150 words |
| `## My core constraint` | The single load-bearing limit on the operator's work. (Time, attention, context-switching, etc.) | 20-100 words |
| `## My core ambition` | The single load-bearing direction of the operator's work. | 20-100 words |
| `## Ground rules for any AI working with me` | A bulleted list of operational rules. The AI MUST treat these as standing instructions. | 50-300 words |

## Body sections (optional)

Implementations MAY include additional H2 sections after the required ones. Common optional sections:

- `## Public-facing thesis` — one-paragraph statement of the operator's public position
- `## Voice corpus` — pointers to the voice corpus directory or raw voice samples
- `## Working hours` — preferred deep-work windows
- `## Confidence map` — observed-vs-asserted patterns (more typically lives in `persona_profile.md`)

## What MUST NOT appear in profile.md

- Client names, project codenames, or any client-privileged information.
- Authentication credentials, API keys, or any secret material.
- Family members' identifying information beyond what they themselves have made public.
- Information the operator would not want loaded into every session's context.

The principle: `profile.md` is loaded into every session. Anything sensitive enough that the operator would not want it in *every* session does not belong here. It belongs in a more carefully gated artifact.

## Length constraints

`profile.md` SHOULD be between 500 and 1,500 words. Files under 500 words underspecify identity and produce thin AI behavior. Files over 1,500 words bloat the session context budget and crowd out task-specific context. Implementations MAY exceed these bounds with explicit operator awareness of the tradeoff.

## Update protocol

- Updates MUST be made by either the operator directly or an AI tool call the operator explicitly authorized.
- Updates MUST NOT be silent. Any automatic process modifying `profile.md` MUST surface the diff to the operator within the same session.
- The `last_updated` field MUST be updated on every meaningful change.
- The file SHOULD be tracked in version control. The reference implementation uses git.

## Compliance

A `profile.md` file is compliant with `profile.v1` if and only if:

1. Frontmatter contains all required fields with valid values.
2. All required H2 body sections are present, in order, and non-empty.
3. The file is UTF-8 encoded markdown.
4. The file contains no forbidden content (credentials, client-privileged information, etc.).
5. The file is within the recommended length bounds, or the implementation explicitly notes the deviation.

Compliance tests are listed in [compliance-tests.md](./compliance-tests.md).

A worked example of a compliant `profile.md` is in [worked-example-profile.md](./worked-example-profile.md).
