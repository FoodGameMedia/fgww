# Food Game Media — Website Project SKILL

> **Version 1.5 | 2026-09-02 (Sydney).** v1.5 records the QAT going live end to end, retake mode (page v1.7), the three-email lifecycle and its two-phase send pipeline (new Section 18), the in-brand `/unsubscribe` page, the Supabase default-grant hazard as Hard Rule 16, and five new gotchas in Section 8. v1.4 recorded the Supabase project moving to the FoodGameMedia Pro organisation and the empty Free organisation being deleted. v1.3 recorded the Quiet Advantage Test build (Sections 14–17), corrected the brand colours and deployment method to match the live site, and added the browser-automation working pattern. v1.2 and earlier are superseded.

> **Session start confirmation line:**
> "FGM Website SKILL loaded. Ready — what are we working on?"

---

## 1. What This Project Is

Food Game Media (FGM) is a hospitality media and consulting business founded by Julian Blok, a former Goldman Sachs banker turned hospitality supply chain operator turned industry consultant. The website at **foodgamemedia.com.au** serves as the central hub for:

- Julian's consulting services (systems-led change, behavioural outcomes)
- **Food Game Weekly Wrap (FGWW)** — a hospitality industry newsletter with 6,500 subscribers, hosted and archived on the site
- **The Contrarian** — a Rory Sutherland-style opinion column on Australian hospitality, embedded from GitHub
- General brand presence and lead generation for consulting enquiries

The site is built in **custom HTML/CSS/JS** (no CMS, no framework). All content is hand-coded or Claude-assisted. Claude's job in this Project is to **maintain and update the codebase** — adding pages, fixing bugs, embedding content, and keeping everything consistent with brand and voice standards defined in this file.

---

## 2. Voice & Tone

### The Core Philosophy (from The Voice Bible)

Hospitality doesn't fail because people don't care. It fails because care is being asked to compensate for bad systems. FGM's voice takes a firm position:

- Good intentions do not scale
- Heroics are not a strategy
- Culture cannot out-run physics
- Effort cannot permanently patch broken design

The modern Food Game is played on hard mode: thinner margins, higher compliance risk, volatile costs, labour scarcity. In this environment, **systems are not optional**.

### What the Voice Sounds Like

**Dry. Direct. Insider. Never condescending.**

✅ DO — examples of correct FGM voice:
> "The Food Game doesn't care how hard you worked last Saturday."
> "Good systems don't replace hospitality. They protect it from itself."
> "Most operators aren't failing because they lack passion. They're failing because passion isn't a scheduling tool."
> "That's not a staffing problem. That's a design problem wearing a staffing costume."
> "Nobody romanticises the cool room. But nobody would run a venue without one."

❌ DON'T — what FGM never sounds like:
> "Exciting news! We're thrilled to share our innovative solution!" ← marketing fluff
> "In today's fast-paced hospitality landscape..." ← generic opener
> "As a passionate advocate for the industry..." ← self-congratulatory
> "AI will revolutionise hospitality!" ← hype without substance
> "Let's unpack that!" ← podcast-bro energy

### Voice Rules

| Rule | Detail |
|------|--------|
| Australian tone | Worldview, not slang. You notice it's Australian — you don't count the colloquialisms |
| Dry humour | Warm, never cruel. Rory Sutherland energy — counterintuitive, not cynical |
| Insider shorthand | "The Food Game" is cultural shorthand — signals you've been around |
| Short sentences | Especially for impact lines. One idea. Full stop. |
| No corporate speak | Never: "leverage", "synergy", "ecosystem", "solutions", "exciting" |
| Systems > heroes | Always frame problems as design failures, not people failures |
| AI positioning | "AI is the tool. People are the rule." Never claim AI replaces judgment |

### The "Food Game" Narrative Thread

Hospitality is affectionately called "the Food Game" throughout — not as jargon, but as cultural shorthand for the mix of chaos, skill, luck, and timing. Use it:
- In anecdotes: *"That's when you realise the Food Game doesn't care how hard you worked…"*
- To frame systemic problems: *"The Food Game is brutal to businesses that rely on memory."*
- Warmly, never cynically

### Sign-off
Julian signs all newsletter content as **JB**

---

## 3. Brand & Design Specs

### Colours

