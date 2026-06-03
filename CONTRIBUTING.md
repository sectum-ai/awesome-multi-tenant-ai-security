# Contributing

Thanks for helping curate this list. The scope is intentionally narrow:
**multi-tenant / cross-tenant AI security** — keeping one tenant's or one
user's data from reaching another across an AI system's surfaces (vector
DB, RAG pipeline, semantic and KV caches, agent memory, MCP tool calls,
fine-tunes and adapters, eval sets, backups, search indexes, tracing).
General "AI security" or "LLM safety" content belongs elsewhere.

## Pull-request template

Open a PR titled `Add <Name> to <Section>` (e.g. `Add Weaviate to Vector
databases with multi-tenancy capabilities`). Include in the description:

```
**Item:** <Name>
**Section:** <which README section>
**Link:** <canonical URL>

**Why it fits:** <1–2 sentences. Tie it explicitly to multi-tenant /
cross-tenant AI security: what the item says about, detects, prevents,
or measures cross-tenant leakage.>

**Maintained / current as of:** <date you last verified the link works
and the project is alive>
```

For papers and advisories, prefer the publisher's canonical URL (arXiv
abstract page, vendor advisory, OWASP / NIST / ISO page). For tools,
prefer the source repository over a marketing page.

## What gets accepted

- **Real, factual, currently maintained** resources. Tools that have had a
  commit, release, or advisory within roughly the last 18 months. Papers
  and standards that are still the canonical reference for what they
  cover.
- **Primary sources.** The actual paper, the actual advisory, the actual
  repository — not a tweet, a vendor blog summarizing someone else, or a
  third-party "top N" listicle.
- **Working links.** Verify the URL resolves and points at the right
  thing.
- **Neutral, factual descriptions.** One short sentence that says what the
  item is and why it bears on multi-tenant AI security. No marketing
  language ("revolutionary", "industry-leading", "next-gen").
- **Honest categorization.** Put tools in the section that matches the
  layer they actually operate on, not the one that flatters them. Listing
  a runtime guardrail under "multi-tenant AI verification" because it has
  a tenant filter does not help readers.

## What gets rejected

- **Vapor.** Vendor pages for products that have not shipped, do not have
  public documentation of the relevant feature, or whose claimed
  capability is not described anywhere verifiable.
- **Marketing pages without substance.** A press release announcing a
  feature is not a reference; the feature's documentation is.
- **Dead links.** Broken URLs, abandoned projects (no commits in 2+
  years, no recent releases), or papers withdrawn / superseded with no
  pointer to the replacement.
- **Off-topic AI security.** Generalist LLM red-teaming, prompt-injection
  defense, model supply-chain scanning, AI governance frameworks — these
  are valuable, but they belong on a different awesome list. Only items
  that bear directly on the *cross-tenant* surface belong here.
- **Self-promotion without substance.** Your own tool can be listed, but
  the description must be neutral and factual; the same standard applies
  to Sectum AI's own entry.

## Style

- One item per line: `- [Name](https://link) — short, factual description.`
- Place the item in the most relevant section; add or rename a section in
  the PR if none fits (and say so in the description).
- Alphabetize within a section where it doesn't break a logical ordering.
- Run a spell check; use plain ASCII punctuation; keep descriptions to
  roughly one sentence.

## Code of conduct

Participation is governed by the
[Contributor Covenant Code of Conduct](code-of-conduct.md). Treat
contributors and competitors with the same standard of fairness — this
list is more useful if it represents the landscape honestly.

## License

By contributing, you agree that your contribution is released under
[CC0-1.0](LICENSE), the same dedication that covers the rest of this
list.
