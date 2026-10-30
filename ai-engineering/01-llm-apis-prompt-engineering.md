# AI Engineering: LLM Integration & Prompt Architecture

---

## 🤖 Model Choice Matrix

| Provider / Model | Strengths | Ideal Use Case | Cost Profile |
| :--- | :--- | :--- | :--- |
| **OpenAI (GPT-4o / O1)** | High reasoning, reliable tool calling | Complex multi-step reasoning, agents | Premium API pricing |
| **Anthropic (Claude 3.5 Sonnet)** | Superior coding capability, natural writing | Code generation, complex artifact creation | Competitive |
| **Groq / Llama 3 (Open Source)** | Ultra-low latency ($\sim 300	ext{ tokens/sec}$) | High-throughput chat, simple classifications | Ultra-cheap / Self-hosted |

---

## 🛠️ Senior AI Engineering Patterns

### 1. Structured Outputs (Forced JSON Schemas)
Never parse LLM output using raw regex. Use **Pydantic** (Python) or **Zod** (TypeScript) with structured output APIs or libraries like **Instructor**.

### 2. Defensive Prompting & Security
* **System Prompt Isolation:** Explicitly delimit user inputs using XML tags (`<user_query>...</user_query>`).
* **Prompt Injection Defense:** Validate and filter input tokens before passing to LLM.

---

## 🔗 Essential Resources & Repositories
* [jxnl/instructor](https://github.com/jxnl/instructor) — Structured outputs for LLMs using Pydantic.
* [colinhacks/zod](https://github.com/colinhacks/zod) — TypeScript-first schema validation for structured LLM parsing.
* [OpenAI Cookbook](https://github.com/openai/openai-cookbook) — Examples and guidelines for using the OpenAI API.