| Token | Hex | Use |
|-------|-----|-----|
| Navy (`--navy`) | `#0f1f38` | Page background, headings |
| Navy mid (`--navy-mid`) | `#1a2f52` | Mobile menu, modals, cards |
| Navy light (`--navy-light`) | `#243b6b` | Secondary surfaces |
| Pink (`--pink`) | `#f4a7b9` | Primary accent: CTAs at rest, brand mark accent, labels, links |
| Pink bright (`--pink-bright`) | `#e91e8c` | Hover states, emphasis, radio/checkbox accent |
| Pink light (`--pink-light`) | `#fce4ec` | Pale tints |
| Cream (`--cream`) | `#fdf8f5` | Light surfaces, email block backgrounds |
| Grey (`--grey`) | `#8a9ab5` | Secondary text, nav links at rest |
| Border (`--border`) | `rgba(244,167,185,0.22)` | Every hairline border and divider |
| Body text (`--text-body`) | `rgba(255,255,255,0.82)` | Body copy on navy |
| Green / Amber / Red | `#4ade80` / `#fbbf24` / `#f87171` | Status only |
| Slate (newsletter bg) | `#cdc8d9` | FGWW email body background |
| Warm Sand (alt) | `#d9cfc5` | Alternate newsletter bg |
| Dusty Rose (alt) | `#e1c8d0` | Alternate newsletter bg |
| White | `#ffffff` | Headings on navy; email body backgrounds |
| Text dark | `#111111` | Body copy on white (emails, print) |

> **Correction (v1.3):** earlier SKILL versions listed pink primary as `#c0185d`. That value appears nowhere on the live site. The live `index.html` `:root` block (main branch) is the authority; the table above reproduces it exactly. New pages copy the `:root` block from the live index verbatim rather than retyping values.

### Typography

| Use | Font | Weight |
|-----|------|--------|
| Display / headlines | Playfair Display (Google Fonts) | 700 / 900 |
| Body copy | DM Sans (Google Fonts) | 300–700 |
| Subheadings / labels | DM Sans, uppercase, letter-spacing 1–2px | 600 |
| Signature / italic | Playfair Display italic | 700 |
| Email (HTML email only) | Georgia headings, Arial body | fallbacks by design |

The live site imports Playfair Display, DM Sans and DM Serif Display from Google Fonts in one `<link>`. New pages copy that `<link>` verbatim from the live index.

### Logo Rules

- Wordmark: "Food Game" in white/navy + "Media" in pink (`#f4a7b9`; the live nav renders it via `--pink`)
- Always horizontal lockup — never stacked unless explicitly approved
- Minimum clear space: equal to cap-height on all sides
- Never recolour, stretch, or add effects to the wordmark
- Pink must always be `#f4a7b9` (with `#e91e8c` for hover/emphasis) — not approximated

### Gmail Signature

The HTML email signature is fully coded and should not be regenerated from scratch. It uses:
- FGM wordmark at top
- Navy/pink separator rules
- Julian Blok | Founder & Principal
- foodgamemedia.com.au + julian@foodgamemedia.com.au
- Italic tagline: *"The question is whether you're still playing the old game."*
- Footer links: Newsletter · Consulting · Podcast

**Third-party brand surface.** Any third-party page a customer lands on counts as brand surface and gets FGM voice. The Calendly booking page sat on Calendly's factory default text until 2026-09-02; it now carries FGM copy.

---

## 4. Technical Reference

### Stack

| Layer | Detail |
|-------|--------|
| Frontend | Custom HTML5 / CSS3 / vanilla JS — no framework |
| Hosting | Netlify, auto-deploy from GitHub `FoodGameMedia/fgww` main branch (~5 min). Site name `cute-tiramisu-8f6def`. DNS zone for foodgamemedia.com.au lives in Netlify DNS (team `julian-zaydjhk`) |
| Database + auth | Supabase project `fgm-quiet-advantage`, ref `bokqxbgnbiubwhivedvk`, region Sydney (ap-southeast-2), org **FoodGameMedia (Pro)**. See Section 14 |
| Transactional email | Cloudflare Worker `fgm-mail` → Resend API, from `test@foodgamemedia.com.au`, reply-to `julian@`. Domain verified in Resend (region Tokyo ap-northeast-1). See Section 14 |
| Content storage | GitHub (articles for The Contrarian stored as JSON/HTML) |
| Newsletter engine | FGWW — separate single-file HTML app, Claude API via Cloudflare Worker proxy |
| The Contrarian | Single-file HTML app, GitHub integration for article storage |
| Email | Gmail with custom signature |
| Newsletter platform | Substack (primary distribution) with GitHub-hosted full designs |

### Key Files & Conventions

- All pages are flat HTML files — no build step, no bundler
- CSS is either inline `<style>` blocks or a single linked stylesheet per page
- JS is vanilla — no jQuery, no React
- Images are either locally hosted or base64 embedded for portability
- The Contrarian articles are stored in GitHub and embedded/fetched at runtime

