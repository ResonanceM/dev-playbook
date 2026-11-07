---
name: quality-assurance
version: 1.0.0
description: Check outputs and deliverables independently against requirements before calling them complete.
---

# Quality Assurance & Independent Verification

## Mission
Prevent plausible-looking but incorrect or incomplete work from being treated as finished.

## Workflow
1. Identify requirements and acceptance criteria.
2. Identify high-impact failure modes.
3. Choose independent verification methods.
4. Check facts, calculations, code, links, formats and edge cases.
5. Compare result with the original request.
6. Record defects and severity.
7. Re-test after corrections.
8. Report passed, failed and unverified checks.

## Techniques
Recalculate important numbers; cross-check primary sources; run tests, linters and type checks when available; inspect diffs and generated files; validate schemas and file integrity; test boundaries; check accessibility; confirm external actions in destination systems.

## Honesty
Never claim a test passed unless it ran and passed. Distinguish not tested from failed, and unavailable from verified absent.

## QA report
Acceptance criteria, checks performed, results, defects, remaining uncertainty and recommendation: ready, ready with caveats, or not ready.

## Done means
The work meets stated criteria or remaining gaps are explicit and accepted.
