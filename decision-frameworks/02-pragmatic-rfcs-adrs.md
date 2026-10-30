# Pragmatic Engineering: RFCs, ADRs & Staff-Level Alignment
*Inspired by Gergely Orosz (The Pragmatic Engineer)*

---

## 💡 Key Principles of Pragmatic Architecture

1. **Ship Value, Not Tech Stack:** Technology choices exist to serve business outcomes and developer velocity, not engineering vanity.
2. **Reversible vs. Irreversible Decisions (Type 1 vs. Type 2):**
   * **Type 1 (Irreversible):** DB schema choice, API protocol for public consumers, multi-tenant auth model. *Requires formal RFC & deep stakeholder review.*
   * **Type 2 (Reversible):** UI state library, component styling, utility library. *Make quickly with local team consensus.*

---

## 📄 Pragmatic RFC Structure

```markdown
# RFC: [Feature / Architectural Initiative]
**Author:** [Your Name] | **Date:** [YYYY-MM-DD] | **Status:** Draft / Review / Approved

## 1. Executive Summary & Business Impact
Briefly explain what problem this solves and how it affects user experience or engineering efficiency.

## 2. Non-Goals
Explicitly list what this proposal is NOT trying to solve to prevent scope creep.

## 3. High-Level Design & System Diagram
Data flow, component boundaries, and integrations.

## 4. Cost & Maintenance Implications
Hosting costs, vendor lock-in risk, onboarding complexity for new hires.
```

---

## 🔗 Essential Resources
* [The Pragmatic Engineer Blog](https://blog.pragmaticengineer.com/) — Gergely Orosz's insights on software engineering leadership.
* [joelparkerhenderson/architecture-decision-record](https://github.com/joelparkerhenderson/architecture-decision-record) — Standard ADR templates.
