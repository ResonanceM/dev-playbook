# Decision Framework: The COTR Model

Senior engineers don't just pick technologies—they justify trade-offs in business and architectural terms. Use the **COTR Framework** when presenting decisions, writing Architecture Decision Records (ADRs), or leading design reviews.

---

## 📐 The COTR Blueprint

### 1. Context
*State the current business or technical problem clearly without jumping to solutions.*
> *"As our dashboard user base scales, client-side data fetching across 30+ components is causing duplicate API calls, poor load times, and race conditions."*

### 2. Options
*List 2–3 viable approaches you evaluated (including the status quo).*
* **Option A:** Keep React Context + custom `useEffect` fetchers.
* **Option B:** Introduce a global store like Redux Toolkit.
* **Option C:** Adopt **TanStack Query (React Query)** for server state.

### 3. Trade-offs Matrix
*Evaluate each option honestly across complexity, performance, DX, and long-term maintenance.*

| Metric | Option A (Context) | Option B (Redux Toolkit) | Option C (TanStack Query) |
| :--- | :--- | :--- | :--- |
| **Setup Cost** | Zero | High (Boilerplate) | Low |
| **Cache Management** | Manual / Buggy | Manual in store | Automatic |
| **Bundle Impact** | 0 kB | ~11 kB | ~13 kB |
| **Maintenance** | High tech debt | Moderate | Minimal |

### 4. Recommendation
*State your explicit choice with a clear business & engineering rationale.*
> *"I recommend **Option C (TanStack Query)**. It completely eliminates manual API cache invalidation, reduces network payload by deduplicating requests, and will save estimated 15% frontend dev time on new feature development."*

---

## 🔗 Curated GitHub Repos & ADR Templates
* [joelparkerhenderson/architecture-decision-record](https://github.com/joelparkerhenderson/architecture-decision-record) — Standard ADR templates for git repos.
* [adr/madr](https://github.com/adr/madr) — Markdown Architectural Decision Records.
