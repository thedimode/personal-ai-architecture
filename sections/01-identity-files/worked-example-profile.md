# Worked example · profile.md

**Status:** Draft (v0.1)
**Last updated:** 2026-05-21
**Section:** [01 · Identity files](./README.md)

This is a worked example of a compliant `profile.md` file. The example is the maintainer's own profile, sanitized per the `thedimode/thedimode` repository's published version. Use it as a template for shape, not for content.

See also: the unsanitized live version at [thedimode/thedimode/identity/profile.md](https://github.com/thedimode/thedimode/blob/main/identity/profile.md) (also sanitized, but in production use).

---

```markdown
---
spec: https://github.com/thedimode/personal-ai-architecture/tree/main/sections/01-identity-files
schema: profile.v1
last_updated: 2026-05-21
canonical: true
language: en
---

# profile.md

## Who I am

US-born, raised between California and Korea. Trained as a lawyer in the
United States, currently licensed in California. Father of two. Husband to
someone who is the better operator of the two of us.

I run three distinct working surfaces in parallel: a regulatory advisory
practice in digital assets, an education company my wife and I founded, and
an AI-content / writing identity that bridges the two.

## What I am working on right now

- Co-authoring a parenting book due to a Korean trade publisher.
- Building the curriculum and the technical platform for the education
  company. Founding members onboard in three weeks.
- Advising a small number of digital-asset clients on Korea-side regulatory
  strategy.
- Maintaining an opinionated Korean-language AI identity for a small but
  high-signal audience.

## How I think

I read fast and write slowly. I see structure before content. I trust
people who name failure modes more than people who promise upside. I
cannot work with half-baked work, so I would rather wait three days for
the right answer than ship two days of plausible-but-wrong work.

## How I want AI to work with me

I want a partner, not a chatbot. I want the AI to know my projects, my
voice, my deadlines, and the people I work with. I will not re-explain
my context in every session.

I expect the AI to push back when I am wrong. Sycophancy is the single
fastest way to lose my trust.

I want bulk delivery on locked specs, not gate-by-gate approval. When a
spec is locked, ship in full; I will spot-check. When a spec is open,
ask the right question once, not piecemeal.

## What I am not

- Not a software engineer by training. I read code and edit code; I do
  not write systems from scratch.
- Not an extrovert.
- Not a believer in productivity hacks. I am a believer in operational
  discipline and identity coherence.

## My core constraint

Time, and the cost of context-switching across the three surfaces.

## My core ambition

To be ahead of where AI takes the rest of the professional class in five
years. Not by guessing the future, but by building the operating system
that lets me move at the pace the next five years will require.

## Ground rules for any AI working with me

- English by default, unless I write in Korean.
- Brief. Lead with the point. Length only when warranted.
- No em dashes. Use commas, periods, colons.
- Name the tradeoffs honestly. Do not make recommendations sound free.
- If a deliverable is for my wife, my Korean clients, or my Korean
  audience: write in Korean from scratch. Do not translate.
- If you do not know, say you do not know. Do not fake context.
```

---

## What this example demonstrates

**Required frontmatter present and valid.** `spec`, `schema`, `last_updated`, `canonical`, optional `language`.

**All eight required H2 sections present, in order, non-empty.** Each section is within the recommended length band.

**No forbidden content.** No client names, no credentials, no family identifiers beyond the role ("father of two," "husband") that the operator has chosen to make public.

**Word count: ~520 words.** Within the recommended 500-1,500 range. Lean toward the low end because this is loaded into every session and the operator chose to bias toward attention-budget protection.

**Voice is the operator's own.** Short sentences, declarative register, no marketing copy. An AI loaded with this file will produce work that sounds like the operator, not work that sounds like an AI imitating the operator.

## What this example is not

This is not a template to copy verbatim. The content is the maintainer's. Yours will be different because you are a different person. Use this for shape, length calibration, and section structure. Generate your content via [Prompt 1 (Quick Profile Interview)](https://github.com/thedimode/operator-stack/blob/main/prompts/01-quick-profile-interview.md).
