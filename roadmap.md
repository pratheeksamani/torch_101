# AI Solutions Analyst Roadmap (6 months, ~8-10 hrs/week)

The goal is not to become a model builder. It is to be the person who can take an AI use case from idea to a reliable production system: defining it, checking data readiness, specifying quality thresholds, testing it, and keeping it healthy after launch. Each phase below ends with a concrete artifact for your portfolio.

---

## Phase 0: Baseline (Weeks 1-2)

- Write down 2-3 past projects as "problem, data, design, outcome" stories. These become your interview material.
- Set up your environment: Python, VS Code or Jupyter, Git, and a GitHub account.
- Pick one cloud (Azure, AWS, or GCP), ideally the one your target employers or current company use.

---

## Phase 1: Technical Foundations (Months 1-2)

### Python for data
- pandas: joins, groupby, reshaping, data profiling (nulls, duplicates, distributions)
- Rebuild one of your real extract or ETL specs as a small script. You already know the logic, so you only need to learn the syntax.
- Reading and writing CSV, JSON, Parquet, and calling REST APIs

### SQL (moderate to strong)
- Window functions, CTEs, deduplication patterns, incremental load queries
- Query performance basics: reading execution plans, indexing, partitioning

### LLM fundamentals
- Tokens, context windows, temperature, and why outputs vary
- Prompt design: system prompts, few-shot examples, structured output (JSON schemas)
- Function/tool calling, and when an LLM is the wrong tool and plain rules or SQL would be better

**Artifact:** a small script that profiles a messy dataset and uses an LLM to classify or extract fields into structured JSON.

---

## Phase 2: RAG End to End (Months 2-3)

This is where your data background becomes an advantage. Most RAG failures are data problems, not model problems.

- **Ingestion and parsing:** PDFs, Word, tables, and why messy parsing ruins retrieval
- **Chunking strategies:** size, overlap, structure-aware chunking, and the trade-offs
- **Embeddings and vector stores:** how similarity search works, plus one tool such as pgvector, Chroma, or a managed service
- **Retrieval quality:** hybrid search (keyword plus vector), reranking, metadata filtering
- **Production data concerns** (the part many tutorials skip):
  - Incremental vs full re-indexing when documents change (this maps directly to your full vs incremental experience)
  - Handling deletions, versioning, and stale content
  - Access control: users must only retrieve documents they are allowed to see
  - Source citations so answers can be verified

**Artifact:** a working RAG app with an ingestion pipeline, not just a notebook.

---

## Phase 3: Evaluation and Quality (Months 3-4)

This is the most valuable skill for an AI analyst and the one fewest candidates have.

- **Build a golden dataset:** 50-100 real questions with expected answers and source references. Writing these is a BA skill.
- **Retrieval metrics:** recall@k, precision@k, MRR
- **Answer metrics:** groundedness (is it supported by the sources?), relevance, completeness, refusal behavior when the answer isn't in the data
- **LLM-as-judge:** how it works, where it fails, and why it needs human calibration
- **Regression testing:** rerun the evaluation set whenever you change the prompt, chunking, or model
- **Defining acceptance criteria for non-deterministic systems**, for example "at least 90% of answers grounded in sources, 0 answers leaking restricted content"
- Tools to explore: Ragas, promptfoo, LangSmith, or a custom evaluation script

**Artifact:** an evaluation report for your RAG app with metrics, failure analysis, and the improvements you made.

---

## Phase 4: Production Readiness (Months 4-5)

