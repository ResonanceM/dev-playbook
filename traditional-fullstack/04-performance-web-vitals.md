# Web Performance & Core Web Vitals Checklist

---

## 🎯 Key Metrics & Targets (Google Standards)

| Metric | Full Name | Target | Primary Causes & Fixes |
| :--- | :--- | :--- | :--- |
| **LCP** | Largest Contentful Paint | $< 2.5	ext{s}$ | Unoptimized hero images $ightarrow$ Use `next/image`, preload fonts, dynamic imports |
| **INP** | Interaction to Next Paint | $< 200	ext{ms}$ | Heavy JS main thread blocking $ightarrow$ Break tasks into `requestIdleCallback`, web workers |
| **CLS** | Cumulative Layout Shift | $< 0.1$ | Missing image/video dimensions $ightarrow$ Reserve aspect ratio, avoid top-injected banners |

---

## 🛠️ Senior Optimization Checklist
- [ ] **Code Splitting:** Route-level code splitting + heavy library dynamic imports (`import()`).
- [ ] **Tree Shaking:** Verify ES module exports and check `sideEffects: false` in `package.json`.
- [ ] **Font Optimization:** Self-host web fonts with `font-display: swap`.
- [ ] **Image Formats:** Serve WebP/AVIF images with responsive `srcset`.

---

## 🔗 Essential Tools & Repositories
* [Google Web Vitals Library](https://github.com/GoogleChrome/web-vitals) — Tiny library to measure Core Web Vitals in real user monitoring (RUM).
* [Lighthouse CI](https://github.com/GoogleChrome/lighthouse-ci) — Automate Lighthouse audits in GitHub Actions.
* [Bundle Analyzer (Webpack/Vite)](https://github.com/webpack-contrib/webpack-bundle-analyzer) — Visualize output bundle size.
