# KarSathi — REAL Product: Complete Build Plan

> Prepared: 2 Sept 2026 · This is the master plan for building the real, workable KarSathi product (not the demo).
> **How to use this file in a new chat:** open it and say *"Follow this plan — start Phase 0."*

---

## 1. Demo vs Real Product — the clear difference

| | Demo (what we have) | Real product (what we'll build) |
|---|---|---|
| Data | Fake demo data, resets on refresh | Real data saved in a real database |
| Accounts | Demo dropdown login | Real email + password signup, forgot password |
| WhatsApp | Simulated chat bubbles | Real WhatsApp messages to real clients |
| Users | One browser at a time | Many CA firms together, each sees ONLY their own data |
| Availability | A static page | Runs 24/7 — reminders go out even when nobody is logged in |
| Payments | None | Real subscriptions collected via Razorpay |

**The demo is NOT wasted** — it becomes two things: (1) our exact design spec, and (2) a sales demo we show to CA firms ("this is what you get"). Link: https://karsathi-demo.vercel.app

---

## 2. Two parts of the project

1. **PART A — Public website (marketing):** where people discover KarSathi, see pricing, and sign up. → `karsathi.in`
2. **PART B — The real app:** where CA firms log in and actually work. → `app.karsathi.in`

One brand, one domain, two parts.

---

## 3. PART A — Public website (all pages)

| Page | What's on it |
|---|---|
| **Home** | Headline + "Start free trial" button, problem→solution, 6 feature cards, how-it-works (3 steps), live stats, screenshots, testimonials, pricing teaser, FAQ |
| **Features** | One section per feature with real screenshots: WhatsApp automation, Documents tracker, Compliance calendar, Client 360, AI assistant, Tasks & team, Invoices, Reports |
| **Pricing** | 3 plans, comparison table, FAQ, "WhatsApp at actual cost — no markup games" |
| **How it works** | Signup → Import clients from Excel → Automations run. Screenshots at every step |
| **Live Demo** | Button linking to our demo (the demo becomes a sales tool!) |
| **About** | Story, founder, mission, city, contact |
| **Blog** | SEO articles: "GST due dates 2026", "How CA firms collect documents without chasing", etc. |
| **Contact** | Form (saves to database + sends email), WhatsApp click-to-chat button, phone |
| **Login / Signup** | Doors to the real app |
| **Legal** | Privacy Policy, Terms of Service, Refund Policy, Data Security page |

Every page: mobile-first, fast, SEO meta tags, WhatsApp chat button floating on all pages.

---

## 4. PART B — The real app (complete feature list)

Built module by module — the demo already proved every screen:

1. **Accounts & Teams** — firm signup, email verification, login, forgot password; roles: **Partner** (owner) and **Article/Staff**; invite team by email. Articles see ONLY their assigned clients — same scoping we perfected in the demo (v3.10.x).
2. **Firm setup** — firm name, GSTIN, logo, WhatsApp number, working hours, reminder schedule, message tone.
3. **Clients** — add/edit clients, **Excel/CSV import & export** (400 clients in 2 minutes), client types (Individual/Proprietorship/Partnership/Pvt Ltd/LLP/HUF), assign to articles, fee status, notes, full history. Client-360 page exactly like the demo.
4. **Documents tracker** — request documents (WhatsApp + email), statuses (pending → chasing → received / escalated), auto-chase reminders (day 3, 7, 15…), client replies auto-matched, **real file upload & storage**, escalation alerts to partner, full audit trail.
5. **Compliance calendar (our engine)** — real due-date rules: GSTR-1/GSTR-3B (monthly + QRMP), TDS returns & challans, ITR (all types), ROC (AOC-4, MGT-7, DPT-3), LLP Forms 8 & 11, advance tax. Auto-builds events per client from their registrations. Calendar view + Overdue / Due<7 days chips (like demo). **This India-specific engine is our biggest moat.**
6. **WhatsApp automation** — via the official WhatsApp Business API (BSP: AiSensy or Interakt): approved message templates, document requests, reminder chains, payment follow-ups, auto-replies to common questions, Telegram alerts to the partner (like demo), message log + cost tracking.
7. **Tasks** — auto-created from deadlines + manual tasks, assign to articles, maker→checker review flow, due dates, statuses.
8. **Invoices & fees** — create invoice, send on WhatsApp/email with a payment link (Razorpay), track paid/pending/overdue, polite→firm reminder chain (the demo's invoice stages, but real).
9. **AI assistant** — answers client queries on WhatsApp, drafts replies, summarises a client's history; global search across clients/docs/deadlines (like demo).
10. **Reports & dashboard** — KPI cards (like demo), staff productivity, collection rate, automation log, export to Excel.
11. **Notifications** — in-app + email digest + Telegram for the partner.
12. **Settings** — team, message templates, automation on/off switches, billing, data export, audit log.
13. **Client portal (later phase)** — clients log in themselves, upload documents, see their deadlines, pay fees online.
14. **Mobile** — PWA first (installs like an app from the browser, works on any phone). Native app only if customers demand it.

---

## 5. Real-life user journey (what a CA firm experiences)

1. Partner finds karsathi.in → sees pricing → starts a 14-day free trial (no card)
2. Sets up firm, invites their articles
3. Imports all clients from Excel
4. System reads each client's registrations → compliance calendar builds itself
5. Partner switches automations ON
6. Clients start getting WhatsApp document requests & deadline reminders automatically
7. Articles mark documents received; partner watches the dashboard; nobody chases anybody by phone

---

## 6. Tech stack (recommended)

| What | Tool | Why | Cost |
|---|---|---|---|
| Website + app code | Next.js (React) | Industry standard, one codebase for site + app | Free |
| Database + logins + file storage | **Supabase** (Postgres, Mumbai region) | Real DB, auth, uploads, and **row-level security** = every firm can only ever see its own data | Free → $25/mo |
| Hosting | **Vercel** | Auto-deploy on every change, fast (we already know it) | Free for dev → $20/mo Pro at launch |
| WhatsApp | **AiSensy** or **Interakt** (official Meta partners) | Legal official API, INR billing, templates | ~₹999–1,500/mo + per-message |
| Payments | **Razorpay** | Subscriptions, UPI/cards/netbanking, India standard | 2% per payment, no monthly fee |
| Email | Resend / Zoho Mail | Signup mails, digests | Free to start |
| Scheduled jobs | Vercel Cron / Supabase pg_cron | Reminders fire 24/7 automatically | Included |
| Domain | karsathi.in | Brand | ~₹500–900/year |

> Why not one HTML file like the demo? A real product needs a real database, logins, file uploads and 24/7 scheduled jobs — impossible in a single static file. The single-file approach stays for the demo only.

---

## 7. Monthly running cost (realistic)

| Stage | Monthly cost (approx) |
|---|---|
| Start (first 10 firms) | **₹2,500–4,000** (Vercel Pro ₹1,800 + AiSensy ₹1,500 + rest free) |
| Growing (50 firms) | ₹8,000–12,000 (Supabase Pro + more messages) |
| WhatsApp message cost | Passed to customers at actual (~₹0.10–0.35 per utility message in India) — we never lose money on it |

---

## 8. Build phases (chat by chat)

Each chat ships something **working and deployed** — same style as the demo (v1 → v3.10.3, always live).

| Phase | Chats | What gets built & LIVE |
|---|---|---|
| **0. Foundation + public website** | 1–2 | Domain connected, logo & colors, ALL marketing pages, legal pages, SEO, analytics, waitlist → **karsathi.in goes live** |
| **1. App skeleton** | 3–5 | Signup/login, firm onboarding wizard, team + roles, clients CRUD + Excel import, basic dashboard → app.karsathi.in live |
| **2. Core work** | 6–8 | Documents tracker + real file uploads, Client 360, tasks, search, notifications |
| **3. Compliance engine** | 9–10 | Due-date rules (GST/ITR/TDS/ROC/LLP), calendar, auto-tasks — **the moat** |
| 4. **WhatsApp automation** | 11–12 | Templates (I draft all), reminder chains, auto-replies, Telegram partner alerts |
| 5. **Money** | 13–14 | Invoices + payment links, KarSathi's own Razorpay subscription billing, AI assistant v1 |
| 6. **Launch** | 15–16 | Client portal v1, PWA mobile, security hardening, final polish → **LAUNCH** 🚀 |

After launch: support chats, marketing content, small features.

---

## 9. WhatsApp — how it really works (important, read once)

- **Official API only** (unofficial WhatsApp tools = account ban risk — we never use them)
- We go through a **BSP** (Meta's official partner): AiSensy (Basic ₹1,500/mo, free tier exists) or Interakt (~₹999/mo) — both Indian, both INR billing
- One-time setup: Meta Business verification of your firm (your documents) + a phone number that is NOT already on the WhatsApp app
- Message templates need Meta approval (1–3 days each) — **I draft every template for you**
- I handle all technical connection — you only create the account (I'll give exact steps, ~15 min)

## 10. KarSathi pricing (LOCKED — from BUSINESS_PLAN.md, 30 Aug 2026)

**One all-inclusive plan** (replaces all earlier tier ideas):
- **Setup: ₹35,000 + GST** (list price) — WhatsApp API setup, Sheets+Drive wiring, dashboard, 9 automations, team training
- **AMC: ₹6,000/mo + GST** — or ₹59,999/yr prepaid (2 months free)
- **Founding deal: first 3 firms — ₹8–10k setup + 3 months AMC free**
- Running costs paid to the client's OWN accounts: WhatsApp utility ₹0.115+GST/msg (replies in 24h free), VPS ₹400–600/mo, Sheets/Telegram/AI ₹0
- Positioning vs DIY SaaS (QwikCA/Finexo/Turia): done-for-you + real conversational AI + data in the firm's own accounts

## 11. Legal & compliance (before launch)

- Privacy Policy + Terms + Refund Policy — I generate drafts; a CA/lawyer friend should review
- **DPDP Act 2023** basics: consent, delete-on-request, security disclosure page
- GST invoices to our customers (Razorpay + auto-invoice page — I build it)
- WhatsApp/Meta policy compliance (approved templates only, opt-out in every message)
- Data security page: encryption, daily backups, **data stored in India region (Mumbai)**

## 12. Domain & brand

- Name check done (Sept 2026): a "Karsathi Consultants Pvt Ltd" exists (Lucknow — a consulting company; **no software product conflict found**). Do a trademark search on ipindia.gov.in before big branding spends.
- You buy the domain (~₹500–900/yr, 10 minutes): first choice `karsathi.in`, then `.com`, backups: `karsathi.app`, `getkarsathi.in`
- Logo + color system: demo's blue/gold evolves into the real brand (I design it)

## 13. Marketing — how people will actually find us

1. **Google/SEO**: target "CA practice management software", "CA firm software with WhatsApp", "GST reminder software India" — blog posts every 2 weeks (I write with you)
2. **Google Business Profile** (free listing)
3. **CA communities**: ICAI branch events, CA WhatsApp/Telegram groups, LinkedIn posts
4. **YouTube**: 3-minute demo video (I script it, you record the screen)
5. **Pilots**: first 5 firms get it free forever → testimonials + case studies
6. **Referral**: 1 month free per referred firm

## 14. What I need from YOU (checklist before/at the next chat)

1. ☐ Buy the domain (I'll give exact steps when we start)
2. ☐ Decide pricing (or say "go with your suggestion")
3. ☐ Content for About/Contact: founder name, photo, phone, email, city, your story
4. ☐ Create these accounts (I guide each, ~15 min): Supabase (free), AiSensy (business details + card), Razorpay (PAN + bank account) — Vercel you already have
5. ☐ First pilot firm: your own firm or a friendly CA firm (for real testing)
6. ☐ Green-light the plan

## 15. How to start the next chat — copy-paste this message:

```
I have the KarSathi real product plan. First fetch and read this file:
https://raw.githubusercontent.com/anujvkarewad-cyber/karsathi-demo/main/REAL_PRODUCT_PLAN.md
Then let's start Phase 0 — foundation and the public website.
```

---

### Assets we already have (big head start)

- ✅ Full working demo = complete design spec + sales tool (v3.10.3, 546/546 tests, live on 2 URLs)
- ✅ Market & competitor research done (Turia, ERPCA, CAOA, TaxDome, Karbon…)
- ✅ Vercel + GitHub + deploy pipeline working
- ✅ WhatsApp message flows, reminder logic, scoping rules — all designed & proven in the demo

### Honest risks (and how we handle them)

| Risk | Handling |
|---|---|
| Meta verification takes time | Start it in Phase 0 (it runs in background while we build) |
| Competitor Turia is WhatsApp-first | Our moat = real India compliance engine + client portal + pricing |
| Trust in a new brand | Free pilots + testimonials + "data in India" messaging |
| I can't run things 24/7 myself | The stack (Vercel/Supabase/cron) runs by itself — no babysitting |

**Bottom line:** ~16 chats from zero to a launched, paid, working product. Every chat ends with something live, like always. 🚀
