# AI Agents and Workflow Orchestration

An agent uses a model to choose actions or sequence steps. Use agent autonomy only when dynamic decision-making creates enough value to justify nondeterminism and operational risk.

## Start with deterministic workflows

If steps and transitions are known, use ordinary code or a workflow engine. Add model decisions only where inputs are ambiguous or the next action genuinely depends on context.

## Core architecture

- **Orchestrator:** controls state, transitions, retries, deadlines, and termination.
- **Model:** proposes a response or action within a constrained contract.
- **Tools:** narrowly scoped capabilities with explicit schemas and authorization.
- **State:** durable workflow state with provenance and versioning.
- **Policy layer:** enforces permissions, limits, approvals, and safety.
- **Human review:** required for high-impact or irreversible actions.
- **Telemetry:** records decisions, tool calls, errors, latency, and cost.

## Tool design

Tools should be small, typed, documented, and least-privileged. Validate arguments server-side. Separate read tools from write tools. Make writes idempotent where possible. Require confirmation or approval for sensitive actions. Never let the model choose arbitrary credentials, SQL, shell commands, or unrestricted URLs.

## MCP and integrations

The Model Context Protocol (MCP) standardizes how AI applications connect to tools and context providers. Treat MCP servers like privileged integrations: authenticate clients, authorize each action, validate inputs, limit capabilities, protect secrets, and audit calls. Protocol compatibility does not establish trust.

## Orchestration patterns

- Sequential chain for known ordered steps.
- Router for selecting among bounded specialists.
- Parallel fan-out for independent tasks, with aggregation.
- Plan-and-execute for tasks requiring adaptive decomposition.
- Human-in-the-loop for approval or ambiguity.
- Durable state machine for long-running workflows.

## Safety controls

Set maximum steps, tool-call count, token budget, wall-clock deadline, and monetary budget. Detect loops. Bound output sizes. Prevent prompt injection from tool results from changing authorization. Keep a human override and cancellation path.

## Evaluation

Test complete trajectories, not just final text. Measure task success, tool correctness, unauthorized action rate, retries, loop rate, latency, and cost. Include adversarial and ambiguous cases.

## Checklist

- [ ] Agent is justified over a deterministic workflow.
- [ ] Tools are least-privileged and schema-validated.
- [ ] State and transitions are durable and auditable.
- [ ] Limits prevent runaway execution.
- [ ] Human approval gates high-impact actions.
- [ ] Tool outputs are treated as untrusted.
- [ ] End-to-end trajectories are evaluated.
