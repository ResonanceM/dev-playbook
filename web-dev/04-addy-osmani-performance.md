# Frontend Performance & Loading Patterns
*Inspired by Addy Osmani (Google Chrome Engineering Lead)*

---

## ⚡ Loading & Architecture Patterns

### 1. Islands Architecture (Astro / Fresh)
* Render static HTML on the server and only hydrate small, interactive "islands" of JavaScript on the client.
* **Impact:** Eliminates massive JS bundle payloads on content-heavy web pages.

### 2. Import On Interaction / Import On Visibility
* Defer loading JavaScript for non-critical UI elements (modals, chat widgets, heavy charts) until the user scrolls them into view or clicks them.

```typescript
// React Lazy + Intersection Observer pattern
const HeavyChart = React.lazy(() => import('./HeavyChart'));
```

---

## 🎯 Core Web Vitals Targets

| Metric | Target | Focus Area |
| :--- | :--- | :--- |
| **LCP** (Largest Contentful Paint) | $< 2.5	ext{s}$ | Preload critical hero assets, optimize web fonts |
| **INP** (Interaction to Next Paint) | $< 200	ext{ms}$ | Break up long main-thread tasks (`requestIdleCallback`) |
| **CLS** (Cumulative Layout Shift) | $< 0.1$ | Reserve aspect-ratio boxes for async images & ads |

---

## 🔗 Essential Resources
* [Addy Osmani: Software Engineering Guides](https://addyosmani.com/) — Web performance & engineering leadership.
* [web.dev Patterns](https://web.dev/patterns/) — Modern web loading and rendering design patterns.
