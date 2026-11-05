# Engineering Management: Technical Debt Framework & Negotiation

---

## 📊 Technical Debt Taxonomy

| Category | Definition | Example | Action Plan |
| :--- | :--- | :--- | :--- |
| **Deliberate / Prudent** | Shortcuts taken for critical business deadlines | Hardcoding API responses for demo | Pay off immediately after launch |
| **Accidental / Legacy** | Code outdated as requirements evolved | Monolithic state object handling 50 routes | Refactor incrementally |
| **Bit Rot** | EOL dependencies or Node runtimes | Node 18 EOL | Reserve dedicated maintenance budget |

---

## 🛠️ The 20% Engineering Allocation Rule
* **70% Feature Velocity:** Direct customer-facing value.
* **20% Architecture & Tech Debt:** Refactoring, performance budgets, test coverage.
* **10% Innovation & Spikes:** R&D and dev tool improvements.
