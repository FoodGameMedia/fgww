# Food Game Media — Website Project SKILL

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
| Navy primary | `#0f1f38` | Headings, heavy UI elements |
| Navy secondary | `#1a2f4e` | Backgrounds, cards |
| Pink primary | `#c0185d` | Accent, CTAs, links |
| Pink light | `#f4a7b9` | Borders, dividers |
| Pink pale | `#f4e8ec` | Section backgrounds |
| Slate (newsletter bg) | `#cdc8d9` | FGWW email body background |
| Warm Sand (alt) | `#d9cfc5` | Alternate newsletter bg |
| Dusty Rose (alt) | `#e1c8d0` | Alternate newsletter bg |
| White | `#ffffff` | Body copy backgrounds |
| Text dark | `#111111` | Body copy |

### Typography

| Use | Font | Weight |
|-----|------|--------|
| Display / headlines | Georgia or Playfair Display | Bold / 700 |
| Body copy | Arial or system sans-serif | 400 |
| Subheadings / labels | Arial | 600, letter-spacing |
| Signature / italic | Georgia italic | Bold italic |

### Logo Rules

- Wordmark: "Food Game" in navy + "Media" in pink (`#c0185d`)
- Always horizontal lockup — never stacked unless explicitly approved
- Minimum clear space: equal to cap-height on all sides
- Never recolour, stretch, or add effects to the wordmark
- Pink must always be `#c0185d` — not approximated

### Gmail Signature

The HTML email signature is fully coded and should not be regenerated from scratch. It uses:
- FGM wordmark at top
- Navy/pink separator rules
- Julian Blok | Founder & Principal
- foodgamemedia.com.au + julian@foodgamemedia.com.au
- Italic tagline: *"The question is whether you're still playing the old game."*
- Footer links: Newsletter · Consulting · Podcast

---

## 4. Technical Reference

### Stack

| Layer | Detail |
|-------|--------|
| Frontend | Custom HTML5 / CSS3 / vanilla JS — no framework |
| Hosting | foodgamemedia.com.au (live domain) |
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

---

## 5. Site Structure

| Route | Status | Purpose |
|-------|--------|---------|
| `/` | Live | Home — brand intro, services overview, newsletter CTA |
| `/about` | Planned | Julian's background, philosophy, the Food Game narrative |
| `/consulting` | Planned | Services: behavioural outcomes, systems-led change |
| `/newsletter` | Planned | FGWW archive — past issues hosted on-site |
| `/contrarian` | Planned | The Contrarian column — embedded from GitHub |
| `/podcast` | Placeholder | Podcast page — content TBC |
| `/contact` | Planned | Enquiry form or mailto CTA |

> **Note:** The site returned a 404 at time of writing — domain may be in development or DNS propagating. Treat all pages as in-development unless Julian confirms live status.

---

## 6. Workflow — How Changes Are Made

### For HTML/CSS/JS edits:

1. Julian describes the change needed in the Project chat
2. Claude reads the relevant existing file (if provided) before writing anything
3. Claude makes the targeted edit — minimal blast radius, never rewrite working sections
4. Claude outputs the full updated file (not just the diff) so Julian can copy-paste or download
5. Julian pastes into his local file and checks in browser before pushing

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

- No CI/CD — changes go live by manual FTP or direct file edit
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
| 11 | Never use the pink (`#c0185d`) for body copy — accent and CTAs only |
| 12 | Never sign off newsletter content as anything other than JB |

---

## 8. Known Gotchas & Edge Cases

| Issue | Detail |
|-------|--------|
| Site 404 | foodgamemedia.com.au was returning 404 at time of SKILL creation — confirm live status before any deployment work |
| Substack HTML stripping | Substack removes custom HTML. Always use GitHub-hosted full design + Substack teaser |
| GitHub cache delay | Raw GitHub URLs cache for ~5 mins. Embedded content won't update instantly after push |
| Contrarian embed blank | Almost always a filename mismatch or the GitHub repo is set to private |
| Newsletter bg colour | FGWW body background is Slate `#cdc8d9` — not white, not navy. Easy to accidentally reset |
| Font fallbacks | Google Fonts won't load in offline/preview environments — always set Georgia / Arial as fallbacks |
| Base64 images | Large base64 embedded images make files slow to open in editors — use sparingly outside of brand suite exports |
| Cloudflare Worker | If Claude API calls fail in the newsletter engine, check Worker is deployed and API key env var is set |

---

## 9. Integrations Reference

| Service | Purpose | Credential pattern | Notes |
|---------|---------|-------------------|-------|
| Anthropic Claude API | Powers FGWW engine + The Contrarian | `sk-ant-...` stored in Cloudflare Worker env var `ANTHROPIC_API_KEY` | Never client-side |
| Cloudflare Workers | API proxy for Claude | Worker URL pattern: `https://[worker-name].[account].workers.dev` | Deployed separately |
| GitHub | Article storage for The Contrarian + full newsletter hosting | Personal access token for write operations | Repo must be public for embed to work |
| Substack | Newsletter distribution | Julian's Substack account | HTML stripped — teaser only |
| Gmail | Email with custom HTML signature | julian@foodgamemedia.com.au | Signature installed via Email Signature Rescue Chrome extension |

---

## 10. Access Details

> ⚠️ Populate this section with real credentials in your private Claude Project — do not commit to public GitHub.

| Item | Value |
|------|-------|
| Site domain | foodgamemedia.com.au |
| Primary email | julian@foodgamemedia.com.au |
| GitHub repo (website + SKILL) | https://github.com/FoodGameMedia/fgww |
| GitHub repo (Contrarian) | https://github.com/FoodGameMedia/fgww (confirm if separate) |
| Cloudflare Worker URL | young-fog-3045fgww-proxy.julian-68d.workers.dev |
| Anthropic API key | `sk-ant-...` [stored in Worker env var — never paste here] |
| Substack URL | [ADD DIRECTLY IN GITHUB] |

---

## 11. Content & Feature Status

| Feature | Status | Notes |
|---------|--------|-------|
| Home page | Unknown — confirm with Julian | Site was 404 at SKILL creation |
| About page | Not confirmed live | Planned |
| Consulting page | Not confirmed live | Planned |
| FGWW newsletter archive | Planned — not yet on site | Issues exist in Substack + GitHub |
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
