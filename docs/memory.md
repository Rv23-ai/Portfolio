# memory.md — Build Progress Log

> This file is NOT filled in at project start. It starts empty (as below) and gets updated by whoever is building (human or AI) after every 2–4 completed tasks. Purpose: anyone (or any AI session) picking this project back up can read this file alone and know exactly where things stand, without re-reading the whole conversation history.

---

## How to update this file

After completing 2–4 tasks/checkboxes from `phases.md`:
1. Add a new dated entry below (most recent at the top)
2. Note which phase/tasks were completed
3. Note which file(s) were touched
4. Note what's next
5. Note any deviations from `architecture.md` / `rules.md` / `design.md` — and why, if any were necessary

---

## Log Format (copy this block for each new entry)

```
### [YYYY-MM-DD] — Phase X: <phase name>

**Completed:**
- [ ] task
- [ ] task

**Files touched:**
- path/to/file.jsx
- path/to/file.js

**Currently in progress / next up:**
- what's being worked on right now

**Deviations / decisions made:**
- none, OR: describe what changed from the docs and why

**Blockers/open questions:**
- none, OR: what's unresolved
```

---

## Log

### 2026-08-15 — Phase 0: Setup & Scaffolding

**Completed:**
- [x] Initialized Next.js App Router project in `d:\Github\Portfolio`
- [x] Created exact directory & file structure per `docs/architecture.md`
- [x] Configured `.gitignore` and created `.env.example`
- [x] Updated `README.md` with project details
- [x] Verified local build and compilation (`npm run build` succeeded with zero errors)
- [x] Committed Phase 0 scaffolding to Git

**Files touched:**
- `package.json`
- `README.md`
- `.gitignore`
- `.env.example`
- `app/layout.jsx`
- `app/page.jsx`
- `app/globals.css`
- `app/projects/[slug]/page.jsx`
- `app/api/chat/route.js`
- `components/Hero.jsx`
- `components/About.jsx`
- `components/ProjectCard.jsx`
- `components/TechStack.jsx`
- `components/ChatWidget.jsx`
- `components/Contact.jsx`
- `content/projects/project-1.md`
- `content/projects/project-2.md`
- `content/bio.md`
- `lib/getProjects.js`
- `lib/chatContext.js`

**Currently in progress / next up:**
- Awaiting styling framework decision from user before starting Phase 1 (Static Layout Skeleton)

**Deviations / decisions made:**
- Scaffolded without pre-installed Tailwind CSS or major styling library to keep styling choice open per `rules.md`.

**Blockers/open questions:**
- Open decision: User choice on styling system (Tailwind CSS vs CSS Modules vs Styled Components vs Vanilla CSS).

