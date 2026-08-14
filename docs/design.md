# design.md — Visual Design System

> Defines the visual identity so every component looks like it belongs to the same site. Fill in the `[ ]` decisions before Phase 3 (Visual Design Pass) begins. Direction confirmed: **bold & experimental** — unique layout, strong visual identity, not a generic template look.

---

## 1. Design Direction

**Chosen direction:** Bold & experimental
**What this means in practice:**
- Strong, opinionated visual identity — not a safe, symmetric SaaS-template look
- Willing to use asymmetry, large type, unexpected layout choices
- Motion and interaction as part of the identity, not decoration bolted on
- Still must stay usable and fast — "bold" doesn't mean "confusing" or "slow"

**Reference sites / inspiration (optional):**
`[ ] paste links to 2-3 portfolio or product sites whose vibe you like, to anchor the direction concretely`

---

## 2. Color Palette

| Role | Color | Hex | Notes |
|---|---|---|---|
| Background (primary) | `[ ]` | `[ ]` | e.g. near-black for bold/dark-first |
| Background (secondary) | `[ ]` | `[ ]` | for section contrast |
| Text (primary) | `[ ]` | `[ ]` | |
| Text (secondary/muted) | `[ ]` | `[ ]` | |
| Accent (primary) | `[ ]` | `[ ]` | used for CTAs, highlights, links |
| Accent (secondary) | `[ ]` | `[ ]` | optional second accent for contrast pops |
| Success/Error (chat states) | `[ ]` / `[ ]` | `[ ]` | for chat widget feedback states |

**Dark mode:** default `[ ] yes/no` — toggle available `[ ] yes/no`

---

## 3. Typography

| Use | Font | Notes |
|---|---|---|
| Display/Headings | `[ ] e.g. a distinctive display font` | Should carry the "bold" identity |
| Body text | `[ ] e.g. a clean, highly readable sans` | Readability over style here |
| Monospace (code/tech accents) | `[ ] e.g. JetBrains Mono` | Good fit for a dev portfolio, use sparingly for labels/tags |

**Type scale (example — adjust once fonts chosen):**
- H1 (hero): `[ ] e.g. 5–7rem, tight line-height`
- H2 (section headers): `[ ] e.g. 2.5–3rem`
- Body: `[ ] e.g. 1–1.125rem`
- Small/labels: `[ ] e.g. 0.875rem, uppercase, letter-spaced`

---

## 4. Spacing & Layout

- Grid system: `[ ] e.g. 12-column, or custom asymmetric grid`
- Section vertical rhythm: `[ ] e.g. generous, min 6–10rem between major sections`
- Max content width: `[ ] e.g. 1200px, or intentionally full-bleed in places for boldness`

---

## 5. Motion Principles

- Scroll-triggered reveals: `[ ] which sections, what trigger point`
- Hover/micro-interactions: `[ ] buttons, cards, links — what happens on hover`
- Page transitions: `[ ] e.g. subtle fade/slide between home and case study pages`
- **Rule:** motion should never delay the user from reading/acting — keep durations short (150–400ms range typically), never block interaction

---

## 6. Component-Specific Notes

**Hero:** `[ ] layout idea — e.g. oversized name/title, asymmetric composition`
**Project cards:** `[ ] hover behavior, image treatment`
**Chat widget:** `[ ] floating button vs docked panel, open/close animation`
**Case study pages:** `[ ] how architecture diagrams/images are presented`

---

## 7. Accessibility Constraints (non-negotiable even in a bold design)

- Text/background contrast must meet WCAG AA minimum
- All interactive elements keyboard-navigable
- Motion respects `prefers-reduced-motion`
- Alt text on all meaningful images
