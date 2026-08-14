# phases.md — Phased Build Plan

> Deliberately broken into small phases. Each phase should be independently completable, testable, and low-risk. Do not start phase N+1 until phase N's exit criteria are met and `memory.md` is updated.

---

## Phase 0 — Setup & Scaffolding
**Goal:** Empty but correctly structured project, deployable.
- [ ] Initialize Next.js app with App Router
- [ ] Set up folder structure per `architecture.md`
- [ ] Configure `.gitignore`, `.env.example`
- [ ] Install and configure styling system (once chosen)
- [ ] Push to GitHub, connect to Vercel, confirm a blank deploy works
**Exit criteria:** Blank Next.js site live on a Vercel URL.

---

## Phase 1 — Static Layout Skeleton
**Goal:** All sections exist on the page with placeholder content, no styling polish yet.
- [ ] Build `Hero`, `About`, `ProjectCard` (preview), `TechStack`, `Contact` components
- [ ] Assemble on `app/page.jsx` in order
- [ ] Placeholder text/images only
**Exit criteria:** Full page scrolls top to bottom with all sections present.

---

## Phase 2 — Content Wiring
**Goal:** Real content replaces placeholders (once you've provided it).
- [ ] Set up `content/` folder (bio.md, project markdown files)
- [ ] Write `lib/getProjects.js` to read/parse project content
- [ ] Replace placeholder text in About/Hero with real copy
- [ ] Wire project preview cards to real project data
**Exit criteria:** Home page shows real content, no more `[ ]` placeholders visible.

---

## Phase 3 — Visual Design Pass
**Goal:** Site matches the bold/experimental direction from `design.md`.
- [ ] Apply color palette, typography from `design.md`
- [ ] Layout refinement (spacing, grid, responsiveness)
- [ ] Add scroll-triggered animations / micro-interactions
- [ ] Mobile responsiveness pass
**Exit criteria:** Site looks intentional and polished on desktop + mobile.

---

## Phase 4 — Project Case Study Pages
**Goal:** Deep-dive pages for flagship project(s).
- [ ] Build `app/projects/[slug]/page.jsx` dynamic route
- [ ] Design case study layout (problem, approach, architecture, results, links)
- [ ] Wire real content for project #1
- [ ] Wire real content for project #2 (if applicable)
**Exit criteria:** Clicking a project card leads to a fully built, real case study page.

---

## Phase 5 — AI Chat Backend
**Goal:** Working serverless chat endpoint, no UI yet.
- [ ] Write `lib/chatContext.js` to assemble system prompt from bio/project content
- [ ] Build `/app/api/chat/route.js`
- [ ] Test via direct API calls (curl/Postman) before building UI
- [ ] Add error handling per `rules.md`
**Exit criteria:** POSTing a question to `/api/chat` returns a coherent, grounded answer.

---

## Phase 6 — AI Chat Frontend
**Goal:** Visitor-facing chat widget.
- [ ] Build `ChatWidget.jsx` (open/close, input, message list)
- [ ] Wire to `/api/chat`
- [ ] Add loading/error states
- [ ] Style to match site's visual identity
**Exit criteria:** A visitor can open the widget, ask a question, get a real answer, with no crashes.

---

## Phase 7 — Polish & Edge Cases
**Goal:** Handle the rough edges.
- [ ] Empty states, 404 page, broken-link handling
- [ ] Rate limiting on `/api/chat`
- [ ] Accessibility pass (contrast, keyboard nav, alt text)
- [ ] Performance pass (image optimization, Lighthouse check)
**Exit criteria:** No obvious bugs in a full manual walkthrough.

---

## Phase 8 — SEO & Metadata
**Goal:** Discoverable, shareable.
- [ ] `metadata` exports per page (title, description)
- [ ] Open Graph / social preview images
- [ ] `sitemap.xml`, `robots.txt`
- [ ] Favicon set
**Exit criteria:** Sharing the link shows a proper preview card; site is indexable.

---

## Phase 9 — Final QA & Launch
**Goal:** Production-ready.
- [ ] Full cross-browser check
- [ ] Mobile device check
- [ ] Final content proofread
- [ ] Custom domain connected (if applicable)
- [ ] Announce/share
**Exit criteria:** Live, correct, and ready to be sent to recruiters.

---

## Phase Tracking Note
After completing 2–4 tasks (checkboxes) within any phase, update `memory.md` with what was done and what's next — see `memory.md` for the exact format.
