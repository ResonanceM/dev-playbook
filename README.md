# Senior Software Engineering Playbook

A practical, opinionated-but-contextual handbook for engineers designing, building, shipping, and operating reliable software. It is intended for senior engineers, staff/principal engineers, tech leads, engineering managers, and product-minded developers.

This is a decision aid, not a collection of universal rules. Treat numeric targets as starting hypotheses; validate them against user needs, workload, risk, team capability, and cost.

## How to use it

1. **Start with the problem.** Define user outcome, constraints, non-goals, and measurable success before choosing technology.
2. **Choose the smallest sufficient design.** Prefer boring, reversible decisions until evidence justifies complexity.
3. **Make quality explicit.** Define functional behavior, NFRs, security/privacy requirements, and operational ownership.
4. **Ship in slices.** Keep changes reviewable, independently testable, observable, and reversible.
5. **Operate what you build.** Set service objectives, dashboards, alerts, runbooks, and incident ownership before launch.
6. **Learn from production.** Use customer feedback, telemetry, incidents, and delivery data to improve the system.

## Repository map

| Area | What it helps you decide |
|---|---|
| `decision-frameworks/` | Problem framing, architecture choices, RFCs, ADRs, and decomposition |
| `web-dev/` | Frontend architecture, APIs, security, performance, testing, data, and operations |
| `ai-engineering/` | LLM applications, RAG, agents, evaluation, safety, and economics |
| `product-management-pm/` | Prioritization, product requirements, SLOs, and AI product strategy |
| `engineering-management-em/` | Technical debt, capacity, DevEx, delivery, and team operating systems |
| `platform-devops/` | CI/CD, infrastructure, cloud architecture, and release engineering |
| `quality-reliability/` | Testing strategy, incident response, and operational readiness |
| `templates/` | Copy-ready engineering artifacts |

## Suggested reading paths

### Shipping a new product capability
`decision-frameworks/03-product-problem-breakdown.md` → `product-management-pm/01-feature-prioritization-matrix.md` → relevant `web-dev/` architecture guides → `quality-reliability/01-testing-strategy.md` → `quality-reliability/02-production-readiness-and-incidents.md`.

### Reviewing a system design
`decision-frameworks/01-cotr-framework.md` → `decision-frameworks/02-pragmatic-rfcs-adrs.md` → `web-dev/10-system-design-fundamentals.md` → database/API/security/observability guides.

### Building an AI feature
`ai-engineering/01-llm-apis-prompt-engineering.md` → `02-rag-architecture.md` or `03-ai-agents-orchestration.md` → `05-evaluation-and-safety.md` → `06-ai-economics-and-operations.md`.

### Improving a team or service
`engineering-management-em/01-technical-debt-framework.md` → `03-team-ops-developer-experience.md` → `platform-devops/` → `quality-reliability/`.

## Engineering principles

- Optimize for **customer outcomes and total cost of ownership**, not novelty.
- Prefer explicit contracts, simple boundaries, and well-understood failure modes.
- Design for failure at system boundaries; avoid speculative resilience inside every function.
- Security, accessibility, privacy, and operability are product requirements.
- Measure user-perceived performance, not only server benchmarks.
- Automate repeatable work, but keep automation observable and recoverable.
- Make ownership clear: every production service needs an accountable team.
- Avoid false precision: estimates, scores, and targets are decision inputs, not facts.
- Document decisions when they are consequential; do not document every implementation detail.
- Revisit assumptions when evidence changes.

## A lightweight definition of done

A change is not done merely because it compiles. Before release, verify that it:
- Solves the agreed user problem and meets acceptance criteria.
- Has appropriate tests at the right levels.
- Handles validation, authorization, errors, retries, and concurrency safely.
- Meets accessibility, performance, and privacy expectations.
- Emits useful logs, metrics, traces, and product events without leaking secrets.
- Has migration, rollout, rollback, and support plans where applicable.
- Is documented enough for the next engineer to operate and change it.

## Important caveat

This playbook intentionally avoids claiming that one framework, cloud, database, or process is best for every organization. Benchmark in your own environment, check current vendor documentation, and involve security/legal specialists for regulated or high-risk systems.
