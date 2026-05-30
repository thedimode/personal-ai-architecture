# Section 01 · Identity files

**Status:** Draft (v0.1)
**Last updated:** 2026-05-21
**Section of:** [Personal AI Architecture v0.9](../../README.md)

This section specifies the two identity files every compliant Operator Stack must maintain: `profile.md` and `persona_profile.md`. These are the load-bearing artifacts that make the operator's AI know who they are without re-explanation.

## Contents

- [Normative overview](#normative-overview) (this file, below)
- [profile schema](./profile-schema.md)
- [persona-profile schema](./persona-profile-schema.md)
- [Worked example: profile.md](./worked-example-profile.md)
- [Compliance tests](./compliance-tests.md)

---

## Normative overview

### Purpose

The identity layer answers the question "who is the operator?" in a form the AI can read at the start of every session. Two files split the question by depth:

- **`profile.md`** is the short, stable, ground-rules document. ~500 to 1,500 words. Loaded at the start of every session.
- **`persona_profile.md`** is the long, voice-extracted, evolving document. ~4,000 to 8,000 words. Loaded when the task requires deep voice or judgment fidelity.

Implementations MUST maintain both files. Implementations MAY consolidate them into a single file at the operator's choice, but compliance with both schemas is required regardless of file layout.

### File location

Both files live in an `identity/` directory at the root of the operator's working tree. Implementations MAY use alternative paths so long as the loader prompt is updated accordingly. The reference implementation uses `identity/profile.md` and `identity/persona_profile.md`.

### Encoding

Files MUST be UTF-8 encoded plain text. Files MUST use markdown syntax. Files MUST be readable as plain text without rendering (no required HTML, no required custom markup).

### Frontmatter

Both files MUST begin with YAML frontmatter containing at minimum:

```yaml
---
spec: <URL or repo path to the active specification version>
schema: <schema name and version, e.g. profile.v1>
last_updated: <ISO 8601 date>
canonical: true
---
```

Implementations MAY include additional frontmatter fields. Common optional fields: `language`, `salience`, `derived_from`, `prior_snapshot`.

### Lifecycle requirements

- **Loaded at session start.** The operator's session-start hook or loader prompt MUST read `profile.md` and inject it into the active context. `persona_profile.md` MAY be loaded selectively based on the task.
- **Not silently mutated.** The AI MUST NOT silently rewrite either file. All updates to identity files MUST be visible to the operator (either as an explicit edit, an explicit AI tool call the operator authorized, or an explicit ritual the operator runs).
- **Versioned.** Both files MUST be tracked in version control. Implementations MUST be able to show the history of any field.

The "not silently mutated" requirement is load-bearing. It is the principle behind which silent-persona-delta capture protocols fail (see [thedimode/architecture/failure-cases.md](https://github.com/thedimode/thedimode/blob/main/architecture/failure-cases.md) for a worked example of why).

### Refresh cadence

The specification does not mandate a refresh cadence. The reference implementation refreshes `profile.md` quarterly with monthly meaningful updates, and `persona_profile.md` every six months with weekly observation accumulation. Operators MAY choose any cadence that maintains fidelity.

### Sanitization for publication

If an operator publishes their identity files publicly (as the maintainer does in [thedimode/thedimode](https://github.com/thedimode/thedimode)), the published version MUST include a sanitization disclosure stating what was removed and what was preserved. Sanitization MUST NOT alter the file's structural or voice integrity.

## Why this section is load-bearing

Without identity files, every AI session begins by re-establishing context the operator has established before. The cost is paid in time (re-explanation), quality (the AI generates more median work because it cannot model the user), and trust (the operator cannot rely on the AI to remember constraints that were named yesterday).

Vendor-managed memory (ChatGPT Memory, Claude Projects, Gemini Saved Info) is the platform-locked alternative to this section. The flags in the [project README](../../README.md) name why platform-locked memory is the wrong answer for an operator who intends to be vendor-portable.

## Relationship to other sections

- **Section 02 (State files)** extends identity-as-context with state-as-context: what the operator is doing right now, what decisions are locked, what the last session produced.
- **Section 05 (Autonomy ladder)** depends on identity files to calibrate trust per task per skill.
- **Section 06 (Recall protocol)** uses the identity files as the highest-priority retrieval anchor.

## Open questions for v0.2

- Should `profile.md` mandate a maximum word count? (Argument for: protects against bloat. Argument against: rigid limits punish operators with multi-language stacks.)
- Should `persona_profile.md` mandate a confidence map for observed-vs-asserted patterns? (The reference implementation uses one; whether to standardize is open.)
- Should there be a third file for `voice_corpus/` (a directory of raw voice samples)? (Open: too implementation-coupled to standardize, or load-bearing enough to standardize?)

Comments welcome via [issues](https://github.com/thedimode/the-dimode-method/issues).

## Status

**Draft v0.1.** Schema is stable enough to implement against; field naming may evolve before RC. Pin to a SHA in your implementation.
