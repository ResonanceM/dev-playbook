# State Management Architecture

The Golden Rule of Senior State Architecture: **Never put Server State inside Client State.**

---

## 🧠 Architectural Taxonomy

```text
               ┌─────────────────────────────────────────┐
               │          Frontend Application           │
               └────────────────────┬────────────────────┘
                                    │
          ┌─────────────────────────┼─────────────────────────┐
          ▼                         ▼                         ▼
  ┌───────────────┐         ┌───────────────┐         ┌───────────────┐
  │ Server State  │         │ Client State  │         │   URL State   │
  │ (APIs, Cache) │         │ (Modals, Theme)│        │(Search, Tabs) │
  └───────┬───────┘         └───────┬───────┘         └───────┬───────┘
          │                         │                         │
  TanStack Query / SWR      Zustand / Jotai           URLSearchParams
```

---

## ⚖️ Trade-off & Choice Table

| State Category | Recommended Tool | Why Senior Devs Choose It | Avoid |
| :--- | :--- | :--- | :--- |
| **Server Data** | **TanStack Query** / **SWR** | Handles retries, stale-while-revalidate, optimistic updates, and automatic caching | Redux / Context for API responses |
| **Client UI State** | **Zustand** / **Jotai** | Atomic, zero-boilerplate, lightweight (~1.5kB), no unnecessary re-renders | Raw React Context for broad state |
| **URL / Filter State** | **URL Search Params** | Bookmarkable, shareable links, back/forward browser support out-of-the-box | Internal `useState` for search filters |

---

## 🔗 Essential Resources & Repositories
* [TanStack Query GitHub](https://github.com/TanStack/query) — Powerful asynchronous state management.
* [pmndrs/zustand](https://github.com/pmndrs/zustand) — Bear essential, unopinionated state management in React.
* [pmndrs/jotai](https://github.com/pmndrs/jotai) — Primitive and flexible state management for React based on atomic model.