### Substack Limitation (Critical)

Substack **strips custom HTML** from newsletter bodies. The workaround is a **hybrid approach**:
- Full designed newsletter lives on GitHub (raw URL)
- Substack post contains a **teaser** + link to the full GitHub-hosted version
- Never attempt to paste complex HTML tables directly into Substack

### Claude API Integration

- Used in the FGWW newsletter engine and The Contrarian tool
- Routed through a **Cloudflare Worker proxy** — the API key is never exposed client-side
- Model: always use the latest Claude Sonnet model available
- All prompts should include explicit output format instructions

### Newsletter Archive Page (`/newsletter`)

- Served by `newsletter.html` in this repo (`FoodGameMedia/fgww`), mapped to `foodgamemedia.com.au/newsletter`.
- It loads issue data from `archive.json` at `https://foodgamemedia.github.io/fgww-engine/archive.json` (Attempt 1), falling back to parsing `archive.html` (Attempt 2), then a heuristic anchor scan (Attempt 3).
- Each issue `title` and `tagline` is injected via `innerHTML` after passing through `escapeHTML()`.
- IMPORTANT: some stored issue data is already HTML-encoded (see Section 8), so `escapeHTML()` decodes entities once via `decodeEntities()` before re-escaping. This is idempotent: plain and pre-encoded values both render correctly. Do not remove that decode step.

---

## 5. Site Structure

| Route | Status | Purpose |
|-------|--------|---------|
| `/` | Live | Home — brand intro, services overview, newsletter CTA |
| `/about` | Planned | Julian's background, philosophy, the Food Game narrative |
| `/consulting` | Planned | Services: behavioural outcomes, systems-led change |
| `/newsletter` | Live | FGWW archive: `newsletter.html` reads `archive.json` and renders past issues as cards |
| `/contrarian` | Planned | The Contrarian column — embedded from GitHub |
| `/podcast` | Placeholder | Podcast page — content TBC |
| `/contact` | Live (index section) | Netlify Forms contact form on index v1.6 |
| `/quiet-advantage` | Live, v1.7 | The Quiet Advantage Test, including retake mode at `?r=<access_token>` (Section 14) |
| `/unsubscribe` | Live, v1.0 | One-click lifecycle opt-out. Serves `?u=<access_token>`, `noindex` (Section 18) |
| `/diagnostic` | Planned | Live nine-question Diagnostic Card, pattern result (Section 15) |
| `/matrix-mate` | Planned | Matrix Mate explainer page (Section 16) |
| `/venue-by-design` | Planned | Venue by Design explainer page (Section 16) |

> **Note:** `/newsletter` is live and serving the FGWW archive (25+ issues published). Other routes below may still be in development, so confirm live status with Julian before deployment work.

---

## 6. Workflow — How Changes Are Made

### For HTML/CSS/JS edits:

1. Julian describes the change needed in the Project chat
2. Claude reads the relevant existing file (if provided) before writing anything
3. Claude makes the targeted edit — minimal blast radius, never rewrite working sections
4. Claude outputs the full updated file (not just the diff) so Julian can copy-paste or download
5. Julian commits to `main` on GitHub (upload or paste); Netlify deploys automatically in ~5 minutes. The live GitHub `main` file is always the source of truth for the next edit, never a local copy

### For new pages:

1. Start from the existing page structure — match nav, footer, font imports exactly
2. Use brand colours from Section 3 — never introduce new colours
3. Never use a CSS framework (Bootstrap, Tailwind) — vanilla CSS only
4. Test mobile breakpoints — use `@media (max-width: 768px)` as the primary breakpoint

### For newsletter issues (FGWW):

1. Use the FGWW newsletter engine (separate HTML app)
2. Design full issue in the engine → export HTML
3. Push full HTML to GitHub
4. Post teaser in Substack with link to GitHub raw URL
5. **Never** paste full newsletter HTML into Substack editor directly

### For Contrarian articles:

1. Write article in The Contrarian tool (separate HTML app)
2. Save to GitHub via the tool's GitHub integration
3. Article auto-embeds on `/contrarian` page via GitHub fetch
4. Do not manually edit article JSON in GitHub — always go through the tool

### Deployment gotchas:

- Deployment is Netlify auto-deploy from GitHub `main`; there is no FTP. Clean URLs work (`/quiet-advantage` serves `quiet-advantage.html`)
- GitHub raw URLs for embedded content can have a **5-minute cache delay** — changes may not appear immediately
- If The Contrarian embed is blank, check the GitHub raw URL is public and the filename matches exactly

---

## 7. Hard Rules

