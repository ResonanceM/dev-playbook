# State Management Architecture

Den gyllene regeln för senior state architecture: **Blanda aldrig ihop serverstate (API-data) med client UI-state (modaler, teman).**

---

## 🧠 Taxonomi och verktygsval

```text
┌────────────────────────────────────────────────────────┐
│                  Frontend Applikation                  │
└───────────┬──────────────────┬─────────────────┬───────┘
            │                  │                 │
            ▼                  ▼                 ▼
     ┌──────────────┐   ┌──────────────┐  ┌─────────────┐
     │ Server State │   │ Client State │  │  URL State  │
     │ TanStack Q.  │   │ Zustand      │  │ URL Params  │
     └──────────────┘   └──────────────┘  └─────────────┘
```

* **Server State:** Hanteras med **TanStack Query** eller **SWR**. Hanterar automatisk cachning, background refetching och deduplicering. Lägg *aldrig* rå API-data i global client store.
* **Client UI State:** Använd **Zustand** eller **Jotai** för rent lokala UI-tillstånd (t.ex. om en sidomeny är öppen eller aktivt mörkt läge). Undvik bred React Context som orsakar onödiga omrenderingar i hela träden.
* **URL State:** Sökparametrar, paginering och flikar ska alltid sparas i **URL Search Params** så att tillståndet blir delbart via länk.
