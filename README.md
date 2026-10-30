# Web Dev & AI Engineering Playbook

A structured decision matrix, reference architecture, and actionable playbook for Devs.

---

## 📁 Playbook Structure

```text
senior-dev-playbook/
├── README.md                          # Quick start & index
├── decision-frameworks/
│   └── cotr-framework.md             # How to pitch technical decisions (COTR)
├── web-dev/
│   ├── 01-rendering-strategies.md     # SPA vs SSR vs SSG vs ISR
│   ├── 02-state-management.md         # Server State vs Client State vs URL
│   ├── 03-api-architectures.md        # REST vs tRPC vs GraphQL vs WebSockets
│   ├── 04-performance-web-vitals.md   # INP, LCP, CLS, Bundle Optimization
│   └── 05-auth-security.md            # OAuth 2.0, JWT vs Cookies, CORS, OWASP
└── ai-engineering/
    ├── 01-llm-apis-prompt-engineering.md # Structured Outputs, Tool Calling, Evals
    ├── 02-rag-architecture.md         # Chunking, Embeddings, Vector DBs, Hybrid Search
    └── 03-ai-agents-orchestration.md   # LangChain vs LlamaIndex vs AutoGen, MCP
```

---

## 🎯 How to Use This Playbook
1. **In Architectural Review Meetings:** Open the corresponding markdown file and refer directly to the **Trade-Off Matrix**.
2. **When Writing RFCs / ADRs:** Copy the **COTR (Context, Options, Trade-offs, Recommendation)** structure from `decision-frameworks/cotr-framework.md`.
3. **During Technical Pitching:** Use pre-formulated senior-level justifications to communicate with product managers and C-level executives.
