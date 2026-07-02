# Case Study — Zabotique

**A boutique of digital wedding & engagement invitations.**
Live: **[zabotique.vercel.app](https://zabotique.vercel.app)** · Bilingual Arabic + English

<a href="https://zabotique.vercel.app"><img src="../assets/zabotique.png" alt="Zabotique" width="720"/></a>

---

## The problem

Couples want a beautiful, shareable digital invitation without hiring a designer or wrestling with generic template sites. Existing options are either bland, English-only (a real gap for Arabic-speaking couples), or force a monthly subscription for a one-time event.

## What I built

A self-serve product where a couple:

1. **Picks a template** from a curated boutique,
2. **Customizes** names, dates, and details (Arabic or English, right-to-left aware),
3. **Pays once**, and
4. **Shares a hosted link** their guests can open for 30 days.

Plus a **custom-commission** path for couples who want a bespoke design rather than a template.

## Key decisions (and why)

| Decision | Why it mattered |
|---|---|
| **Lemon Squeezy as Merchant of Record** for payments | Handles global tax/VAT and acts as the seller of record — so the product could take international payments **without needing a registered business entity in Egypt**. A pragmatic unblock, not just a tech choice. |
| **Bilingual Arabic + English with RTL layout** | The underserved segment. Correct RTL typography and mirrored layouts are the difference between "localized" and "an afterthought." |
| **Pay-once, 30-day hosted link** | Matches how people actually think about a single event — no subscription friction. |
| **Graceful-degradation architecture** | Public pages (`/`, template preview, custom request) render even when backend services aren't configured — the data proxy no-ops when env is missing. Keeps the marketing surface fast and always-up. |
| **Supabase magic-link auth** | Passwordless — lower friction for non-technical users creating one invitation. |

## Architecture

- **Frontend/App:** Next.js 16 (App Router, Turbopack) on Vercel.
- **Data & Auth:** Supabase — Postgres, magic-link Auth, and Storage for template assets.
- **Payments:** Lemon Squeezy (Merchant of Record).
- **Email:** Resend — magic-link and commission-notification emails.

```
Guest link  ─▶  Next.js (Vercel)  ─▶  Supabase (Postgres + Storage)
Customize   ─▶  Next.js server actions ─▶ Supabase
Checkout    ─▶  Lemon Squeezy  ─▶  webhook ─▶ Supabase
Notifications ─▶ Resend
```

## My role

Sole designer and engineer — product scope, template system, bilingual UX, payments/webhooks, auth, and deployment.

## Status

Shipped and live. The public product is running at [zabotique.vercel.app](https://zabotique.vercel.app); the source is private. **Happy to walk through the code and architecture on a call.**

---

*Want something similar — a polished, self-serve web product with payments and multi-language support? [Hire me on Upwork](https://www.upwork.com/freelancers/~01ed61069bdf946adc) or email [ziadabdelsalam143@gmail.com](mailto:ziadabdelsalam143@gmail.com).*
