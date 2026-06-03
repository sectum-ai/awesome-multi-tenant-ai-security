# Awesome Multi-Tenant AI Security [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of resources for understanding, detecting, and preventing
cross-tenant data leakage in multi-tenant AI systems — shared vector stores,
RAG pipelines, semantic and KV caches, agent memory, MCP tool calls,
fine-tunes and adapters, eval sets, backups, search indexes, and tracing
pipelines.

Multi-tenant AI systems universally claim that one tenant's (or one user's)
data cannot reach another. This list collects the research, advisories,
standards, and tools that bear on whether that claim holds up in practice.
Entries are listed neutrally — including this project's own OSS — so the
list stays useful as a reference rather than a marketing surface.

## Contents

- [Research](#research)
- [Tools and frameworks](#tools-and-frameworks)
- [Standards and frameworks](#standards-and-frameworks)
- [Vector databases with multi-tenancy capabilities](#vector-databases-with-multi-tenancy-capabilities)
- [MCP-related security resources](#mcp-related-security-resources)
- [Compliance mappings](#compliance-mappings)
- [Conference talks and podcasts](#conference-talks-and-podcasts)
- [Contributing](#contributing)

## Research

Foundational papers and advisories that motivate the category.

- [OWASP LLM08:2025 — Vector and Embedding Weaknesses](https://genai.owasp.org/llmrisk/llm082025-vector-and-embedding-weaknesses/) — names multi-tenant context leakage and cross-tenant access in shared vector stores as a top-10 LLM application risk.
- *Retrieval Pivot Attacks in Hybrid RAG* (arXiv, Feb 2026) — 334 of 350 *benign* queries (95.4%) triggered cross-tenant leakage in a hybrid RAG setup via shared organic entities (shared person names, vendors, compliance terms, monetary amounts, dates); stronger embedding models leaked more. *Canonical arXiv ID pending; contributions linking the final preprint are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).*
- [Silent Leaks: Implicit Knowledge Extraction Attack on RAG Systems through Benign Queries](https://arxiv.org/abs/2505.15420) — the IKEA paper: 91% extraction efficiency and 96% attack success rate against RAG systems using only benign queries, with no prompt injection.
- [Text Embeddings Reveal (Almost) As Much As Text](https://arxiv.org/abs/2310.06816) — embedding inversion reconstructs source text from embedding vectors, so cross-tenant access to an embedding store is itself a leakage path.
- [Information Leakage in Embedding Models](https://arxiv.org/abs/2004.00053) — foundational work on what embeddings disclose about their inputs.
- *Asana MCP cross-tenant data leak post-mortem* (Coalition for Secure AI, May 2025) — a cross-tenant flaw with token-passthrough as root cause; ~1,000 enterprises affected. *Coalition for Secure AI advisory; canonical URL pending — see [CONTRIBUTING.md](CONTRIBUTING.md).*
- *LiteLLM PyPI breach analysis* (Mar 2026) — compromise of a package at ~95M monthly downloads, with downstream impact confirmed at Mercor; relevant as a supply-chain motivation for evidence-chain integrity around multi-tenant AI proxies. *Vendor and security-research writeups vary; canonical post-mortem URL pending — see [CONTRIBUTING.md](CONTRIBUTING.md).*

## Tools and frameworks

Listed neutrally, in the categories buyers most often shortlist them under.
Inclusion does not imply endorsement; exclusion does not imply criticism.

### Multi-tenant AI verification

- [Sectum AI](https://github.com/sectum-ai/sectum-ai) — open-source multi-tenant AI verification (Apache-2.0): a synthetic-tenant marker substrate, a catalog of cross-tenant leakage probes covering vector DBs, caches, agents, MCP, and fine-tunes, and a tamper-evident evidence chain with an independent `sectum-ai verify` CLI. Listed here for completeness — this list is curated by the Sectum AI project.

### LLM red-team frameworks

- [DeepTeam](https://github.com/confident-ai/deepteam) — an LLM red-teaming framework from Confident AI; includes a [`CrossContextRetrieval`](https://www.trydeepteam.com/docs/red-teaming-vulnerabilities-cross-context-retrieval) vulnerability check that does a single-prompt, LLM-as-judge test for tenant/user cross-context retrieval.
- [garak](https://github.com/NVIDIA/garak) — NVIDIA's open-source LLM vulnerability scanner with probes for prompt injection, data leakage, toxicity, hallucination, and more.
- [PyRIT](https://github.com/Azure/PyRIT) — Microsoft's Python Risk Identification Tool for generative-AI red teaming; orchestrates attack strategies against LLM endpoints.
- [promptfoo](https://github.com/promptfoo/promptfoo) — LLM evaluation and red-teaming with a configurable security-test catalog covering OWASP LLM Top 10 categories.
- [Rebuff](https://github.com/protectai/rebuff) — a prompt-injection detection framework (canary-token-based heuristics plus an LLM-based classifier).

### Runtime AI security platforms

- [Lakera Guard](https://www.lakera.ai/) — a runtime guardrail / firewall for LLM applications: prompt-injection and data-leak detection inline with inference.
- [NVIDIA NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) — an open-source toolkit for programmable runtime guardrails over LLM conversations.
- [Cisco AI Defense](https://www.cisco.com/site/us/en/products/security/ai-defense/index.html) — Cisco's runtime AI security platform: model validation, inline runtime protection, and policy enforcement for enterprise AI use.
- [Protect AI](https://protectai.com/) — a portfolio covering ML supply-chain scanning ([ModelScan](https://github.com/protectai/modelscan)), LLM red-teaming ([LLM Guard](https://github.com/protectai/llm-guard)), and runtime detection.

### GRC platforms

Included because tenant-isolation testing often gets adjacently discussed
during SOC 2 / ISO 27001 scoping, even though these tools do not perform
multi-tenant AI testing themselves.

- [Vanta](https://www.vanta.com/) — automated SOC 2 / ISO 27001 / HIPAA compliance: continuous control monitoring and audit-pack assembly.
- [Drata](https://drata.com/) — automated compliance and continuous control monitoring for SOC 2, ISO 27001, HIPAA, PCI-DSS, and GDPR.

### Privacy and DSR workflow

Included because GDPR Article 17 erasure workflows must reach every AI
surface a tenant's data touched, and DSR tools coordinate the request
without verifying the AI-surface outcome.

- [Securiti](https://securiti.ai/) — a privacy and data-governance platform: DSR (data-subject-request) orchestration, consent management, and data discovery.

## Standards and frameworks

- [OWASP Top 10 for Large Language Model Applications](https://genai.owasp.org/) — the umbrella project; [LLM08:2025 — Vector and Embedding Weaknesses](https://genai.owasp.org/llmrisk/llm082025-vector-and-embedding-weaknesses/) is the canonical multi-tenant reference.
- [NIST AI Risk Management Framework (AI 100-1)](https://www.nist.gov/itl/ai-risk-management-framework) — the GOVERN / MAP / MEASURE / MANAGE functions, including MEASURE 2.7 (security and resilience) and MANAGE 2.x (managing AI risks).
- [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial threat landscape for AI systems: techniques, tactics, and case studies relevant to multi-tenant attack modeling.
- [EU AI Act, Article 15 — Accuracy, robustness and cybersecurity](https://artificialintelligenceact.eu/article/15/) — the high-risk-AI cybersecurity and robustness obligations that multi-tenant isolation testing speaks to.
- [GDPR Article 17 — Right to erasure](https://gdpr-info.eu/art-17-gdpr/) — erasure must cover every surface a tenant's data reached, including AI-derived stores (embeddings, caches, fine-tunes, logs).
- [GDPR Article 32 — Security of processing](https://gdpr-info.eu/art-32-gdpr/) — the security baseline of which tenant isolation is part.
- [ISO/IEC 27001:2022](https://www.iso.org/standard/27001) — information-security management; relevant Annex A controls include A.5.15 (access control), A.8.3 (information access restriction), and A.8.12 (data leakage prevention).
- [AICPA SOC 2 Trust Services Criteria](https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2) — the criteria auditors use (CC6.1, CC6.6, CC6.7) for logical access and boundary protection, which tenant isolation falls under.

## Vector databases with multi-tenancy capabilities

Tenant isolation in vector stores is implementation-specific. The links
below point at each vendor's own multi-tenancy documentation; whether the
default deployment mode is single-tenant-per-namespace or shared-index is
the key thing to verify against your own configuration.

- [Pinecone — Multitenancy](https://docs.pinecone.io/guides/index-data/implement-multitenancy) — per-namespace tenant isolation inside a serverless index.
- [pgvector](https://github.com/pgvector/pgvector) — Postgres vector extension; multi-tenancy follows the surrounding Postgres pattern (per-row tenant ID, per-schema, or row-level security).
- [Weaviate — Multi-tenancy](https://weaviate.io/developers/weaviate/manage-data/multi-tenancy) — first-class tenant objects with per-tenant shards.
- [Chroma](https://github.com/chroma-core/chroma) — supports per-collection or per-tenant partitioning; see the Chroma docs for the current collection / tenant model.
- [Qdrant — Multitenancy](https://qdrant.tech/documentation/guides/multiple-partitions/) — recommended approach is single shared collection with a `group_id` payload index per tenant.
- [Milvus — Multi-tenancy strategies](https://milvus.io/docs/multi_tenancy.md) — database / collection / partition-key strategies depending on tenant count and isolation needs.

## MCP-related security resources

The Model Context Protocol exposes tools and data to LLM agents across
tenant boundaries; tenant-scope handling here is a fast-moving attack
surface.

- [Model Context Protocol — specification](https://modelcontextprotocol.io/) — the canonical spec and reference servers.
- [Model Context Protocol — Security best practices](https://modelcontextprotocol.io/specification/2025-06-18/basic/security_best_practices) — the spec's own security guidance, including tool-call authorization and token-passthrough warnings.
- *Asana MCP cross-tenant flaw post-mortem* (Coalition for Secure AI, May 2025) — see [Research](#research) above. The root cause was a token-passthrough pattern that lost tenant scope inside the MCP server.
- *Surge of MCP-related CVEs (Jan–Feb 2026)* — public CVE trackers show roughly 30 MCP-related CVEs filed across a 60-day window in early 2026, covering tool-call confused-deputy, token passthrough, and prompt-injection-via-tool-output patterns. *No single canonical aggregator; the MITRE / NVD CVE feeds are the source of record — see [CONTRIBUTING.md](CONTRIBUTING.md) if you would like to contribute a curated tracker URL.*

## Compliance mappings

How multi-tenant AI verification evidence maps to specific control numbers
(SOC 2 CC6.x, ISO/IEC 27001 A.5/A.8, GDPR Art. 17 / 25 / 32, EU AI Act
Art. 15, HIPAA §164.312, NIST AI RMF):

- [sectum.ai/docs/compliance-mappings/](https://sectum.ai/docs/compliance-mappings/) — the canonical mapping table maintained alongside the Sectum AI evidence chain.

## Conference talks and podcasts

(none yet)

If you know of a talk or podcast episode on multi-tenant AI security
specifically — not the general "AI security" overview talk — please open a
PR; see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md) for the
PR template, the inclusion criteria, and the rejection criteria. This
project follows the [Contributor Covenant Code of Conduct](code-of-conduct.md).

## License

[CC0-1.0](LICENSE) — to the extent possible under law, the contributors to
this list have waived all copyright and related rights, dedicating the work
to the public domain.
