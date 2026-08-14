# Personal Portfolio Website

An interactive, personal portfolio website built with Next.js (App Router), showcasing deep-dive project case studies and an embedded AI chat assistant.

## Features & Structure

- **App Router Architecture:** Modular Next.js structure (`app/`, `components/`, `content/`, `lib/`).
- **Project Case Studies:** Dynamic routing for deep-dive technical project write-ups (`/projects/[slug]`).
- **AI Chat Assistant:** Serverless endpoint powering an interactive QA experience about background, experience, and projects (`/api/chat`).
- **Static Content Driven:** Markdown-based content management (`content/projects/`, `content/bio.md`).

## Development

```bash
# Install dependencies
npm install

# Run dev server
npm run dev

# Build for production
npm run build
```

## Documentation

Full project specifications and build phase tracking can be found under `docs/`:
- `docs/prd.md`: Product Requirements Document
- `docs/architecture.md`: System Architecture & Folder Layout
- `docs/rules.md`: Coding Guardrails & Standards
- `docs/phases.md`: Phased Build Plan
- `docs/design.md`: Visual Design System
- `docs/memory.md`: Build Progress Log
