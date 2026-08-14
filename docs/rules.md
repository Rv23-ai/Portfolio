# rules.md — Build Rules & Guardrails

> Concrete do's/don'ts for whoever (human or AI) is writing code on this project. When in doubt, this file wins over general habits or defaults.

---

## 1. Libraries & Tools — Use

| Category | Approved | Notes |
|---|---|---|
| Framework | Next.js (App Router) | Do not use Pages Router — keep consistent with app/ structure |
| Styling | `[ ] to confirm — e.g. Tailwind CSS` | Once chosen, do not mix in a second styling system |
| Animation | `[ ] e.g. Framer Motion` | Keep animations purposeful, not decorative-only |
| Icons | `[ ] e.g. lucide-react` | One icon library only, don't mix |
| LLM SDK | Official Anthropic/OpenAI SDK (server-side only) | Never call LLM APIs from client-side code |
| Package manager | `[ ] npm / pnpm / yarn — pick one and stick to it` | |

## 2. Libraries & Patterns — Avoid

- No jQuery or non-React DOM manipulation
- No client-side API key usage — anything with a secret must live in a server component or API route
- No inline styles as the primary styling method (fine for tiny one-offs, not for components)
- No unnecessary state management libraries (Redux, Zustand) unless app complexity genuinely requires it — React state/context is enough for a portfolio
- No vector database / RAG infra until content volume actually requires it (see architecture.md)
- Avoid `useEffect` for things that can be server-rendered or computed at build/request time

## 3. Error Handling Standards

- Every API route (`/app/api/**`) must wrap logic in try/catch and return a proper status code + JSON error shape, e.g.:
  ```js
  { error: true, message: "..." }
  ```
- The AI chat route must handle: empty input, LLM API failure, rate limiting/timeout — with a user-visible fallback message, never a raw stack trace
- Never let a failed component crash the whole page — use error boundaries for the chat widget specifically, since it's the most likely point of failure

## 4. Security

- All secrets in environment variables, never hardcoded, never committed
- `.env.local` must be in `.gitignore`
- `.env.example` must list required variable names with placeholder values only
- Sanitize/limit user input length before sending to the LLM API (prevent abuse/cost blowup)
- Add basic rate limiting to `/api/chat` before public launch (even simple IP-based throttling)

## 5. Code Style

- Functional components only, no class components
- Keep components small and single-purpose — if a component file exceeds ~150 lines, consider splitting
- Co-locate a component's styles with the component unless using a global utility system (Tailwind)
- Comments explain *why*, not *what* — code should be readable enough that *what* is obvious

## 6. AI Agent Boundaries

> These apply specifically when an AI (Claude Code or similar) is doing the building.

- The AI **must** follow `phases.md` in order — do not skip ahead to later phases before earlier ones are marked complete in `memory.md`
- The AI **must not** invent content (bio text, project descriptions, metrics) — if content is missing, it should insert a clear `[ ] placeholder`, not fabricate plausible-sounding filler
- The AI **must not** introduce a new major dependency (new library, new service) without flagging it first — additions to the stack should be deliberate, not incidental
- The AI **must** update `memory.md` after every 2–4 completed tasks, per the process defined there
- The AI **should** ask for clarification rather than guess when a requirement in `prd.md` is ambiguous
- The AI **should** prefer the simplest solution that satisfies `prd.md` — no speculative/generalized abstractions for features that don't exist yet

## 7. Testing Expectations

- `[ ] define minimum testing bar — e.g. manual QA per phase, or automated tests for /api/chat only`
