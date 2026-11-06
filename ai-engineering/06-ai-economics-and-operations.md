# AI Unit Economics and Production Operations

AI economics should be measured per successful user outcome, not only per token.

## Cost model

Include:
- Input and output tokens, including cached-token pricing where applicable.
- Embedding and reranking calls.
- Vector/search/database infrastructure.
- Document parsing and storage.
- Tool/API calls and workflow compute.
- Human review and support.
- Evaluation, monitoring, and failed/retried requests.

A useful metric is cost per successful task, segmented by task type and customer tier.

## Cost controls

- Use smaller models for simple tasks when quality holds.
- Bound context and retrieve only relevant evidence.
- Limit output length and tool calls.
- Cache safe, reusable work.
- Batch offline workloads where latency permits.
- Set per-user and per-tenant quotas.
- Detect loops, repeated retries, and abnormal usage.
- Alert on spend rate and cost per completed task.

## Reliability and operations

Track provider latency, error/rate-limit rates, token volume, refusal rates, schema failures, retrieval misses, tool success, and user outcomes. Use correlation IDs across application, retrieval, model, and tool calls.

## Capacity and fallback

Plan quotas and provider limits. Consider multi-provider routing only if the added complexity and data-governance implications are acceptable. Fallback models may behave differently; run the same evaluation suite against them.

## Vendor and model governance

Record model version, region, data retention terms, subprocessors, availability commitments, pricing assumptions, and change-notification policy. Re-evaluate after provider model changes.

## Checklist

- [ ] Cost per successful outcome is measured.
- [ ] Quotas and budget alerts exist.
- [ ] Retries and agent loops are bounded.
- [ ] Provider limits and fallback behavior are tested.
- [ ] Model/version and prompt configuration are traceable.
- [ ] Data handling and vendor terms are reviewed.
