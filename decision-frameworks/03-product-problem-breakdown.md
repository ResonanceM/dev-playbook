# Software Product Problem Decomposition Framework

A structured, 6-stage blueprint for Software Experts, Technical Leads, and Project Managers to deconstruct complex, ambiguous product problems into execution-ready engineering tasks while addressing all technical and operational dimensions.

---

## 🧭 The 6-Stage Problem Breakdown Pipeline

```text
┌───────────────────────────┐
│ Stage 1: Problem & Scope  │ Define core outcome, non-goals, and boundary conditions
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Stage 2: Functional Specs │ Map user journeys, data flow, state changes & edge cases
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Stage 3: Technical NFRs   │ Latency, scalability, security, availability & resilience
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Stage 4: System Architecture│ Rendering, API protocols, state taxonomy & database schemas
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Stage 5: Ops & Telemetry  │ Observability, error boundaries, analytics & rollout flags
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Stage 6: Delivery & Risk  │ Work breakdown (WBS), dependencies, buffers & type 1/2 risks
└───────────────────────────┘
```

---

## 🔍 Detailed Checklist Across Dimensions

### Stage 1: Problem & Scope Definition
- [ ] **Core User Value:** What specific user pain point does this solve?
- [ ] **Business Impact:** How does this move company metrics (ARR, conversion, retention, latency)?
- [ ] **Explicit Non-Goals:** What are we deliberately **NOT** building in this version?
- [ ] **Constraints:** Fixed deadlines, compliance/legal boundaries, budget caps.

### Stage 2: Functional Specs & Edge Cases
- [ ] **Primary User Flow:** Step-by-step user journey from entry to success state.
- [ ] **Edge Cases & Failure Modes:**
  - Network loss / Offline mode behavior.
  - Partial API failures or timeout states.
  - Concurrent user edits / race conditions.
  - Empty states, loading skeletons, and multi-tenant data isolation.

### Stage 3: Non-Functional Requirements (NFRs)
- [ ] **Performance Budget:** Target $p95$ response time, max initial JS payload size.
- [ ] **Scalability:** Peak QPS (queries per second), data growth per month.
- [ ] **Availability & Reliability:** Target SLO (e.g., 99.9% uptime), circuit breaker thresholds.
- [ ] **Security & Compliance:** Auth/AuthZ roles, HttpOnly cookies, CSP headers, GDPR PII scrubbing.

### Stage 4: Architectural Selection (The Senior Stack Choices)
- [ ] **Rendering & UI Strategy:** SPA vs. SSR vs. SSG vs. ISR.
- [ ] **State Taxonomies:** Separate Server State (TanStack Query), Client State (Zustand), and URL State.
- [ ] **API Paradigm:** REST vs. tRPC vs. GraphQL vs. WebSockets.
- [ ] **Data Model:** SQL vs. NoSQL schema, index optimization, vector database requirements (if AI).

### Stage 5: Production Operations & Telemetry
- [ ] **Error Boundaries:** Scope UI boundaries to prevent full-page crashes.
- [ ] **Structured Logging:** Standardized JSON format (`timestamp`, `trace_id`, `level`).
- [ ] **Observability:** OpenTelemetry traces across client-to-server boundaries.
- [ ] **Analytics Taxonomy:** `[Entity] [Action]` event naming conventions (e.g., `checkout_started`).
- [ ] **Feature Flag Strategy:** Dark launch, progressive rollouts (1% -> 10% -> 100%).

### Stage 6: Delivery, WBS & Risk Management
- [ ] **Work Breakdown Structure (WBS):** Slice epic into decoupled, testable pull requests ($< 250	ext{ lines}$).
- [ ] **Dependency Mapping:** Third-party vendor dependencies, backend API Readiness.
- [ ] **Risk Classification:** Identify Type 1 (Irreversible) vs. Type 2 (Reversible) decisions.
- [ ] **Capacity Buffer:** Apply the 20% capacity buffer rule for unknown technical risks.

---

## 🗣️ Communication Template for Alignment Meetings

> **Problem:** *"We need to add real-time collaborative editing to our invoice builder."*  
> **Decomposition Pitch:**  
> 1. **Scope:** *Phase 1 is limited to concurrent field editing; version history is a non-goal.*  
> 2. **Architecture:** *We use WebSockets for real-time deltas and URL State for session joining.*  
> 3. **Resilience:** *If the socket connection drops, fallback gracefully to optimistic polling via REST and preserve local drafts.*  
> 4. **Delivery:** *3-phase rollout behind a PostHog feature flag starting with internal beta users.*
