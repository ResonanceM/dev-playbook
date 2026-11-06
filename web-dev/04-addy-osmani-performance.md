# Frontend Performance & Laddmönster (Inspirerat av Addy Osmani)

---

## ⚡ Moderna prestandamönster

### 1. Islands Architecture (Astro / Fresh)
* Rendera statisk HTML på servern och hydrera enbart små, isolerade öar av interaktiv JavaScript på klienten. Eliminerar gigantiska JS-bundle-filer.

### 2. Import on Interaction / Visibility
* Skjut upp laddning av tunga komponenter (t.ex. grafer, chattwidgetar, modaler) tills användaren faktiskt scrollar dem i synfältet eller klickar på knappen.

```typescript
// Exempel med React.lazy och Intersection Observer
const HeavyAnalyticsChart = React.lazy(() => import('./HeavyAnalyticsChart'));
```

---

## 🎯 Core Web Vitals Mål
* **LCP (Largest Contentful Paint):** $< 2.5	ext{s}$
* **INP (Interaction to Next Paint):** $< 200	ext{ms}$
* **CLS (Cumulative Layout Shift):** $< 0.1$
