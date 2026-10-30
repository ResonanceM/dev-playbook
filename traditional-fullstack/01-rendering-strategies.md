# Web Rendering Strategies: SPA vs SSR vs SSG vs ISR

*Quick Reference for Frontend & Full-Stack Architecture Decision Making.*

---

## 📊 Strategy Comparison Matrix

| Strategy | Ideal Use Case | Initial TTFB | Interactive Speed | SEO Impact | Hosting Complexity |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **SPA** (Client-Side) | SaaS Dashboards, Internal Admin Tools | Blazing Fast | Dependent on bundle size | Poor | Minimal (CDN static hosting) |
| **SSR** (Server-Side) | Dynamic E-commerce, Feeds, Personalization | Moderate (Server processing) | High | Excellent | High (Node/Edge Runtime required) |
| **SSG** (Static Site) | Marketing Sites, Blogs, Docs | Blazing Fast | Blazing Fast | Perfect | Minimal (Static CDN) |
| **ISR** (Incremental) | Massive E-commerce Catalogs, News | Fast (Cached static) | High | Excellent | Moderate (Next.js / Vercel style) |

---

## 🎯 Quick Decision Tree
* **Is SEO critical AND content updates frequently per user?** $ightarrow$ **SSR**
* **Is the content public, static, or updated via CMS periodically?** $ightarrow$ **SSG / ISR**
* **Is the app behind authentication with no SEO requirement?** $ightarrow$ **SPA**

---

## 🔗 Essential Resources & Repositories
* [Next.js Documentation on Rendering](https://nextjs.org/docs/app/building-your-application/rendering) — Official Next.js SSR/SSG/ISR guide.
* [vercel/platforms](https://github.com/vercel/platforms) — Multi-tenant SSR/ISR starter kit.
* [web.dev: Rendering on the Web](https://web.dev/rendering-on-the-web/) — Google's official deep dive on web performance metrics across rendering strategies.
