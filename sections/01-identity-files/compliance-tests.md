# Compliance tests · Section 01 (Identity files)

**Status:** Draft (v0.1)
**Last updated:** 2026-05-21
**Section:** [01 · Identity files](./README.md)

A `profile.md` or `persona_profile.md` file is compliant with this section's schemas if and only if it passes all tests below. These tests are deliberately implementation-agnostic. They can be run by hand, in a CI shell script, with a markdown linter, or with an LLM-as-judge — the spec does not mandate the runner.

## Tests for `profile.md` (profile.v1)

### T01.1 · Frontmatter is present and valid
- The file MUST begin with a YAML frontmatter block delimited by `---`.
- The frontmatter MUST contain `spec`, `schema`, `last_updated`, `canonical`.
- `schema` MUST equal `profile.v1`.
- `last_updated` MUST be an ISO 8601 date.
- `canonical` MUST be a boolean.

### T01.2 · Required body sections are present, in order
- The body MUST contain these H2 headings, in this order:
  - `## Who I am`
  - `## What I am working on right now`
  - `## How I think`
  - `## How I want AI to work with me`
  - `## What I am not`
  - `## My core constraint`
  - `## My core ambition`
  - `## Ground rules for any AI working with me`
- Each section MUST contain at least one sentence (≥1 period or terminal punctuation followed by at least one word in the next paragraph).

### T01.3 · Length is within recommended bounds OR deviation is noted
- The body (excluding frontmatter) SHOULD be between 500 and 1,500 words.
- Files outside this range MUST include a comment or sentence acknowledging the deviation and the reason.

### T01.4 · File encoding is UTF-8 plain markdown
- The file MUST be UTF-8 encoded.
- The file MUST NOT require HTML rendering to be readable.
- The file MUST NOT contain unescaped raw HTML beyond what standard markdown permits.

### T01.5 · No forbidden content
- The file MUST NOT contain authentication credentials, API keys, secret tokens, or any string matching common credential patterns.
- The file MUST NOT contain client names, project codenames, or attorney-client privileged information.
- The file MUST NOT contain family member identifying information beyond what those members have made public.

### T01.6 · Not silently mutated
- The file's git history (if version-controlled) MUST show all updates as deliberate commits by the operator or by an AI tool call the operator authorized.
- The file MUST NOT have updates from automatic background processes that the operator did not see.
- (This test is process-based, not file-content-based. Implementations enforce it via hook configuration or operator discipline.)

## Tests for `persona_profile.md` (persona-profile.v1)

### T01.7 · Frontmatter is present and valid
- Required fields: `spec`, `schema`, `last_updated`, `last_meaningful_refresh`, `canonical`, `source`.
- `schema` MUST equal `persona-profile.v1`.

### T01.8 · Required body sections are present, in order
- The body MUST contain these H2 headings, in this order:
  - `## One sentence`
  - `## Identity and background`
  - `## True north`
  - `## Core message`
  - `## Confidence map`
  - `## Executive summary`
  - `## Voice characteristics`
  - `## Operating patterns`
  - `## Decision-making patterns`
  - `## Relational patterns`

### T01.9 · Confidence map has three tiers
- The `## Confidence map` section MUST distinguish three tiers, each as a labeled subsection:
  - `### Strongly grounded` (or equivalent)
  - `### Reasonable inference` (or equivalent)
  - `### Observed live` (or equivalent)
- Each tier MUST contain at least three observations.

### T01.10 · Length is within recommended bounds OR deviation is noted
- The body SHOULD be between 4,000 and 8,000 words.
- Outside this range MUST be noted.

### T01.11 · File encoding is UTF-8 plain markdown
- Same as T01.4.

### T01.12 · No forbidden content
- Same as T01.5.

### T01.13 · Not silently mutated
- Same as T01.6, applied with extra force per the section overview.

## Running these tests

The reference implementation provides a `compliance/` directory (forthcoming in v0.10) with shell scripts and a Python validator. Until then, tests can be run by hand against the schemas in this section.

A simple structural check using `awk` or `grep` can verify T01.1 through T01.4, T01.7 through T01.11. Forbidden-content checks (T01.5, T01.12) require either a credential-pattern scanner (e.g. `gitleaks`, `trufflehog`) or operator review. The "not silently mutated" tests (T01.6, T01.13) are process-based and enforced through hook configuration; the reference implementation's hook setup is the canonical example.