- **Guardrails and safety:** prompt injection, hallucination handling, PII detection and masking, content filtering, "I don't know" behavior
- **Security and compliance:** data residency, what data can be sent to which model, retention, audit logging
- **Observability:** logging prompts and responses, tracing, tracking latency, cost per query, user feedback (thumbs up/down), and drift over time
- **Cost and performance:** model selection (large vs small models), caching, token budgets, latency targets
- **Human-in-the-loop:** where review is mandatory, escalation paths, feedback loops
- **Lifecycle:** versioning prompts and configs, environment promotion (dev, test, prod), rollback plans
- **Intro to agents and workflows:** multi-step tool use, and why bounded, deterministic workflows are often safer than fully autonomous agents
- **Cloud AI services:** one platform's LLM service and AI search offering, plus a fundamentals-level certification if you want a credential

**Artifact:** add guardrails, logging, and a simple monitoring view to your capstone, plus a short runbook.

---

## Phase 5: Analyst Deliverables and Governance (Months 5-6)

Package your BA craft for AI projects:

- **AI use case canvas:** problem, users, value, data, risks, and why AI is justified
- **Data readiness assessment:** quality, coverage, freshness, ownership, sensitivity
- **AI-specific BRD template:** functional requirements plus quality thresholds, fallback behavior, and out-of-scope examples
- **Evaluation and UAT plan:** how business users test AI output and who signs off
- **Risk register:** hallucination, bias, privacy, vendor dependency, user over-trust
- **Operating model:** who monitors, who retrains or re-tunes, how incidents are handled
- **Responsible AI basics:** NIST AI RMF, the EU AI Act risk categories, and ISO 42001 at awareness level
- **Change management:** training, adoption metrics, and communicating limitations to users

**Artifact:** a complete AI project document pack for your capstone, as if handing it to a delivery team.

---

## Capstone Project

Build a **RAG assistant over data documentation**, such as synthetic BRDs, mapping specs, data dictionaries, and vendor file specifications, so users can ask things like "which fields feed the vendor extract, and what are the filter rules?"

It suits you because you know the domain, the questions are realistic, and you can judge answer quality better than most people. Use synthetic or public documents only, never your employer's confidential material.

Publish on GitHub with:

1. A README covering the problem, architecture, and results
2. The document pack from Phase 5
3. The evaluation report from Phase 3
4. A short demo video

---

## Milestones and Job Search

| When | Milestone |
|---|---|
| End of Month 2 | Python and SQL projects on GitHub |
| End of Month 3 | Working RAG app |
| End of Month 4 | Evaluation report published |
| End of Month 5 | Guardrails, monitoring, and runbook added |
| Month 5 onward | Start applying, rewrite your resume, and update LinkedIn |
| Month 6 | Interview prep, plus try to apply AI to a real task at your current job |

Also try to get exposure inside your current company. Even a small internal pilot, such as summarizing requirement documents or generating first-draft mapping specs, gives you real production experience for your resume.

---

## Interview Preparation

Be ready to explain, with examples:

- How you would decide whether a problem needs AI at all
- How you would define "good enough" for a chatbot
- What can go wrong in production and how you would detect it
- How you handled data quality, edge cases, and requirement ambiguity in past projects, framed for AI
- A walkthrough of your capstone, including what failed and how you fixed it

---

## Habits That Make This Stick

- Build in public: short posts on what you learned, especially evaluation lessons
- Read real postmortems and case studies of AI failures
- Follow one or two practitioner sources rather than chasing every new tool. Tools change quickly, but the concepts above are stable.

---

## Progress Checklist

- [ ] Phase 0: Project stories written, environment set up, cloud chosen
- [ ] Phase 1: Python and SQL projects on GitHub, LLM extraction script done
- [ ] Phase 2: RAG app with ingestion pipeline working
- [ ] Phase 3: Golden dataset built, evaluation report published
- [ ] Phase 4: Guardrails, logging, monitoring view, and runbook added
- [ ] Phase 5: AI project document pack completed
- [ ] Capstone published on GitHub with demo video
- [ ] Resume and LinkedIn rewritten for AI Solutions Analyst roles
- [ ] Interview stories and capstone walkthrough rehearsed

*Assumes about 8-10 hours per week. Adjust pacing up or down to fit your time.*
