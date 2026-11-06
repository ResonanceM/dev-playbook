# LLM APIs and Prompt Engineering

Treat an LLM call as a probabilistic dependency with latency, cost, safety, and availability characteristics—not as a deterministic function.

## Model selection

Evaluate models on representative tasks using quality, latency, cost, context capacity, tool support, data handling terms, availability, and operational constraints. Use the smallest model that meets quality requirements. Route difficult or high-impact cases to stronger models only when evaluation supports it.

## Prompt design

A robust prompt separates:
- Role and task objective.
- Trusted instructions and policy.
- Untrusted user or retrieved content.
- Available tools and their schemas.
- Output contract.
- Examples and edge cases.

Be explicit about uncertainty and refusal behavior. Do not rely on prompt wording as the only security boundary.

## Structured output

Use provider-supported structured output or constrained JSON schemas where available. Validate every response at runtime. Handle refusals, truncation, invalid schemas, and provider errors separately.

```ts
const output = await model.generate({
  responseFormat: {
    type: "json_schema",
    schema: {
      type: "object",
      properties: {
        category: { type: "string", enum: ["billing", "technical", "other"] },
        confidence: { type: "number", minimum: 0, maximum: 1 }
      },
      required: ["category", "confidence"],
      additionalProperties: false
    }
  }
});

// Validate again at the application boundary.
const parsed = ClassificationSchema.parse(output);
```

Provider APIs differ; adapt the shape to the selected provider's current documentation.

## Reliability patterns

- Set request timeouts and cancellation.
- Bound retries and avoid retrying permanent errors.
- Handle rate limits and provider outages.
- Stream only when incremental output benefits the user.
- Track model/version, prompt version, token usage, latency, and outcome.
- Use idempotency for side-effecting workflows.
- Keep a fallback or graceful degradation path.

## Prompt injection and trust boundaries

Treat user text, retrieved documents, web pages, and tool outputs as untrusted data. Delimit and label them, constrain tools, validate arguments, and enforce authorization outside the model. A model instruction such as “ignore malicious content” is not a security control.

## Prompt lifecycle

Version prompts, test changes against a regression set, compare variants, and roll out gradually. Avoid silently changing prompts that influence consequential decisions.

## Checklist

- [ ] Model choice is supported by task-specific evaluation.
- [ ] Inputs and outputs are validated.
- [ ] Untrusted content is clearly separated.
- [ ] Tool permissions are enforced outside the model.
- [ ] Timeouts, retries, quotas, and fallbacks exist.
- [ ] Prompt/model versions and cost are observable.
- [ ] Sensitive data handling matches policy and provider terms.
