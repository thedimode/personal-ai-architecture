# Contributing to Personal AI Architecture

Thanks for your interest in contributing to the Personal AI Architecture specification. This document explains how to file issues, propose changes, and submit pull requests.

The specification is published under [CC BY 4.0](./LICENSE). By contributing you agree your contributions are licensed under the same terms.

## Before you contribute

- Read the [README](./README.md) and the current [ROADMAP](./ROADMAP.md).
- Check open and closed [issues](https://github.com/thedimode/the-dimode-method/issues) so you do not duplicate existing discussion.
- Review the [Code of Conduct](./CODE_OF_CONDUCT.md). It applies to all interaction in this repository.

## Three kinds of contribution

This specification accepts three kinds of contribution, each with a different process.

### 1. Specification changes

Changes to the schemas, protocols, or normative text in any of the section files (`01-identity-files` through `07-fact-capture` once shipped).

- File an issue first, labeled `spec-proposal`, describing the change and its motivation.
- For substantive changes, expect discussion before a PR is reviewed. Pre-1.0 schemas may change between minor versions; post-1.0 changes follow stricter compatibility rules.
- PRs must include a `CHANGELOG.md` entry under `[Unreleased]`.

### 2. Documentation and prior-art

Improvements to the README, the prior-art acknowledgments, the citation block, or any non-normative explanatory text.

- These can be filed as PRs directly without prior issue.
- For prior-art additions, include a one-line rationale: what makes this work relevant.

### 3. Translations

Translations of the specification into Korean, Japanese, Mandarin, Spanish, or any other language are welcome at v1.0+. Pre-1.0 translations may be useful for community feedback but should not be considered authoritative.

## AI-assisted contributions

If you used an AI tool to draft any part of your contribution, disclose it in the PR description. A line like *"This PR was drafted with Claude / ChatGPT / Cursor and reviewed by me"* is sufficient. The disclosure is not a quality bar; it is a transparency norm consistent with how the spec itself treats memory and identity.

## Filing a good issue

- One issue per topic.
- Title that names the section and the problem.
- Body that includes: what you observed, what you expected, why it matters.
- For spec proposals, include the smallest change that would address the issue.

## Pull request expectations

- Branch from `main`.
- One logical change per PR.
- Update `CHANGELOG.md` under `[Unreleased]`.
- For schema changes, include a worked example before/after.
- Pass any CI checks (added as the spec matures).

## Maintainer and governance

The maintainer is the sole author at v0.9. Contributor governance opens at v1.0; until then, the maintainer reserves the right to accept, request changes, or decline contributions based on alignment with the project's direction.

For security-relevant issues, see [SECURITY.md](./SECURITY.md) and do not file a public issue.

---

*This CONTRIBUTING.md is modeled on the contribution patterns used by the [Model Context Protocol specification](https://github.com/modelcontextprotocol/specification) and the [JSON Schema specification](https://github.com/json-schema-org/json-schema-spec).*
