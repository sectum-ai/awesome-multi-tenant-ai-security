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

## Research

- [Silent Leaks (IKEA)](https://arxiv.org/abs/2505.15420) — high-efficiency extraction of foreign knowledge through a sequence of benign queries, with no prompt injection.

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

- [DeepTeam — CrossContextRetrieval](https://www.trydeepteam.com/docs/red-teaming-vulnerabilities-cross-context-retrieval) — an LLM red-teaming vulnerability check for cross-context (tenant/user) retrieval.
- [Sectum AI](https://github.com/sectum-ai/sectum-ai) — multi-tenant AI verification: a synthetic-tenant marker substrate, a catalog of cross-tenant leakage probes, and a tamper-evident evidence chain (Apache-2.0).

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). Keep entries
on-topic (multi-tenant / cross-tenant AI security), factual, and with a working
link.
