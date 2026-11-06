# AI Product Playbook: From Use Case to Trusted Capability

AI should solve a real user problem better than a simpler alternative. Novelty is not product value.

## Use-case qualification

Assess:
- User pain and frequency.
- Whether the task is language/knowledge intensive or benefits from probabilistic inference.
- Cost of an incorrect answer or action.
- Availability and quality of source data.
- Human review requirements.
- Privacy, safety, legal, and regulatory constraints.
- Whether deterministic rules or conventional search are sufficient.

## Define the product contract

Specify what the AI does, what it does not do, how uncertainty is shown, when it asks clarifying questions, when it refuses, and how users correct or appeal outcomes.

## Human control

For consequential actions, separate recommendation from execution. Require explicit confirmation, review, or escalation based on impact. Provide undo where possible and preserve an audit trail.

## Success metrics

Measure task completion, time saved, correction rate, escalation rate, user trust, quality, safety incidents, latency, and cost per successful outcome. Do not optimize only engagement or generated volume.

## Rollout

Start with internal testing, then a limited cohort. Use representative evals and monitor quality by user segment and task category. Maintain a non-AI fallback and kill switch.

## Product anti-patterns

- AI added without a user problem.
- “Human-like” output mistaken for correctness.
- No explanation of limitations.
- No feedback or correction path.
- Cost and review effort omitted from unit economics.
- High-impact decisions delegated without meaningful oversight.
