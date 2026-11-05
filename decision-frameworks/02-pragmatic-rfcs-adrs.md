# Pragmatic Engineering: RFCs, ADRs & Staff-Level Alignment
*Inspired by Gergely Orosz (The Pragmatic Engineer)*

---

## 💡 Key Principles of Pragmatic Architecture

1. **Ship Value, Not Tech Stack:** Technology choices exist to serve business outcomes and developer velocity, not engineering vanity.
2. **Reversible vs. Irreversible Decisions (Type 1 vs. Type 2):**
   * **Type 1 (Irreversible):** DB schema choice, API protocol for public consumers, multi-tenant auth model. *Requires formal RFC & deep stakeholder review.*
   * **Type 2 (Reversible):** UI state library, component styling, utility library. *Make quickly with local team consensus.*
