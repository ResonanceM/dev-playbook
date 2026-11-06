# Retrieval-Augmented Generation (RAG) Architecture

RAG grounds generation in external knowledge. It improves access to current or private information but does not guarantee factual correctness.

## Pipeline

1. **Ingest:** identify authorized sources, formats, owners, and update cadence.
2. **Parse:** extract text and structure; preserve headings, tables, metadata, and source locations.
3. **Normalize:** remove boilerplate carefully; retain meaningful context.
4. **Chunk:** split by semantic structure and token budget, not arbitrary character count alone.
5. **Enrich:** attach tenant, ACL, source, timestamp, version, and content-type metadata.
6. **Embed/index:** generate embeddings and store vectors plus lexical/searchable fields.
7. **Retrieve:** apply authorization filters, lexical search, vector search, and hybrid fusion.
8. **Rerank:** use a reranker when evaluation shows improved relevance.
9. **Generate:** provide selected evidence with clear instructions and citation metadata.
10. **Evaluate/monitor:** measure retrieval quality, answer quality, latency, freshness, and cost.

## Chunking

Chunk size and overlap depend on document structure and question type. Small chunks improve precision but may lose context; large chunks preserve context but can add noise. Prefer structure-aware splitting and test alternatives on real queries.

## Retrieval choices

| Technique | Benefit | Limitation |
|---|---|---|
| Keyword/BM25 | Exact terms, IDs, names | Vocabulary mismatch |
| Dense vectors | Semantic similarity | Weak on exact identifiers and some domain terms |
| Hybrid | Combines lexical and semantic | More tuning and infrastructure |
| Reranking | Improves ordering of candidates | Additional latency/cost |

## Security and multi-tenancy

Authorization filtering must happen before retrieved content reaches the model. Do not rely on the model to ignore unauthorized chunks. Prevent cross-tenant leakage in indexes, caches, logs, and citations. Re-check access when permissions change and define deletion propagation.

## Grounding and citations

Carry source IDs, URLs, versions, and offsets through the pipeline. Require claims to be supported by retrieved evidence where the task needs citations. Say when evidence is missing or conflicting. Do not fabricate references.

## Evaluation

Build a representative dataset of questions and expected relevant sources. Measure recall@k, precision@k, MRR/nDCG where appropriate, answer correctness, groundedness, citation accuracy, refusal behavior, and latency/cost. Review failures by query category.

## Common failure modes

- Poor parsing of tables, PDFs, or code.
- Chunks detached from their title or context.
- Stale indexes after source updates.
- Retrieval without permission filters.
- Too many low-quality chunks in context.
- Evaluating only fluent answers rather than evidence quality.

## Checklist

- [ ] Source authority, freshness, and access rights are known.
- [ ] Parsing and chunking preserve useful structure.
- [ ] Metadata supports filtering and citations.
- [ ] Hybrid retrieval/reranking are evaluated, not assumed.
- [ ] ACLs apply before model context construction.
- [ ] Deletion and re-indexing are operationalized.
- [ ] Evaluation includes retrieval and generation quality.
