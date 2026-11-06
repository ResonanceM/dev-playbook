# Team Operations and Developer Experience

Developer experience is the combined friction of understanding, changing, testing, reviewing, deploying, and operating software.

## DORA-style delivery measures

Common delivery measures include deployment frequency, lead time for changes, change failure rate, and time to restore service. Interpret them together and in context; they are not individual productivity scores. Definitions must be consistent across teams.

## DevEx dimensions

- **Cognitive load:** can engineers understand the system and find ownership?
- **Feedback loops:** how quickly do tests, builds, reviews, and deployments respond?
- **Flow:** how much work waits on approvals, dependencies, or environments?
- **Tooling:** are local setup, CI, observability, and release tools reliable?
- **Safety:** can engineers ship small changes and recover safely?

## Practical improvements

- Maintain a fast, documented local development path.
- Make CI reliable and failures diagnosable.
- Provide paved roads for common service patterns.
- Automate repetitive but deterministic work.
- Keep service catalogs, ownership, and runbooks current.
- Reduce flaky tests and slow feedback loops.
- Use templates and examples instead of mandatory heavyweight process.

## Team operating cadence

Use lightweight planning, technical design reviews for consequential decisions, regular incident learning, and periodic architecture/maintenance reviews. Protect focus time and make on-call load visible.

## Measure experience

Use surveys and interviews alongside system data. Ask where engineers lose time, what is confusing, and which internal tools are unreliable. Prioritize recurring friction with measurable impact.
