# AI Agents & Multi-Agent Orchestration

---

## 🛠️ Framework Selection Matrix

| Framework | Primary Language | Best Used For | Architecture Style |
| :--- | :--- | :--- | :--- |
| **LangChain / LangGraph** | Python / TS | Cyclic state machines, complex agent graphs | Graph-based (Nodes & Edges) |
| **LlamaIndex** | Python / TS | Data-centric AI agents, advanced retrieval systems | Document & Index focused |
| **AutoGen (Microsoft)** | Python | Multi-agent conversation simulation | Conversational agents |
| **Model Context Protocol (MCP)** | Any | Standardized LLM tool & data connectivity | Open Protocol standard |

---

## 🤖 Model Context Protocol (MCP) Overview
**MCP** (developed by Anthropic) is an open standard that allows LLMs to connect securely to local or remote resources (databases, GitHub repos, local dev tools) without custom, brittle API integrations for each application.

---

## 🔗 Essential Resources & Repositories
* [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) — Build resilient language agent workflows as graphs.
* [run-llama/llama_index](https://github.com/run-llama/llama_index) — Data framework for LLM applications.
* [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) — Reference MCP servers for tools and integrations.
