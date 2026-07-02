# GitHub Profile Portfolio Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a clean, professional GitHub profile README + repo hygiene that sells Ziad (`@Ziadabdelsalam`) as a freelance AI engineer and drives clients to Upwork/email.

**Architecture:** A new special repo `Ziadabdelsalam/Ziadabdelsalam` holds `README.md`, which GitHub renders at the top of the profile. Public repo descriptions are set via `gh repo edit`. Pins and profile bio are manual (no GitHub API) — delivered as a click-list. One screenshot of the live zabotique site anchors the hero.

**Tech Stack:** Markdown, shields.io badges, github-readme-stats, `gh` CLI, git, Playwright (screenshot).

**Verification model:** No unit tests. Each task verifies via render check, `gh api` confirmation, or visual inspection.

**Facts (do not re-derive):**
- Username: `Ziadabdelsalam` (case matters for the special repo).
- Commit identity: `git -c user.name='Ziad Ahmed' -c user.email='ziadabdelsalam143@gmail.com'`.
- CTA email: `ziadabdelsalam143@gmail.com` · Upwork: `https://www.upwork.com/freelancers/~01ed61069bdf946adc`
- Live product: `https://zabotique.vercel.app`
- Repo dir already exists + git-inited at `Ziadabdelsalam/` with the spec committed.

---

### Task 1: Capture zabotique hero screenshot

**Files:**
- Create: `Ziadabdelsalam/assets/zabotique.png`

**Step 1:** Use the Playwright browser tool: navigate to `https://zabotique.vercel.app`, set viewport ~1280×800, wait for load, screenshot to `assets/zabotique.png`.

**Step 2 (verify):** `ls -la Ziadabdelsalam/assets/zabotique.png` → file exists, non-zero size.

**Step 3 (fallback):** If the site is down or screenshot fails, skip the image and use a text-only hero card. Do NOT block the plan on this.

**Step 4: Commit**
```bash
git add assets/zabotique.png
git commit -m "assets: add zabotique hero screenshot"
```

---

### Task 2: Write the profile README

**Files:**
- Create: `Ziadabdelsalam/README.md`

**Step 1:** Write `README.md` with these sections (clean & professional; badges via shields.io `for-the-badge` style, muted colors):

1. **Header block**
   - `# Ziad Ahmed` + subtitle *"AI Engineer — I build & ship LLM products: RAG, agents, and fine-tuning."*
   - CTA badge row (top, above the fold): **Hire me on Upwork** (links to Upwork URL) · **Email** (mailto). Optional "available for freelance" shields badge.
2. **Intro** — 2–3 sentences: turns AI/LLM ideas into shipped products; helps startups/founders build RAG systems, agents, and custom LLM apps; open to freelance work.
3. **Featured Work** — one subsection per project, credibility-first order. Each: bold name (linked), one-line what, `Stack:` line, status badge (🟢 Live / 🔵 In active development / 🔵 R&D). Order:
   - **Zabotique** 🟢 Live → link `https://zabotique.vercel.app`. Embed `assets/zabotique.png` if it exists.
   - **Gaudia** 🔵 In active development — AI-generated animated event invitations. *code private — walkthrough on request.*
   - **Mentra** 🔵 In active development — multi-tenant AI agent platform (APIs-as-tools for a Claude agent). *code private — walkthrough on request.*
   - **Agentic RAG** 🔵 R&D — infrastructure-agnostic agentic RAG platform. *code private — walkthrough on request.*
   - **txt-sql-langchain-agent** 🟢 Public → repo link. English→SQL analytics agent.
   - **deal-brief** 🟢 Public → repo link. LLM deal-extraction pipeline + React UI.
   - **Dahab-chatbot** 🟢 Public → repo link. Fine-tuned LLM on Reddit data.
4. **Tech stack** — grouped shields badges: *LLM/AI* (LangChain, LangGraph, Vercel AI SDK, Claude, RAG, fine-tuning) · *Backend* (Python, FastAPI, Go) · *Frontend* (Next.js, TypeScript, Tailwind) · *Data/Infra* (PostgreSQL, pgvector, Supabase, Docker).
5. **GitHub stats** — one card:
   `![stats](https://github-readme-stats.vercel.app/api?username=Ziadabdelsalam&show_icons=true&hide_border=true&theme=graywhite&count_private=true)`
   Top-languages card optional (`hide=jupyter notebook` if noisy). No streak/trophy.