| # | Rule |
|---|------|
| 1 | Never introduce a CSS framework (Bootstrap, Tailwind, Foundation) — vanilla CSS only |
| 2 | Never use a JS framework (React, Vue, Angular) — vanilla JS only |
| 3 | Never change brand colours — use exact hex values from Section 3 |
| 4 | Never rewrite a working page from scratch — always edit the minimum required |
| 5 | Never paste complex HTML directly into Substack — use the GitHub hybrid method |
| 6 | Never expose the Claude API key client-side — always route through Cloudflare Worker |
| 7 | Never use "AI will revolutionise hospitality" or equivalent hype language |
| 8 | Never describe systems as replacing people — always "AI is the tool, people are the rule" |
| 9 | Never use corporate language: leverage, synergy, ecosystem, solutions, exciting |
| 10 | Never create a new page without matching the existing nav and footer exactly |
| 11 | Never use the pinks (`#f4a7b9`, `#e91e8c`) for body copy — accent and CTAs only |
| 14 | Never offer a direct download of any FGM instrument (Diagnostic Card PDF etc). Delivery is by email after capture, or a live online version. See Section 15 |
| 15 | The Supabase publishable key and Worker URL may live in page source (they are public by design, protected by row-level security and CORS). The Supabase secret/service_role key, database password, and Resend API key never appear in any file or page. Stronger as of v1.7: the service_role key is **never used at all** — the lifecycle scheduler runs inside Supabase on `pg_cron` and `pg_net`, so no privileged Supabase key exists outside the database |
| 12 | Never sign off newsletter content as anything other than JB |
| 13 | When rendering stored issue data (titles, taglines), decode HTML entities once before re-escaping. Some legacy data is already encoded, and escaping it again double-encodes it |
| 16 | On Supabase, `revoke ... from public` does **not** close a function off. Default privileges separately grant EXECUTE to `anon` and `authenticated`, and those grants survive. Any function that must not be reachable from a browser must name all three roles: `revoke execute on function f() from public, anon, authenticated;`. Verify with `has_function_privilege('anon', oid, 'EXECUTE')`, never by reading the migration |

---

## 8. Known Gotchas & Edge Cases

