# Web Dev & AI Engineering Playbook

A structured decision matrix, reference architecture, and actionable playbook for Devs.

---

## 📁 Playbook Structure

senior-dev-playbook/
├── README.md                          # Quick start & master index
├── decision-frameworks/
│   ├── 01-cotr-framework.md          # Pitching architectural decisions (COTR)
│   ├── 02-pragmatic-rfcs-adrs.md     # Gergely Orosz (Pragmatic Engineer) RFCs & alignment
│   └── 03-product-problem-breakdown.md # 🆕 6-STAGE PRODUCT DECOMPOSITION FRAMEWORK
├── engineering-management-em/        # EM LEADERSHIP FRAMEWORKS
│   ├── 01-technical-debt-framework.md # 20% Allocation Rule & Tech Debt Negotiation
│   ├── 02-delivery-capacity-planning.md# Capacity Planning & 80% Buffer Rule
│   └── 03-team-ops-developer-experience.md # DORA Metrics & DevEx
├── product-management-pm/            # PM LEADERSHIP FRAMEWORKS
│   ├── 01-feature-prioritization-matrix.md # RICE Score & MoSCoW Frameworks
│   ├── 02-technical-prerequisites-slas.md  # SLIs/SLOs/SLAs & p95 Latency Budgets
│   └── 03-ai-product-playbook.md          # LLM Economics & AI Product Evals
├── web-dev/            # TECHNICAL FULL-STACK REFERENCE
│   ├── 01-rendering-strategies.md     # SPA vs SSR vs SSG vs ISR
│   ├── 02-state-management.md         # Server State vs Client UI vs URL state
│   ├── 03-api-architectures.md        # REST vs tRPC vs GraphQL vs WebSockets
│   ├── 04-addy-osmani-performance.md  # Addy Osmani Loading Patterns & Islands Arch
│   ├── 05-matt-pocock-typescript.md   # Matt Pocock Advanced TypeScript Patterns
│   ├── 06-auth-security.md            # Session Security & OWASP Top 10
│   ├── 07-error-handling-resilience.md # Error Boundaries, Retries & Circuit Breakers
│   ├── 08-observability-logging.md     # Structured Logging, OpenTelemetry & Tracing
│   └── 09-analytics-telemetry.md      # Event Schema Taxonomy & GDPR Privacy
└── ai-engineering/                   # AI & LLM SYSTEMS REFERENCE
    ├── 01-llm-apis-prompt-engineering.md # Model Selection & Structured JSON Schemas
    ├── 02-rag-architecture.md         # RAG Pipelines & Vector DB Matrices
    └── 03-ai-agents-orchestration.md   # LangGraph, LlamaIndex & MCP Protocol

---

## 🎯 How to Use This Playbook
1. **In Architectural Review Meetings:** Open the corresponding markdown file and refer directly to the **Trade-Off Matrix**.
2. **When Writing RFCs / ADRs:** Copy the **COTR (Context, Options, Trade-offs, Recommendation)** structure from `decision-frameworks/cotr-framework.md`.
3. **During Technical Pitching:** Use pre-formulated senior-level justifications to communicate with product managers and C-level executives.
