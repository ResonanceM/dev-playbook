# Pragmatic RFCs, ADRs, and Staff-Level Alignment

Architecture work is successful when it helps a group make a timely, informed decision—not when it produces a long document.

## RFC versus ADR

- **RFC (Request for Comments):** a proposal circulated before a decision. It invites alternatives, questions, and stakeholder input.
- **ADR (Architecture Decision Record):** a concise record of a decision already made, including context and consequences.
- **Design document:** a deeper description of a proposed or existing system, interfaces, data flows, and operational behavior.
- **Runbook:** instructions for operating or recovering a service.

## Reversibility and decision depth

A useful heuristic is to distinguish decisions that are cheap to reverse from decisions that create long-lived commitments.

| Decision type | Examples | Process |
|---|---|---|
| Easily reversible | Internal component organization, local library choice | Team discussion, small experiment |
| Costly to reverse | Public API shape, data model, tenancy model, identity provider | Written proposal, cross-functional review |
| High-risk / regulated | Security boundary, data residency, safety-critical workflow | Formal threat/risk review, specialist approval, audit trail |

Do not use the Type 1/Type 2 label mechanically. Consider blast radius, migration cost, external commitments, and time-to-learn.

## RFC lifecycle

1. **Discover:** collect user needs, constraints, current-state evidence, and stakeholders.
2. **Draft:** state the problem, goals, non-goals, proposal, alternatives, and open questions.
3. **Review:** invite affected teams, operations, security, data, and product.
4. **Resolve:** capture objections, decisions, and accepted risks; assign owners.
5. **Record:** create an ADR with status and links to implementation.
6. **Validate:** compare outcomes with assumptions after rollout.

Set a review window and a decision owner. Avoid endless consensus loops; distinguish blocking safety concerns from preferences.

## Minimum RFC outline

- Title, author, reviewers, status, date
- Summary and decision needed
- Context and evidence
- Goals and non-goals
- Proposed design and key interfaces
- Alternatives considered
- Data model and migration
- Security, privacy, and threat considerations
- Reliability, performance, and operational impact
- Rollout, rollback, and observability
- Cost, staffing, dependencies, and risks
- Open questions and decision deadline

## ADR quality bar

An ADR should explain **why**, not merely record **what**. Keep it short enough to read in one sitting. Use statuses such as Proposed, Accepted, Rejected, Superseded, or Deprecated. Never silently rewrite history: supersede an old ADR with a new one.

## Staff-level alignment

Staff-level influence comes from clarifying the problem, surfacing hidden constraints, reducing cross-team ambiguity, and creating a path to execution. It does not mean unilaterally selecting a stack.

Before a review:
- Identify the decision owner and impacted teams.
- Share the document early with specific questions.
- Bring evidence and a prototype where uncertainty is empirical.
- Separate facts, assumptions, preferences, and unresolved risks.
- Offer a phased option when the full proposal is too risky.

After a review:
- Publish the decision and dissenting concerns.
- Convert decisions into owners, milestones, and measurable validation.
- Communicate what changes for dependent teams.
- Revisit the decision when its trigger conditions occur.
