# AI-Nativ Applikationsstack & Arkitekturmönster

Hur du bygger skalbara AI-nativa applikationer i produktion.

---

## 🏗️ De tre primära applikationsmönstren

1. **Request-Response & Streaming:** 
   * Direkta LLM-anrop med Server-Sent Events (SSE) för att streama tokens till klienten i realtid med robusta timeouts.
2. **Asynkrona Pipelines:**
   * Stegvisa transformationer av tunga dokument (Inmatning $ightarrow$ Chunking $ightarrow$ Embedding $ightarrow$ Indexering i vektordatabas) som körs i bakgrundsköer (t.ex. BullMQ / Celery).
3. **Agent Loops (Resonemang & Verktyg):**
   * Interaktionscykel där modellen observerar, planerar, anropar verktyg (via API/MCP) och reflekterar över resultatet.

---

## 💰 Tokenoptimering & Modellrutning
* **Prompt Caching:** Utnyttja plattformarnas inbyggda cache-stöd för stora statiska systemprompter för att minska latens och kostnader med upp till 90%.
* **Model Routing:** Skicka enkla uppgifter till snabba/billiga modeller och eskalera endast till tunga modeller vid behov.
