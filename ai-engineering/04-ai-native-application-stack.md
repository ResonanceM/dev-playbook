# AI-Native Application Stack and Architecture

An AI feature is a product workflow wrapped around a probabilistic capability. The application—not the model—must own identity, authorization, data integrity, and business invariants.

## Reference architecture

1. **Experience layer:** streaming UX, progress, citations, cancellation, feedback, and accessible error states.
2. **Application API:** authentication, authorization, validation, rate limiting, quotas, and request lifecycle.
3. **AI orchestration:** prompt/model selection, retrieval, tool routing, policy checks, and workflow state.
4. **Knowledge/data layer:** source systems, document ingestion, indexes, permissions, and audit.
5. **Model gateway:** provider abstraction, routing, retries, timeout, token accounting, and fallback.
6. **Evaluation/observability:** offline test sets, online feedback, tracing, cost dashboards, and safety monitoring.

## Three common workload patterns

- **Interactive generation:** user request → retrieve/context → model stream → validate/format → UI.
- **Document processing:** upload → scan/parse → queue → extract/classify → validate → human review → persist.
- **Tool-using workflow:** request → plan or route → authorized tool calls → verify results → approval if needed → complete.

## Model routing and caching

Route based on task quality, risk, latency, and cost—not model brand assumptions. Cache only when inputs, permissions, freshness, and privacy permit. Prompt caching is provider-specific and should be validated against current pricing and behavior.

## Streaming UX

Show progress and allow cancellation. Treat partial output as provisional until validation and completion. Handle disconnects and reconnects. Do not present an incomplete answer as a completed transaction.

## Data governance

Classify prompts, retrieved documents, outputs, and logs. Define retention, deletion, access, and provider data handling. Avoid sending data to a model unless necessary and authorized.

## Failure handling

Plan for provider outage, rate limits, malformed output, refusal, retrieval miss, tool failure, and user cancellation. Graceful degradation may mean a non-AI path, queued processing, or a clear “try again later” state.

## Production gates

Before launch, establish eval thresholds, abuse testing, budget limits, privacy review, incident owner, provider fallback policy, and rollback/disable switch.
