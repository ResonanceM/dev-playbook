# Produktionsklar RAG-arkitektur (Retrieval-Augmented Generation)

En robust RAG-pipeline kräver mer än en enkel vektorbaserad sökning. Följ denna arkitektur för hög precision.

---

## 🏗️ Pipeline-steg

1. **Optimal Chunking:** Dela in dokument i bitar om cirka 500 tokens med en överlappning (overlap) på 50–100 tokens för att inte bryta kontexten mitt i en mening.
2. **Hybrid Search (Vektorer + BM25):** 
   * Kombinera *Dense Vector Search* (semantisk likhet via embeddings) med *Sparse Keyword Search* (BM25 för exakta facktermer, produktkodes och namn).
3. **Re-Ranking (Cross-Encoder):**
   * Skicka de 20 bästa träffarna från din sökning genom en kraftfull cross-encoder (t.ex. *Cohere ReRank* eller BGE-Reranker) för att vaska fram de 5 absolut mest relevanta träffarna som skickas vidare till LLM:ens kontextfönster.
