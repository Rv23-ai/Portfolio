# architecture.md — System Architecture & Structure

> Defines *how* the product is built: stack, structure, data flow. The AI agent should treat this as binding — do not deviate from folder structure or stack without updating this file first.

---

## 1. Tech Stack (confirmed)

| Layer | Choice | Reason |
|---|---|---|
| Framework | Next.js (React) | File-based routing + built-in API routes on one deploy |
| Hosting | Vercel | Zero-config Next.js deploys, serverless functions native |
| Styling | `[ ] e.g. Tailwind CSS / CSS Modules` | `[ ] decide before Phase 1` |
| Animation | `[ ] e.g. Framer Motion` | For scroll-triggered/micro-interactions |
| AI Chat backend | Next.js API route (`/app/api/chat/route.js`) | Serverless, stateless, no server to manage |
| LLM Provider | `[ ] e.g. Anthropic API (Claude)` | `[ ]` |
| Data storage | None (v1) — content is static/markdown, chat is context-stuffed, no DB | Keeps v1 simple, no infra cost |
| Content source | `[ ] e.g. local markdown/JSON files vs hardcoded components` | `[ ]` |

> Note: an earlier draft of this doc used a Flask-style structure (`app.py`, `templates/`, `static/`). That was replaced with the Next.js structure below since Next.js was the confirmed stack.

---

## 2. High-Level App Flow

```
Visitor lands on "/"
   → Hero renders immediately (static, fast)
   → Scrolls through About / Projects / Tech Stack / Contact
   → Clicks a project card → navigates to /projects/[slug] (case study page)
   → Optionally opens AI chat widget
        → types a question
        → frontend POSTs to /api/chat
        → serverless function loads bio/project context + calls LLM API
        → streams/returns answer to widget
```

---

## 3. Folder & File Structure (Next.js / Vercel)

```
portfolio/
├── .gitignore
├── .env.local              # local secrets (API keys) — never committed
├── .env.example            # documents required env vars, no real values
├── README.md
├── package.json
├── next.config.js
├── LICENSE
│
├── app/
│   ├── layout.jsx           # root layout, fonts, global providers
│   ├── page.jsx             # home page (hero, about, projects preview, contact)
│   ├── globals.css
│   │
│   ├── projects/
│   │   └── [slug]/
│   │       └── page.jsx     # dynamic case study page
│   │
│   └── api/
│       └── chat/
│           └── route.js     # serverless function powering the AI chat
│
├── components/
│   ├── Hero.jsx
│   ├── About.jsx
│   ├── ProjectCard.jsx
│   ├── TechStack.jsx
│   ├── ChatWidget.jsx
│   ├── Contact.jsx
│   └── ...
│
├── content/
│   ├── projects/             # one markdown/JSON file per project (case study content)
│   │   ├── project-1.md
│   │   └── project-2.md
│   ├── bio.md                 # source content fed into the AI chat's context
│   └── resume.pdf
│
├── lib/
│   ├── getProjects.js        # helper to read/parse content/projects
│   └── chatContext.js        # builds the system prompt/context for /api/chat
│
├── public/
│   ├── images/
│   └── favicon.ico
│
├── tests/
│   └── ...
│
└── docs/
    ├── prd.md
    ├── architecture.md
    ├── rules.md
    ├── phases.md
    ├── design.md
    └── memory.md
```

---

## 4. Data Flow — AI Chat Feature (detail)

1. `content/bio.md` + `content/projects/*.md` are the source of truth for what the AI "knows" about you.
2. `lib/chatContext.js` reads these files at request time (or build time) and assembles them into a system prompt.
3. `app/api/chat/route.js` receives the visitor's message, attaches the system prompt + context, calls the LLM API server-side.
4. API key lives only in Vercel environment variables — never sent to the browser.
5. Response streamed/returned to `ChatWidget.jsx`.

No vector database in v1 — content volume is small enough to context-stuff directly. Revisit only if content grows significantly (e.g. full blog archive).

---

## 5. Deployment

- Repo connected to Vercel → auto-deploy on push to `main`
- Environment variables (API keys) set in Vercel dashboard, mirrored in `.env.example` (without values) for local dev
- Preview deployments on PRs/branches before merging to `main`

---

## 6. Open Architecture Decisions

- [ ] Styling approach (Tailwind vs CSS Modules vs styled-components)
- [ ] Content source format — markdown files vs JSON vs hardcoded JSX
- [ ] Which LLM provider/model for the chat feature