6. **Contact footer** — "📬 Available for freelance AI work" → Upwork button + email.

**Step 2 (verify):** Render check — open the file, confirm all links are absolute, no broken markdown, image path matches Task 1 output (or removed if skipped). Confirm both CTAs (Upwork + email) appear in the header AND footer.

**Step 3 (verify):** Grep for placeholders: `grep -nE 'TODO|TBD|XXX|\[link\]|example\.com' README.md` → no matches.

**Step 4: Commit**
```bash
git add README.md
git commit -m "feat: add profile README portfolio"
```

---

### Task 3: Publish the profile repo to GitHub

**Step 1:** Create the special public repo and push:
```bash
cd Ziadabdelsalam
gh repo create Ziadabdelsalam/Ziadabdelsalam --public --source . --remote origin --push
```
(If the repo somehow already exists: `git remote add origin https://github.com/Ziadabdelsalam/Ziadabdelsalam.git && git push -u origin main`.)

**Step 2 (verify):** `gh api repos/Ziadabdelsalam/Ziadabdelsalam --jq '.name, .visibility'` → `Ziadabdelsalam`, `public`.

**Step 3 (verify):** `gh api repos/Ziadabdelsalam/Ziadabdelsalam/readme --jq '.name'` → `README.md`. This confirms the profile README is live.

---

### Task 4: Set public repo descriptions

**Files:** none local — remote metadata via `gh`.

**Step 1:** For each public repo lacking a good description, set one with `gh repo edit Ziadabdelsalam/<repo> --description "<text>"`. Targets + copy:
- `RAG-Chatbot` → "Retrieval-augmented chatbot over custom documents (Python, LangChain)."
- `Conversational-Assistant` → "Conversational AI assistant backend (Python, LLM)."
- `Conversational-Assistant-APK` → "Mobile build of the Conversational Assistant (TypeScript/React Native)."
- `LangGraph-Tutorial` → "Hands-on LangGraph examples for building stateful LLM agents."
- `deal-brief` → keep existing if present, else "LLM-powered deal-text extraction pipeline with a React UI."
- `Dahab-chatbot` → keep existing ("Fine tuned llm on Dahab sub reddit").
- `archimest` (public) → set only if it has real content; otherwise leave and do NOT pin. Decide by `gh api repos/Ziadabdelsalam/archimest/readme` returning content.
- `brain-boost-ai` → "AI-powered learning/quiz app (TypeScript)." — only if content warrants.
- `LangChainApp` → "Early LangChain experiments (Python)." — optional, low priority.

Skip any repo the user later says is client-owned. Do NOT touch forks or 2023 coursework.

**Step 2 (verify):** For each edited repo: `gh api repos/Ziadabdelsalam/<repo> --jq '.description'` → returns the new text.

**Step 3:** No commit (remote metadata only). Log what changed.

---

### Task 5: Deliver manual click-list (pins + bio)

GitHub has no API for pinned repos or profile bio/social links — the user does these. Produce an exact, copy-paste click-list:

**Pins** (Profile → "Customize your pins"): select exactly these 6 public repos, in order:
1. `txt-sql-langchain-agent`
2. `deal-brief`
3. `Dahab-chatbot`
4. `RAG-Chatbot`
5. `Conversational-Assistant`
6. `LangGraph-Tutorial`
(Swap any that turn out thin for `agentic-rag`'s public equivalent — but private repos cannot be pinned publicly.)

**Bio** (Settings → Public profile):
- Bio: `AI Engineer • building & shipping LLM products • available for freelance`
- Add social link: the Upwork URL.
- Confirm "AI Engineer" headline stays.

**Step (verify):** Ask the user to confirm pins + bio are set, then visually confirm `github.com/Ziadabdelsalam` renders README + pins + CTAs above the fold.

---

## Definition of Done

- `github.com/Ziadabdelsalam` shows the new README with Upwork + email CTAs above the fold.
- zabotique live link present (+ screenshot if captured).
- All 7 featured projects render with clear what/stack/status.
- Public repo descriptions filled; no blank AI repos in the pinned set.
- User has the click-list for pins + bio.
