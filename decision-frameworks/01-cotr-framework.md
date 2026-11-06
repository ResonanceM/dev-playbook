# COTR: Context, Options, Trade-offs, Recommendation

Use COTR to explain a technical choice in terms that engineering, product, security, operations, and leadership can evaluate. It is suitable for design reviews, proposals, and concise decision records.

## 1. Context

Describe the observable problem before proposing a solution.

Include:
- User or business impact: who is affected and how often?
- Current behavior and evidence: traces, incidents, support reports, benchmarks, or workflow observations.
- Constraints: deadlines, team skills, budget, compliance, legacy dependencies, and platform boundaries.
- Non-goals: what this decision will not solve.
- Success measures: what changes if the decision works?

Avoid framing a technology preference as a business problem.

## 2. Options

List at least two viable approaches, including the status quo where relevant. Include a deliberately simpler option. Explain why apparently attractive alternatives were excluded.

For each option, describe the operating model, migration path, dependencies, and failure modes—not just the happy path.

## 3. Trade-off matrix

Score options only when scoring helps discussion. Use a consistent scale and write down what each score means.

| Dimension | Questions |
|---|---|
| User impact | Does it improve task completion, latency, or reliability? |
| Delivery cost | How long to build, migrate, and validate? |
| Operational burden | Who runs it? What new alerts, backups, and on-call work appear? |
| Complexity | How many concepts, components, and failure modes are added? |
| Security/privacy | Does it change trust boundaries, data exposure, or compliance scope? |
| Performance/scale | What workload assumptions have been tested? |
| Reversibility | How costly is it to change direction? |
| Total cost | Infrastructure, licensing, engineering, support, and opportunity cost? |

Do not use made-up precision such as an unsupported “15% productivity gain.” Label estimates, assumptions, and confidence.

## 4. Recommendation

State one recommendation, why it is the best fit now, the conditions under which it would change, and the first validation step.

A strong recommendation sounds like:

> Choose option B for the next release because it meets the required consistency and latency with the lowest migration risk. Keep the boundary behind an interface so that option C remains possible if measured throughput exceeds the current database's capacity.

## Worked example: server-state management

**Context:** Several screens independently fetch the same customer data, causing duplicated requests, inconsistent loading states, and ad hoc cache invalidation.

**Options:** Keep local fetch hooks; use a general client store; adopt a server-state library; consolidate reads behind a backend-for-frontend.

| Concern | Local hooks | General client store | Server-state library |
|---|---|---|---|
| Initial setup | Low | Medium/high | Low/medium |
| Cache lifecycle | Hand-built | Hand-built or custom | Built-in primitives |
| Mutations | Custom | Custom | Mutation/invalidation patterns |
| Best fit | Few isolated reads | Complex shared client workflows | Remote data with caching needs |
| Risk | Inconsistent duplication | Mixing server and UI state | Misconfigured cache semantics |

**Recommendation:** Use a server-state library for remote data and keep transient UI state local or in a small client store. Define cache keys, freshness, invalidation, and optimistic-update rollback explicitly. Validate with network traces and tests; do not assume a library removes the need to understand consistency.

## Review checklist

- [ ] Problem is evidence-based and solution-independent.
- [ ] Status quo and simpler options were considered.
- [ ] Constraints and non-goals are explicit.
- [ ] Trade-offs include operations, security, migration, and cost.
- [ ] Recommendation is clear and falsifiable.
- [ ] Risks have owners and mitigations.
- [ ] Decision has a review trigger or expiry condition.
