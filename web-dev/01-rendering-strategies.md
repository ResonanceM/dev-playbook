# Web Rendering Strategies: CSR, SSR, SSG, ISR, and Streaming

Rendering strategy determines where and when HTML is produced. Choose based on user experience, data freshness, personalization, infrastructure, and caching—not fashion.

## Strategy comparison

| Strategy | HTML generated | Strengths | Costs / risks | Good fit |
|---|---|---|---|---|
| CSR / SPA | Browser | Rich interactions; simple static hosting | JS startup, SEO/discovery, client data waterfalls | Authenticated app with app-like workflows |
| SSR | Per request on server | Fresh personalized HTML; faster meaningful content in some cases | Server cost, caching complexity, hydration | Dynamic public pages and personalized views |
| SSG | Build time | Fast CDN delivery; low runtime cost | Build time and stale content | Docs, marketing, stable catalogs |
| ISR / revalidation | Build plus periodic/on-demand refresh | Static-like delivery with controlled freshness | Invalidation complexity; stale windows | Large content sites |
| Streaming SSR | Incremental server response | Early shell and progressive content | More complex loading/error boundaries | Pages with independent slow data regions |

## Decision factors

- **Discoverability:** Does content need to be indexed or previewed by crawlers and social platforms?
- **Personalization:** Is output user-specific or permission-sensitive?
- **Freshness:** How stale can content be? Define an explicit freshness budget.
- **Interaction:** How much client-side state and interactivity is required?
- **Latency:** Where are users, compute, and data located?
- **Cost:** What is the request volume and server rendering cost?
- **Reliability:** What happens if a data source is slow or unavailable?

## Hydration and server components

Hydration attaches client behavior to server-rendered markup. It can add CPU and JS cost; avoid shipping client JavaScript for static content. Framework-specific server component models can move data access and rendering to the server, but require clear boundaries for secrets, caching, and client interactivity.

Never expose secrets in serialized props or client bundles. Treat cached server output as shared data: ensure cache keys vary by all security-relevant dimensions, or do not cache personalized responses.

## Practical recommendations

- Start with the simplest strategy compatible with product requirements.
- Use static generation for stable public content.
- Use SSR when request-time data or personalization materially improves the experience.
- Use CSR for highly interactive authenticated workflows when SEO is irrelevant.
- Avoid turning every route into a different rendering architecture without a clear need.
- Measure Core Web Vitals and real-user performance on representative devices and networks.

## Release checklist

- [ ] Cache policy and invalidation behavior are documented.
- [ ] Authenticated data cannot leak through shared caches.
- [ ] Loading, error, and partial-render states are intentional.
- [ ] Hydration mismatches are tested.
- [ ] JavaScript and image budgets are monitored.
- [ ] SEO metadata, canonical URLs, and accessibility semantics are correct where relevant.
