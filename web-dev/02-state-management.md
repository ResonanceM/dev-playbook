# Frontend State Management: Assign State to the Right Owner

Most state bugs come from unclear ownership, duplicated sources of truth, or lifecycle assumptions.

## State taxonomy

| State type | Examples | Preferred location |
|---|---|---|
| Server state | Users, orders, search results | Query/cache layer |
| URL state | Search terms, filters, pagination, selected tab when shareable | URL/query parameters |
| Local UI state | Open dialog, hover, draft input | Component state |
| Shared client state | Wizard progress, local preferences, cross-component workflow | Small client store or context |
| Form state | Values, dirty/touched, validation | Form library or local state |
| Persistent device state | Theme, dismissed notice | Storage with versioning and privacy review |
| Ephemeral realtime state | Presence, typing indicator | Realtime connection layer |

Do not copy server state into a global store unless there is a specific reason and a synchronization policy.

## Server-state lifecycle

Define:
- Query identity/key and parameter normalization.
- Freshness and stale-time policy.
- Cache retention and memory limits.
- Refetch triggers (focus, reconnect, polling, invalidation).
- Mutation strategy and optimistic rollback.
- Pagination/infinite loading behavior.
- Cancellation and race handling.
- Permission changes and logout cache clearing.

## URL state

Put state in the URL when users should be able to bookmark, share, reload, or navigate back to it. Validate and normalize URL input. Avoid encoding secrets or sensitive personal data in query parameters.

## Common anti-patterns

- One giant global store for every value.
- Fetching in effects without cancellation or race protection.
- Duplicating server state in component and global state.
- Storing derived values that can be computed.
- Persisting transient or sensitive values indefinitely.
- Optimistic updates without rollback and conflict behavior.

## Decision rule

Keep state as local as possible, lift it only to the lowest common owner, and make external state ownership explicit. Introduce a store when coordination complexity is real—not because the application has reached an arbitrary component count.
