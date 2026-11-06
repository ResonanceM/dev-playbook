# Avancerade TypeScript-mönster (Inspirerat av Matt Pocock)

---

## 🧠 Pro-nivå TypeScript-tekniker

### 1. Discriminated Unions i stället för optional-fält
Undvik fladdriga objekt med många valfria fält. Använd explicita diskriminerade unioner för att göra ogiltiga tillstånd omöjliga i koden.

```typescript
// ❌ Dåligt (flera optional-fält)
type UserState = {
  isLoading: boolean;
  data?: User;
  error?: Error;
};

// ✅ Bra (Diskriminerad union)
type UserState =
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: User }
  | { status: 'error'; error: Error };
```

### 2. Template Literal Types
Bygg strikta strängtyper dynamiskt för rutter, händelser eller fältnamn.
