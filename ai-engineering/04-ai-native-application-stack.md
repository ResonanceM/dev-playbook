# AI-Native Application Stack & Architecture

## 🏗️ Core Application Patterns
1. **Request-Response (Chat/Completions):** Direct streaming tokens to UI with timeout handling.
2. **Pipelines (Async Document/Data Processing):** Multi-step transformations (ingestion $ightarrow$ chunking $ightarrow$ embedding $ightarrow$ indexing).
3. **Agent Loops (Reasoning & Tools):** Observe $ightarrow$ Plan $ightarrow$ Execute Tool (via MCP/APIs) $ightarrow$ Reflect.

## ⚖️ Cost & Token Management
* **Model Routing:** Use fast/cheap models (e.g., Llama 3 8B / GPT-4o-mini) for classifications and routing, reserving heavy reasoning models (GPT-4o / Claude 3.5 / O1) for complex generation and agent execution.
* **Prompt Caching:** Utilize provider prompt caching (Anthropic/OpenAI) to reduce latency and costs on large system prompts.