| Issue | Detail |
|-------|--------|
| Diagnostic Card PDF footer | The current `diagnostic-card.pdf` prints "Confidential" and the tagline on top of each other in the footer of both pages (rendering defect, confirmed visually). Do not email it. Rebuild pending (Section 15) |
| Supabase org placement | `fgm-quiet-advantage` lives in the **FoodGameMedia Pro** org (transferred 2026-09-01, +$10/month), so it does not pause. Never create FGM projects in a Free org: free-tier projects pause after 7 days idle and the instrument silently breaks between enquiries |
| Substack HTML stripping | Substack removes custom HTML. Always use GitHub-hosted full design + Substack teaser |
| GitHub cache delay | Raw GitHub URLs cache for ~5 mins. Embedded content won't update instantly after push |
| Contrarian embed blank | Almost always a filename mismatch or the GitHub repo is set to private |
| Newsletter bg colour | FGWW body background is Slate `#cdc8d9` — not white, not navy. Easy to accidentally reset |
| Font fallbacks | Google Fonts won't load in offline/preview environments — always set Georgia / Arial as fallbacks |
| Base64 images | Large base64 embedded images make files slow to open in editors — use sparingly outside of brand suite exports |
| Cloudflare Worker | If Claude API calls fail in the newsletter engine, check Worker is deployed and API key env var is set |
| Double-encoded titles | Legacy issue data in `archive.json` can store a title already HTML-encoded (e.g. issue #25's apostrophe saved as `&#39;`, from an older FGWW engine build). Rendering that through `escapeHTML()` double-encodes it, so the browser prints a literal `&#39;`. Fixed in `newsletter.html`: `escapeHTML()` now decodes entities once (`decodeEntities()`) before re-escaping. Keep new issue titles plain in the data source |
| RLS blocks an insert that asks for the row back | `.insert(...).select("id").single()` makes PostgREST apply the SELECT policy to the returned row. Anonymous submitters have no SELECT policy, so the whole insert aborts with `42501` and rolls back. Symptom is a 401 at the gateway and an empty table. Insert without `RETURNING` and treat the absence of an error as success |
| Supabase default grants reach every new function | `revoke ... from public` leaves the `anon` and `authenticated` grants in place (Hard Rule 16). Found in production 2026-09-02: `anon` could have called `qat_dispatch_due()` with nothing but the publishable key |
| `pg_net` is asynchronous | `net.http_post` returns a request id immediately; the response lands later in `net._http_response`. Never write a "sent" flag at dispatch time. Dispatch, then settle from the response, and write the flag only on a 200 |
| Never call a mutating function from a SELECT column list | `select ..., (select qat_dispatch_due()) as x` actually dispatches. It cost a duplicate send during testing |
| Supabase SQL editor renders blank in fresh tabs under load | `document.body.innerText.length` comes back 0 and hard navigation does not fix it. What does: find a tab where the dashboard is already rendered and click through to the SQL editor in the left sidebar, which routes inside the SPA |

---

## 9. Integrations Reference

| Service | Purpose | Credential pattern | Notes |
|---------|---------|-------------------|-------|
| Anthropic Claude API | Powers FGWW engine + The Contrarian | `sk-ant-...` stored in Cloudflare Worker env var `ANTHROPIC_API_KEY` | Never client-side |
| Cloudflare Workers | API proxy for Claude | Worker URL pattern: `https://[worker-name].[account].workers.dev` | Deployed separately |
| GitHub | Article storage for The Contrarian + full newsletter hosting | Personal access token for write operations | Repo must be public for embed to work |
| Substack | Newsletter distribution | Julian's Substack account | HTML stripped — teaser only |
| Gmail | Email with custom HTML signature | julian@foodgamemedia.com.au | Signature installed via Email Signature Rescue Chrome extension |
| Supabase | Test submissions + customer accounts | Publishable key in page (public); secret key never used client-side | Project ref `bokqxbgnbiubwhivedvk`; RLS on every table |
| Resend | Transactional email sending | `RESEND_API_KEY` as encrypted secret in Worker `fgm-mail` (key name `fgm-mail-worker`, sending-only) | Domain foodgamemedia.com.au verified: DKIM `resend._domainkey`, MX + SPF on `send`, DMARC `_dmarc` p=none, all in Netlify DNS |
| Cloudflare Worker `fgm-mail` | Email dispatch for QAT result (live), card delivery and diagnostic result (scaffolded) | No key in code; CORS locked to foodgamemedia.com.au and www | `https://fgm-mail.julian-68d.workers.dev` |
| Netlify Forms | Contact form capture | none | index v1.6 |
| Cloudflare Worker `fgm-lifecycle` | The three anniversary emails and the unsubscribe fallback | `RESEND_API_KEY` and `DISPATCH_SECRET` as Worker secrets; `SUPABASE_URL`, `SUPABASE_ANON_KEY`, `UNSUB_BASE` as plain text | `POST /send` is gated on an `x-fgm-dispatch` header, because CORS does not stop a server-to-server call. Secret shared with the Supabase Vault entry `fgm_dispatch_secret` |
| Calendly | The free 30-min discovery call | none | One event, "Free 30-min Call". Free plan: one active event type and **no webhooks**, so a booking cannot be detected programmatically |

Resend holds a second sending key, `fgm-lifecycle`, alongside the `fgm-mail` one. The dead `fgm-mail-worker` key was deleted 2026-09-02.

---

## 10. Access Details

> ⚠️ Populate this section with real credentials in your private Claude Project — do not commit to public GitHub.

| Item | Value |
|------|-------|
| Site domain | foodgamemedia.com.au |
| Primary email | julian@foodgamemedia.com.au |
| GitHub repo (website + SKILL) | https://github.com/FoodGameMedia/fgww |
| GitHub repo (Contrarian) | https://github.com/FoodGameMedia/fgww (confirm if separate) |
| Cloudflare Worker (Claude proxy) | young-fog-3045fgww-proxy.julian-68d.workers.dev |
| Cloudflare Worker (mail) | fgm-mail.julian-68d.workers.dev (account id `68d5682ce8e4949039378baad0c0b45c`) |
| Supabase project | `fgm-quiet-advantage`, ref `bokqxbgnbiubwhivedvk`, `https://bokqxbgnbiubwhivedvk.supabase.co`, org FoodGameMedia (Pro). Other orgs on the account: The95Platform (Pro) |
| Netlify team / site | team `julian-zaydjhk`; site `cute-tiramisu-8f6def` serves foodgamemedia.com.au |
| Resend team | `foodgamemedia` (also holds venuebydesign.com.au verified, matrixmate.com.au not started) |
| Anthropic API key | `sk-ant-...` [stored in Worker env var — never paste here] |
| Substack URL | https://foodgameweeklywrap.substack.com/ |
| Cloudflare Worker (lifecycle) | fgm-lifecycle.julian-68d.workers.dev |
| Calendly | calendly.com/julian-foodgamemedia |
| Supabase Vault secret | `fgm_dispatch_secret`, shared with the lifecycle Worker |
| Supabase extensions enabled | `pg_cron` 1.6.4, `pg_net` 0.20.4 on `fgm-quiet-advantage` |

---

## 11. Content & Feature Status

| Feature | Status | Notes |
|---------|--------|-------|
| Home page | Live | index v1.6 on Netlify; Netlify Forms contact form |
| Quiet Advantage Test | Live and working end to end | Page v1.7 on main; result stored, result email delivered, retake mode verified on production 2026-09-02. Section 14 |
| QAT lifecycle emails | Built and scheduled | Migrations 001–003 applied. `qat-dispatch` Tuesdays 22:00 UTC, `qat-settle` hourly at :07. Section 18 |
| QAT retake mode | Live | `/quiet-advantage?r=<access_token>`. Landing, comparison, help capture and call CTA all verified against production |
| Unsubscribe | Live | `unsubscribe.html` v1.0, one click, idempotent |
| Diagnostic Card (current PDF) | Live but flawed | Ungated direct download on index; footer defect; eight questions. Being replaced (Section 15) |
| Matrix Mate / Venue by Design pages | Planned | Section 16 |
| About page | Not confirmed live | Planned |
| Consulting page | Not confirmed live | Planned |
| FGWW newsletter archive | Live | `newsletter.html` reads `archive.json`; issues also on Substack + GitHub |
| The Contrarian embed | Planned | Tool exists, embed needs wiring to `/contrarian` page |
| Podcast page | Placeholder only | Content TBC |
| Contact page | Not confirmed live | Planned |
| Gmail signature | Live | Installed via Email Signature Rescue |
| FGWW newsletter engine | Live (separate app) | Single-file HTML, Claude API via Cloudflare Worker |
| The Contrarian tool | Live (separate app) | Single-file HTML, GitHub integration |

---

## 12. Self-Improvement Protocol

At the end of every session where something new was discovered, built, or fixed, Claude must flag any SKILL.md updates needed:

> "**SKILL.md update needed:** [Section X] — [what changed and why]"

Examples of things that must trigger an update flag:
- A new page goes live → update Section 5
- A bug is discovered and fixed → add to Section 8
- A new integration is set up → update Section 9
- A credential or URL is confirmed → update Section 10
- A new hard rule is established → add to Section 7
- Voice or brand spec changes → update Sections 2 or 3

Julian confirms the update, then adds it to the SKILL.md in GitHub.

---

## 13. How to Use This Skill File

### Where it lives
This file lives at:
```
https://raw.githubusercontent.com/FoodGameMedia/fgww/main/FGM_WEBSITE_SKILL.md
```

`raw.githubusercontent.com` is reachable from the Claude Project's bash tool (confirmed 2026-08-24, `curl` returns 200). Fetch it there. If a session's tooling cannot reach it, the project-knowledge copy is the fallback, and this file's version line says which is newer.

### Session start
Every conversation in this Claude Project begins with Claude fetching the SKILL.md from its GitHub raw URL, reading it in full, then confirming with exactly one line:

> "FGM Website SKILL loaded. Ready — what are we working on?"

Claude then waits. It does not summarise the SKILL, ask clarifying questions unprompted, or offer suggestions before Julian states what he needs.

### What Claude must never do
- Never skip fetching the SKILL.md at session start
- Never assume brand colours, voice, or structure from memory — always reference this file
- Never rewrite a working page from scratch without explicit instruction
- Never introduce dependencies (frameworks, libraries) not already in the codebase
- Never produce content that violates the voice rules in Section 2

---

## 14. The Quiet Advantage Test (QAT) — architecture

Approved documents (all in the Project): `QAT_Instrument_Spec_v1.0`, `QAT_Copy_Deck_v1.1`, `QAT_Supabase_Setup_v1.0`, `QAT_Email_Setup_v1.0`. Every word of page and email copy is in the deck; nothing is changed without a new approved deck version.

**Instrument.** Five questions from the closing chapter of *The Food Game*, four-point answers scored 4→1, total out of 20. Bands: Held 18–20, Built with gaps 14–17, Carried 9–13, Running on adrenaline 5–8. Result = the two lowest-scoring questions; tie-break order Q2, Q3, Q4, Q1, Q5. Each maps to a fixed diagnosis block and first default.

**Page** `quiet-advantage.html` (v1.3): flat HTML, inherits the live index design system verbatim. Flow: intro → five questions → details form → on-screen result → optional account creation (after the result, never before) → done. Privacy statement is an on-page modal. Config block near the bottom of the module script:
```
SUPABASE_URL: "https://bokqxbgnbiubwhivedvk.supabase.co"
SUPABASE_ANON_KEY: "sb_publishable_..."   (publishable key, public by design)
EMAIL_WORKER_URL: "https://fgm-mail.julian-68d.workers.dev"
```
Fields: first/last name, email, mobile (AU), venue name, venue type, role, street address, suburb, state, postcode, employees band, covers band, weekly turnover band (with Prefer not to say), FGWW opt-in, privacy consent. Honeypot field `company`.

**Supabase.** Org FoodGameMedia (Pro), so the project never pauses. Table `public.qat_submissions` (all fields above + `answers jsonb`, `score int 5–20`, `band`, `priorities jsonb`, `created_at`). RLS on. Policies: insert for anon+authenticated with `privacy_consent = true`; select for authenticated where `email = auth.jwt()->>'email'`; no update/delete from the browser. Index on `email` (the canonical join key for the future Xenvia customer graph). Auth: email+password, Confirm email OFF. Julian reads everything in Table Editor; export CSV.

**Email.** Page POSTs `{to, first_name, venue_name, score, priorities}` to the Worker. The Worker owns all copy, derives the band from the score itself, validates every field, escapes names, and sends via Resend from `Food Game Media <test@foodgamemedia.com.au>`, reply-to `julian@`. Subject: `Your Quiet Advantage result: [Band]`. Table-based inline-styled HTML. Handlers `card_delivery` and `dc_result` are scaffolded (return 503) for Sections 15 and 16 work.

**Live test procedure** (before pointing anyone at it): incognito → `/quiet-advantage` → real email, venue `QAT TEST — DELETE` → confirm (a) on-screen result with "on its way to your inbox", (b) email received, (c) row in `qat_submissions`, (d) reply-to `julian@`. Delete the test row and any test user.

**Decisions on record.** Pattern of the funnel: QAT is the self-serve instrument (score + two fixes); the Diagnostic Card is the guided one (pattern + consult). Accounts are the seed of the group customer record; consent is scoped to Food Game Media only; cross-product sharing (Matrix Mate, Xenvia, Venue by Design) requires its own explicit, revocable consent when the hub exists.

**Amendments, 2026-09-02.**

- The page inserts **without** `RETURNING` and sends no `submission_id` to the Worker (Section 8).
- `fgm-mail` sends as `Food Game Media <Julian@foodgamemedia.com.au>`, reply-to `julian@`. The old `test@` sender is gone; it was a spam-filter liability on a new domain.
- The result email lands in Gmail's **Updates** tab, not spam. Acceptable and not worth chasing.
- Retake mode is v1.7: `?r=<access_token>` renders the previous answers read-only, never preselected, skips the details form, and ends on a movement comparison, one free-text question and the call. All reads and writes go through the security-definer functions, so the page never touches a table and never sees a contact field. A retake sends no result email, because the page cannot obtain the address by design.
- The comparison line says "Last time you scored…", not "Three months ago…", because a retake can land at any interval.

---

## 15. Diagnostic Card — decisions and pending rebuild

- **No direct download, ever** (Hard Rule 14). Two paths only: do the diagnostic live at `/diagnostic` with the result emailed, or have the printable card emailed after a short capture (first name, email, venue name, FGWW opt-in, consent). `diagnostic-card.pdf` is to be deleted from the repo so the public URL dies; the rebuilt PDF is bundled inside the Worker as base64 and sent as an attachment.
- **Nine questions, not eight.** The Signals domain (03 on the website) had no question. Approved Q5 — SIGNALS: *"How often do your staff have to verbally correct a guest — explaining how ordering works, what the venue does not do, or where they should be?"* Answers: Rarely — the room teaches the rules before anyone has to speak / Occasionally — a few predictable corrections each service / Regularly — the same explanations, every shift, to guests who could not have known / Constantly — correcting guests is simply part of the job here. New order: Q1–2 Throughput, Q3–4 Defaults, Q5 Signals, Q6 People Load, Q7 Operational Memory, Q8–9 Calm Index. Framing everywhere: "Nine questions. Five minutes. Six domains. One clear picture."
- **PDF rebuild required** (footer defect, Section 8) with the ninth question; presented rendered for visual approval before any email goes out.
- **Live version shows pattern, not prescription:** the answers mapped across the domains, where the load concentrates, then the free thirty-minute consult as the interpretation step. Answers ranked 1–4 internally for storage and retakes; no numeric score shown. Result page says the card reads six of the seven domains Venue by Design tracks weekly (the difference is the upsell, not an inconsistency).
- Supabase tables to add: `dc_submissions`, `card_downloads`; Worker types `dc_result`, `card_delivery`.

---

## 16. Platform pages — Matrix Mate and Venue by Design

Each gets its **own full page** (`matrix-mate.html`, `venue-by-design.html`) plus a Platforms section on the index linking through. CTAs mirror each platform's own site exactly: Matrix Mate → **Book a Demo** at matrixmate.com.au; Venue by Design → **Book your Deep Diagnostic** at venuebydesign.com.au. Never "sign up".

**Matrix Mate terminology (use precisely):** category name *Intelligent Equipment Management*; **MM8** (the AI agent, included every tier from day one); **IUM** and **IUM record** (proper noun, never expanded); **IUM Tag** (durable QR, no app, 4-digit PIN); human-verified **OEM record**; **Marketplace** (multiple bids, fault history attached); **Pre-Sale Audit**; one fee per IUM, unlimited users. Approved category line: *"Matrix Mate defined the category — intelligent equipment management with an AI agent on every unit — a category with no incumbent to displace."* Never "no competitors" (contradicts The Calm Venue's own disclosure that a category exists).

**Venue by Design terminology:** **Calm Index** (out of 10, "not a grade, it is a map"); **seven domains** (Throughput, Pacing, Defaults, People Load, Signals, Endings, Operational Memory); states Structural Risk 0–4 / Functional but Fragile 5–7 / Designed for Calm 8–10; **Deep Diagnostic** (forty questions, ninety-day design prescription, sixty-minute walkthrough); **Venue Pulse** (weekly loop). Tagline shared with the book: "Calm is not a personality trait. It is a design outcome."

Copy is drafted from the manuscripts and the live sites, presented for approval before any page is built. One index edit carries the card rework, the Platforms section and the QAT homepage link together.

---

## 17. Browser automation (Claude in Chrome) — working pattern

Learned 2026-08-25/27 driving Resend, Netlify, Cloudflare, Supabase and GitHub.

- **Hard limits, regardless of instruction:** Claude never creates accounts, never types passwords to sign in, never copies or pastes API keys, secrets or tokens into any field, never solves CAPTCHAs. Julian does sign-ins and secret pastes; Claude does everything around them.
- **Reliable inputs:** `find` (natural-language element search) → click by `ref`; `form_input` for fields and selects; verify every save with `get_page_text` or a screenshot. Coordinate clicks on modals are unreliable (modals move).
- **When rendering breaks** (viewport reports 0x0, screenshots error, SPA buttons do not fire): the DOM channel usually still works. Use the platform's own API from the page context via `javascript_exec` with the signed-in session (worked first time for the Cloudflare Worker deploy: `PUT /api/v4/accounts/{id}/workers/scripts/{name}` multipart; `POST .../subdomain`). Supabase's dashboard API needs a bearer token Claude must not extract, so Supabase is driven through the UI (Monaco editors accept `monaco.editor.getEditors()[0].setValue(...)`; typed keystrokes do not land).
- **Large payloads:** never hand-transcribe more than ~20KB of base64 into a call; corruption is likely. Chunk to ~6KB with length/edge verification per chunk, or hand the file to Julian for a 60-second upload.
- **Connection drops** every few minutes under load and recover minutes later; each site also needs its own extension permission grant on first visit. Keep Chrome foregrounded; save server-side progress before each step; report exact state on every drop so nothing is redone.
- Every browser-driven build ends with the on-prod vs pending ledger.

---

## 18. The QAT lifecycle

Three emails, then stop. Month one and month two each carry an anchor, a book excerpt and one small move, chosen from that person's own priority questions. Month three invites a retake. **A retake restarts the sequence** (decision, 2026-09-02).

Excerpt selection is derived by hashing `access_token`, so a retake — which mints a new token — does not repeat a passage.

Sends run Wednesday morning Sydney (`0 22 * * 2` UTC), never Monday, because the Wrap goes out then. Settle runs hourly at :07.

The pipeline is two-phase because `pg_net` is asynchronous: `qat_dispatch_due()` posts and logs the request id and sets no flags; `qat_settle_sends()` reads the response and writes `mN_sent_at` only on a 200. A failed send stays unsent and is retried, rather than being silently recorded as delivered.

Ordering is enforced: m2 requires `m1_sent_at`, m3 requires `m2_sent_at`. A backlog therefore drains one email per week per person, in order, rather than arriving as a pile.

Unsubscribe is one click, no confirmation, idempotent, and served from `/unsubscribe` in brand — never a `workers.dev` URL.

Authority documents, all approved: `QAT_Lifecycle_Spec_v1.1`, `QAT_Copy_Deck_v1.4`, `QAT_Excerpt_Library_v1.0`, `QAT_Send_Pipeline_v1.0`.
