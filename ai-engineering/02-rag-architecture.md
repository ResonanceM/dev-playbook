# RAG (Retrieval-Augmented Generation) Architecture

---

## 🏗️ Production RAG Pipeline Architecture

```text
[ Document Ingestion ] ──► [ Chunking (500 tokens) ] ──► [ Embedding Model ]
                                                                 │
                                                                 ▼
[ User Query ] ──► [ Dense/Sparse Vector Search ] ──► [ Vector Database ]
                           │                                     │
                           ▼                                     ▼
                   [ Re-Ranker (Cohere) ] ──► [ Context Window + LLM ]
```

---

## 📊 Vector Database Matrix

| Vector DB | Deployment | Best For | Key Feature |
| :--- | :--- | :--- | :--- |
| **pgvector (PostgreSQL)** | Managed DB / Self-host | Apps already on Postgres | Hybrid relational + vector queries |
| **Pinecone** | Fully Managed SaaS | Low operational overhead, high scale | Serverless index scaling |
| **Qdrant** | Open Source / Cloud | Production Rust-backed speed | Rich payload filtering & hybrid search |
| **Chroma** | In-memory / Local | Fast prototyping & local test suites | Zero-config Python/JS setup |

---

## 🎯 Advanced RAG Best Practices
* **Hybrid Search:** Combine Dense Vector Search (semantic similarity) + Sparse Keyword Search (BM25) for high-precision retrieval.
* **Re-Ranking:** Run top-20 retrieved chunks through a cross-encoder / re-ranker (e.g., Cohere ReRank) to send only the top-5 relevant chunks to the LLM.

---

## 🔗 Essential Resources & Repositories
* [pgvector/pgvector](https://github.com/pgvector/pgvector) — Open-source vector similarity search for Postgres.
* [qdrant/qdrant](https://github.com/qdrant/qdrant) — High-performance vector database written in Rust.
* [Pinecone Docs](https://docs.pinecone.io/) — Official managed vector database guides.
