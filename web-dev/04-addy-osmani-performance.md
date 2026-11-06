# Frontend Performance Engineering

Performance is a user experience and business concern. Optimize the critical path and validate with field data.

## Measurement model

- **Core Web Vitals:** LCP (loading), INP (interaction responsiveness), and CLS (visual stability).
- **Field data (RUM):** real users, devices, geographies, and network conditions.
- **Lab data:** repeatable diagnostics for regressions and controlled experiments.
- **Backend timings:** server response, database, and dependency latency.
- **User outcomes:** task completion, abandonment, and conversion.

Use percentile distributions and segment by device/network; averages hide slow experiences.

## Practical optimization order

1. Establish a baseline and identify the slow user journey.
2. Improve server response and eliminate avoidable request waterfalls.
3. Optimize critical images: dimensions, modern formats, responsive sources, priority hints.
4. Reduce render-blocking CSS and JavaScript.
5. Split code by route and interaction; defer non-critical work.
6. Reduce long main-thread tasks and unnecessary re-renders.
7. Cache static assets with immutable content hashes.
8. Use preconnect/preload only for critical known dependencies.
9. Re-measure in field data.

## Resource loading

- Prioritize the actual LCP resource; avoid lazy-loading it.
- Lazy-load below-the-fold images and non-critical components.
- Reserve image/video dimensions to prevent layout shifts.
- Avoid excessive third-party scripts; each adds network, CPU, privacy, and reliability cost.
- Use fonts carefully: subset, preload only critical faces, and define fallbacks.

## JavaScript and rendering

- Analyze bundle composition, not just total size.
- Prefer platform APIs and small focused dependencies where practical.
- Avoid expensive synchronous work during input.
- Virtualize genuinely large lists; do not add virtualization to every list.
- Use memoization only when profiling shows meaningful work or identity instability.
- Keep server-rendered static content out of the client bundle when possible.

## Performance budgets

Set budgets for route-level JS, image weight, LCP, INP, CLS, and API latency. Budgets are guardrails, not universal values. Enforce important budgets in CI and monitor field distributions after release.

## Common mistakes

- Optimizing microbenchmarks unrelated to user journeys.
- Adding preload hints indiscriminately.
- Lazy-loading the hero image.
- Treating Lighthouse as a substitute for field data.
- Caching personalized responses without correct variation.
- Fixing frontend symptoms while backend latency dominates.

## Checklist

- [ ] Baseline and target are documented.
- [ ] LCP element and critical path are known.
- [ ] Images have responsive sizing and reserved dimensions.
- [ ] Non-critical JS and third parties are deferred or removed.
- [ ] Long tasks and interaction delays are measured.
- [ ] Field metrics are segmented and monitored.
