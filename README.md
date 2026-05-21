# Awesome Multi-Tenant AI Security [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of resources on multi-tenant AI security and cross-tenant data
leakage across the LLM surface.

Multi-tenant AI systems — shared vector stores, RAG pipelines, caches, agents,
and model endpoints — must keep one tenant's (or one user's) data from reaching
another. This list collects research, standards, advisories, and tools for
understanding, detecting, and preventing cross-tenant leakage.

## Contents

- [Standards & frameworks](#standards--frameworks)
- [Research](#research)
- [Surfaces](#surfaces)
- [Tools](#tools)
- [Contributing](#contributing)

## Standards & frameworks

- [OWASP LLM08:2025 — Vector and Embedding Weaknesses](https://genai.owasp.org/llmrisk/llm082025-vector-and-embedding-weaknesses/) — names multi-tenant context leakage a top-10 LLM risk.
- [OWASP Top 10 for LLM Applications](https://genai.owasp.org/) — the broader generative-AI risk catalog.
- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) — measure/manage functions applicable to multi-tenant isolation risk.
- [MITRE ATLAS](https://atlas.mitre.org/) — the adversarial threat landscape for AI systems.
- [Model Context Protocol specification](https://modelcontextprotocol.io/) — the protocol behind agent tool calls; tenant-scope handling here is a cross-tenant surface (confused-deputy, token passthrough).
- [EU AI Act, Article 15](https://artificialintelligenceact.eu/article/15/) — accuracy, robustness, and cybersecurity obligations that tenant-isolation robustness speaks to.
- [GDPR Article 17 — Right to erasure](https://gdpr-info.eu/art-17-gdpr/) — erasure must cover every AI surface a tenant's data reached.
- [GDPR Article 32 — Security of processing](https://gdpr-info.eu/art-32-gdpr/) — the security baseline that cross-tenant isolation is part of.
- [ISO/IEC 27001:2022](https://www.iso.org/standard/27001) — information-security management; A.8.12 (data leakage prevention) and access-restriction controls map to tenant isolation.
- [AICPA SOC 2](https://www.aicpa-cima.com/topic/audit-assurance/audit-and-assurance-greater-than-soc-2) — the Trust Services Criteria (logical access, boundary protection) auditors use to assess tenant separation.

## Research

- [Silent Leaks: Implicit Knowledge Extraction Attack on RAG Systems through Benign Queries](https://arxiv.org/abs/2505.15420) — high-efficiency extraction of foreign knowledge through a sequence of benign queries, with no prompt injection.
- [Text Embeddings Reveal (Almost) As Much As Text](https://arxiv.org/abs/2310.06816) — embedding inversion reconstructs source text from vectors, so cross-tenant access to embeddings is a leakage path.
- [Information Leakage in Embedding Models](https://arxiv.org/abs/2004.00053) — what embeddings disclose about their inputs; foundational for embedding-inversion risk in shared vector stores.

> Retrieval-pivot attacks — benign cross-tenant leakage in hybrid RAG via shared
> organic entities (shared names, vendors, compliance terms, amounts, dates) —
> are a central motivation for this topic. Contributions linking the canonical
> writeups are welcome.

## Surfaces

Cross-tenant leakage can occur across the whole AI surface: vector databases,
RAG pipelines, prompt/completion logs and tracing, semantic and KV caches,
agent memory, MCP tool calls, fine-tunes and adapters, eval sets, backups, and
search indexes.

- [Cresta — Observability for AI agents with Langfuse](https://cresta.com/blog/observability-for-ai-agents-tracing-multi-service-llm-pipelines-with-langfuse) — a real-world per-customer multi-tenant tracing setup.

## Tools

Multi-tenant-specific:

- [Sectum AI](https://github.com/sectum-ai/sectum-ai) — multi-tenant AI verification: a synthetic-tenant marker substrate, a catalog of cross-tenant leakage probes, and a tamper-evident evidence chain (Apache-2.0).
- [DeepTeam — CrossContextRetrieval](https://www.trydeepteam.com/docs/red-teaming-vulnerabilities-cross-context-retrieval) — an LLM red-teaming vulnerability check for cross-context (tenant/user) retrieval.

General LLM security tooling (applicable to isolation testing):

- [garak](https://github.com/NVIDIA/garak) — an LLM vulnerability scanner with probes for leakage and data exposure.
- [PyRIT](https://github.com/Azure/PyRIT) — Microsoft's Python Risk Identification Tool for generative-AI red teaming.
- [Giskard](https://github.com/Giskard-AI/giskard) — testing and scanning for LLM and ML systems.
- [promptfoo](https://github.com/promptfoo/promptfoo) — LLM evaluation and red-teaming with configurable security checks.

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). Keep entries
on-topic (multi-tenant / cross-tenant AI security), factual, and with a working
link.
