# AI Evaluation, Safety, and Quality Assurance

LLM quality is multidimensional. A single “accuracy” score rarely captures usefulness, groundedness, safety, and reliability.

## Evaluation layers

- **Unit tests:** deterministic parsing, validation, policy checks, tool wrappers.
- **Component evals:** retrieval, classification, extraction, ranking, or summarization.
- **End-to-end evals:** realistic user tasks and complete workflows.
- **Adversarial evals:** prompt injection, jailbreak attempts, malicious files, data exfiltration, and tool misuse.
- **Human review:** expert assessment for subjective or high-impact outcomes.
- **Online monitoring:** feedback, escalation, drift, refusal, latency, and cost.

## Dataset design

Use representative, diverse, versioned examples. Include common cases, edge cases, ambiguous requests, long context, multilingual inputs, out-of-domain questions, and adversarial inputs. Keep a held-out set to reduce overfitting to the evaluation suite.

## Metrics

Choose metrics aligned with the task: exact match or field-level accuracy for extraction; precision/recall for classification; recall@k and nDCG for retrieval; groundedness and citation correctness for RAG; task completion and tool correctness for agents.

Use rubrics with clear anchors for human evaluation. Calibrate graders and inspect disagreements. Model-based graders are useful but can share biases with the system being evaluated.

## Safety and trust

- Treat all external content as untrusted.
- Enforce permissions and business rules in application code.
- Minimize sensitive input and output.
- Use refusal and escalation paths for unsupported/high-risk tasks.
- Constrain tools and require approval for consequential actions.
- Test for leakage, harmful output, manipulation, and unsafe overconfidence.

## Release strategy

Version prompts, models, retrieval settings, and tool schemas. Run regression evaluations on every meaningful change. Use shadow/canary rollout and monitor segment-level regressions. Maintain a kill switch.

## Checklist

- [ ] Evaluation set represents real usage and adversarial cases.
- [ ] Quality thresholds are defined per task.
- [ ] Human review is used where appropriate.
- [ ] Safety boundaries are enforced outside the model.
- [ ] Prompt/model/config versions are traceable.
- [ ] Rollout, rollback, and kill switch are tested.
