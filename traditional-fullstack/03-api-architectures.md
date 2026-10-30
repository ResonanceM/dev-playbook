# API Architecture Matrix: REST vs tRPC vs GraphQL vs WebSockets

---

## 📊 Comparison Matrix

| Protocol | Best For | Type Safety | Network Efficiency | Learning Curve |
| :--- | :--- | :--- | :--- | :--- |
| **tRPC** | Monorepo / Full-stack TypeScript (Next.js/Node) | 100% End-to-End | High | Low |
| **REST** | Public APIs, Multi-platform clients (iOS + Web) | OpenAPI / Swagger | Moderate | Low |
| **GraphQL** | Deeply nested relational data, multi-client frontend demands | Schema-driven | High (No over-fetching) | High |
| **WebSockets** | Real-time chats, live dashboards, collaborative tools | Manual / Protocol-based | Low latency streaming | Moderate |

---

## 🗣️ Senior Decision Pitch
> *"For our full-stack TypeScript application, adopting **tRPC** eliminates the need for build-step API schema generators or manual fetch wrappers. If a backend route or payload changes, the frontend build immediately fails with TypeScript errors, preventing runtime bugs in production."*

---

## 🔗 Essential Resources & Repositories
* [trpc/trpc](https://github.com/trpc/trpc) — End-to-end typesafe APIs made easy.
* [graphql/graphql-spec](https://github.com/graphql/graphql-spec) — Official GraphQL specification.
* [socketio/socket.io](https://github.com/socketio/socket.io) — Real-time bidirectional event-based communication.
