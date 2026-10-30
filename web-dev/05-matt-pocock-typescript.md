# Advanced TypeScript Patterns & Type-Driven Design
*Inspired by Matt Pocock (Total TypeScript)*

---

## 🧠 Must-Know TypeScript Techniques

### 1. Discriminated Unions over Optional Properties
Avoid ambiguous state types with optional flags. Use explicit type discriminators.

```typescript
// ❌ Bad (Ambiguous)
type State = { isLoading: boolean; data?: User; error?: Error };

// ✅ Good (Discriminated Union)
type State =
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: User }
  | { status: 'error'; error: Error };
```

### 2. Template Literal Types
Derive strict, typed string patterns directly in TypeScript.

```typescript
type Event = 'click' | 'hover';
type Element = 'button' | 'link';
type EventHandler = `on${Capitalize<Event>}${Capitalize<Element>}`; 
// 'onClickButton' | 'onClickLink' | 'onHoverButton' | 'onHoverLink'
```

---

## 🔗 Essential Resources
* [Matt Pocock's Total TypeScript](https://www.totaltypescript.com/) — Pro-level TypeScript tutorials & patterns.
* [type-challenges/type-challenges](https://github.com/type-challenges/type-challenges) — Interactive TypeScript type exercises.
