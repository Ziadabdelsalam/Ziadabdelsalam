# GitHub Profile as Client Portfolio — Design Spec

**Date:** 2026-07-02
**Owner:** Ziad Ahmed (`@Ziadabdelsalam`)
**Goal:** Turn the GitHub profile into a portfolio that convinces **freelance AI clients** that Ziad ships real LLM products, and pushes them to hire via Upwork or email.

---

## 1. Context & Constraints

- **Audience:** Freelance AI clients (paying, contract work). Not recruiters, not investors.
- **Desired action:** Contact Ziad → **Upwork** (`https://www.upwork.com/freelancers/~01ed61069bdf946adc`) or **email** (`ziadabdelsalam143@gmail.com`).
- **Specialty:** AI Engineer — LangChain, LangGraph, RAG, agents, LLM fine-tuning, LLM product delivery.
- **Private-work strategy:** Hybrid. Private repos **stay private** (not open-sourced). Best work is surfaced via **case studies in the profile README**, not by exposing code.
- **WIP handling:** Feature ALL products, labeled honestly. WIP framed as *"in active development"* with real stack detail so it reads as capability, not abandonment.
- **Visual style:** Clean & professional. Tasteful badges, one stats card. No streak/trophy/emoji spam.
- **No LinkedIn, no personal website** currently.

### Known reality (from reading repos on 2026-07-02)
- No profile README repo exists yet (`Ziadabdelsalam/Ziadabdelsalam` → 404). Biggest quick win.
- `zabotique` — shipped, **live** (`https://zabotique.vercel.app`), clean README. The hero.
- `invy.ai` (aka "gaudia") — AI event invitations. Self-labeled *"side project, ~7 weekends to ship."* Presentable, WIP.
- `mentra.ai` — multi-tenant agent platform, *"Phase 1 in progress."* WIP.
- `mentra.studio` — Eloquent-platform rebuild (Go). WIP.
- `agentic-rag`, `archimest`, `menkra.ai` — empty READMEs / no description.
- Strong public AI repos with descriptions: `txt-sql-langchain-agent`, `deal-brief`, `Dahab-chatbot`.
- Mostly 0 stars → appeal must come from **presentation**, not social proof.
- Old 2023 forks/coursework (`privateGPT`, `klaam`, `Arabic-OCR`, `scikit-llm` fork, Udacity repos) dilute if surfaced.

---

## 2. Deliverables

### A. Profile README (`Ziadabdelsalam/Ziadabdelsalam` repo — NEW)
Markdown rendered at the top of the GitHub profile. Sections top → bottom:

1. **Header**
   - Name + positioning line: *"AI Engineer — I build & ship LLM products: RAG, agents, fine-tuning."*
   - Two CTA badges at the very top: **Hire me on Upwork** + **Email**.
   - "Available for freelance AI work" status line.
2. **Intro** — 2–3 sentences: what he does, who he helps, how to engage.
3. **Featured Work** — case-study cards, credibility-first order, honest status labels:
   | Project | Status | Link treatment | Stack highlights |
   |---|---|---|---|
   | `zabotique` | 🟢 Live | Live demo link | Next.js 16, Supabase, Lemon Squeezy, Resend |
   | `gaudia` (`invy.ai`) | 🔵 In active development | "code private — walkthrough on request" | Next 16, Vercel AI SDK 6, Claude Sonnet |
   | `mentra` (`mentra.ai`/`.studio`) | 🔵 In active development | "code private — walkthrough on request" | FastAPI + Go, agents-as-tools, multi-tenant |
   | `agentic-rag` | 🔵 R&D | "code private — walkthrough on request" | Infra-agnostic agentic RAG |
   | `txt-sql-langchain-agent` | 🟢 Public | Repo link | LangChain, FastAPI, Streamlit, LangSmith |
   | `deal-brief` | 🟢 Public | Repo link | LLM extraction pipeline, React UI |
   | `Dahab-chatbot` | 🟢 Public | Repo link | Fine-tuned LLM on Reddit data |
4. **Tech stack** — grouped badges:
   - *LLM/AI:* LangChain, LangGraph, Vercel AI SDK, Claude, RAG, fine-tuning
   - *Backend:* Python / FastAPI, Go
   - *Frontend:* Next.js, TypeScript, Tailwind
   - *Data/Infra:* Postgres, pgvector, Supabase, Docker
5. **GitHub stats card** — one github-readme-stats card, clean theme. No streak/trophy.
6. **Contact / CTA footer** — "Available for freelance AI work" → Upwork button + email.

### B. Repo Hygiene
- **Pin 6 public repos** (manual — no API): `txt-sql-langchain-agent`, `deal-brief`, `Dahab-chatbot`, `RAG-Chatbot`, `Conversational-Assistant`, `LangGraph-Tutorial`. Pins only show public repos; private products are covered by the README.
- **Add descriptions** to public repos missing them (blank descriptions read as abandoned): `RAG-Chatbot`, `Conversational-Assistant`, `Conversational-Assistant-APK`, `LangGraph-Tutorial`, `archimest`, `brain-boost-ai`, `LangChainApp`, `ArabicOCR-Deeplearning`.
- **Profile bio + links** (manual): bio → "AI Engineer • building LLM products • available for freelance". Add Upwork link to profile social links.
- **Old forks/coursework:** GitHub hides forks by default; leave as-is since pins are curated. No archiving unless requested later.

### C. Assets
- One screenshot of the live `zabotique` site for the hero card (optional; captured via browser tool). Kept minimal to preserve the clean style.

---

## 3. What I do vs. what the user does

| Action | Who | Method |
|---|---|---|
| Create profile README repo + content | Claude | git + `gh repo create` / push |
| Edit public repo descriptions | Claude | `gh repo edit` |
| Screenshot zabotique | Claude | browser tool |
| Pin repos | **User** | GitHub UI (no API) — Claude provides exact click-list |
| Edit profile bio/social links | **User** | GitHub UI (no API) — Claude provides exact text to paste |

---

## 4. Success Criteria

- Visiting `github.com/Ziadabdelsalam` shows a polished README that, within ~10 seconds, tells a client: *AI Engineer, ships LLM products, available for hire, click here.*
- At least one **live, working** product visible (zabotique).
- Every featured project has a clear what/stack/status; no blank or confusing entries.
- Two obvious CTAs (Upwork + email) above the fold.
- Pinned repos are all relevant AI work with real descriptions — no forks/coursework noise.

---

## 5. Out of Scope (YAGNI)

- Making any private repo public.
- Building a separate personal website.
- Star-farming / social engagement graphics (streaks, trophies).
- Rewriting any project's actual code or READMEs beyond descriptions.
- Archiving/deleting old repos (optional future cleanup).
