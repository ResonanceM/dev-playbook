# TypeScript: Type-Driven Design and Runtime Boundaries

TypeScript improves developer feedback, but types are erased at runtime. Treat external data as unknown until validated.

## Core practices

### Prefer `unknown` at boundaries
Use `unknown` for parsed JSON, network responses, environment variables, and untrusted plugin data. Narrow it with validation rather than asserting it into a desired shape.

### Model domain states explicitly
Use discriminated unions to represent mutually exclusive states. Avoid boolean combinations that permit impossible states.

```ts
type Result<T, E> =
  | { ok: true; value: T }
  | { ok: false; error: E };

type PaymentState =
  | { status: "pending"; requestId: string }
  | { status: "authorized"; authorizationId: string }
  | { status: "declined"; reason: string };
```

### Make invalid states difficult to express
Use branded identifiers when mixing IDs is dangerous, constructors for validated values, and exhaustive `switch` statements with a `never` check.

### Use generics for reusable relationships
Generics are valuable when input and output types are related. Avoid abstract generic frameworks that obscure simple business logic.

### Prefer composition
Use small interfaces and composition over deep inheritance. Keep public types stable and implementation details private.

## Compiler configuration

For new projects, consider strict mode and evaluate options such as `noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`, and `useUnknownInCatchVariables`. Adopt stricter flags incrementally in legacy code.

## Runtime validation

Use a schema library or explicit validators for API payloads, forms, environment configuration, queue messages, and persisted data. Share schemas between client and server only where ownership and versioning are clear.

## Type design pitfalls

- `any` silently removes safety.
- `as` assertions do not validate data.
- Optional properties can hide missing required business information.
- Overloaded utility types can make errors unreadable.
- Giant unions can become hard to maintain.
- Types should not mirror database internals blindly.

## Example: safe parsing

```ts
import { z } from "zod";

const UserSchema = z.object({
  id: z.string().uuid(),
  email: z.string().email(),
  role: z.enum(["member", "admin"]),
});

type User = z.infer<typeof UserSchema>;

function parseUser(input: unknown): User {
  return UserSchema.parse(input);
}
```

Handle validation errors deliberately at the boundary; do not assume parsing always succeeds.

## Review checklist

- [ ] External values enter as `unknown`.
- [ ] Runtime schemas validate untrusted inputs.
- [ ] Domain states are modeled explicitly.
- [ ] Strictness is enabled where feasible.
- [ ] Assertions and `any` have clear justification.
- [ ] Public types are stable and documented.
