# Product & Publishing Roadmap — Audience Side

**Status:** planning / handoff draft
**Repo:** `momentum-track-record` (public Product repo). The Engine (`momentum-screener-bot`) stays private and unaware this exists.
**Companion files:** `DECISIONS.md` (append-only decision log) · `DATA_CONTRACT.md` (the JSON fields design must build against).

---

## How to use this document (read first)

Work on this project happens across **three tools that cannot see each other**:

- **Code (Claude Code)** — has this repo. Builds and deploys everything. Owns implementation.
- **Design center** — has no repo access. Produces brand, visuals, copy.
- **Regular chat** — has no repo access. Strategy, naming, editorial, pricing.

Because they can't see each other, this doc is the **single source of truth**. The rule that keeps all three aligned:

> **Decisions are *made* in chat/design. Decisions are *recorded* here (in the repo).**
> Any copy pasted into another tool is scratch — it always flows *back* to this doc. This doc never has a rival "master" copy.

If you're a **designer**, read §2 (starting point), §4 (what you own), §7 (the brief + exact deliverable format). If you're in a **strategy/editorial chat**, read §1, §3, §5, §9. If nothing else: follow the **Working Agreement in §8** — those six rules are what prevent misalignment.

---

## 1. The goal (north star)

Turn the automated, tamper-evident paper-trading record into an **audience business**, where:

- the **public track record is the funnel** (free, verifiable proof — not the product),
- a **free newsletter + a free market-regime signal** build the audience,
- **real-time entry/exit alerts** are the paid tier, and **written narrative/reports** are premium.

We stay a **publisher**, not an investment adviser. We publish our own impersonal results and commentary; we never give personalized advice or manage anyone's money. That single line keeps the whole thing low-burden and shippable before live capital.

**One-sentence pitch:** *"An automated, publicly auditable momentum track record — proof you can check, not screenshots you have to trust — with a newsletter and signal service built on top."*

---

## 2. Where we are today (the real starting point)

| Piece | State |
|---|---|
| Proof page (`index.html`) | ✅ Works, but a deliberate **unbranded placeholder** — dark theme, system fonts, restyle-later CSS variables |
| Auto-publishing (`ledger.jsonl`, `track_record.json`) | ✅ Live — signals published before outcomes are known |
| "How to verify" / tamper-evidence story | ✅ Written, strong — this is the differentiator |
| Publisher-safe disclaimers | ✅ Drafted |
| Paper book | ✅ $15k, 10 open positions, record from 2026-07-06, **no closed trades yet** |
| **Brand** (name, logo, voice, visual system) | ❌ Nothing |
| **Newsletter / content** | ❌ Nothing |
| **Email capture / funnel** | ❌ Nothing |
| **Free regime lead-magnet** | ❌ Nothing |
| **Paid tiers / payments** | ❌ Nothing |

The engineering spine is done. **Everything in the bottom half of that table is this roadmap.**

---

## 3. The product in one picture

```
   FREE (proof + top of funnel)                 PAID
 ┌───────────────────────────────┐   ┌───────────────────────────────┐
 │  Public track record (page)   │   │  CORE — real-time alerts      │
 │  Market-regime signal (free)  │──▶│   entry/exit + stop/target/    │
 │  Free newsletter (weekly)     │   │   sizing, pushed on the day    │
 │        │  email capture       │   │                                │
 │        ▼                      │   │  PREMIUM — + written rationale,│
 │  Delayed public ledger        │   │   live book, weekly context    │
 └───────────────────────────────┘   └───────────────────────────────┘
        proof / trust                       timeliness + narrative
```

**Hard rule (constrains design and pricing):** tier boundaries are **time, breadth, and convenience only** — never scores, gates, or strategy internals. Selling internals would let subscribers clone the edge. The delay on the public ledger is the paid incentive, but it must stay short enough that every signal still publishes *before* its outcome is knowable.

---

## 4. Division of labor (who owns what)

| Design center / regular chat OWNS | Claude Code OWNS |
|---|---|
| Product/brand **name** + tagline | Restyling the page from the design (CSS tokens) |
| **Positioning** & messaging / voice | New page sections (About, How it works, Pricing) |
| **Logo**, favicon, social/OG images | Email capture wiring + list integration |
| **Visual system**: color, type, spacing, chart styling | Newsletter generation/automation from the ledger |
| **Copy** (hero, about, disclaimer polish, newsletter templates) | Regime lead-magnet endpoint/widget |
| Newsletter **format & editorial cadence** | Payment/subscription + tier gating |
| **Pricing** numbers & tier names | Analytics, SEO metadata, deploy |
| Channel/launch **strategy** | Anything that reads the ledger or Engine artifacts |

**Rule of thumb:** if it's a decision about how it *looks*, what it's *called*, or what it *says* → design/chat. If it *reads data, renders, sends, or charges* → Code.

---

## 5. Newsletter + payments platform (recommendation)

**Recommendation: beehiiv** for newsletter + list + paid subscriptions.

The margin killer is a **percentage take rate**, not the tooling. Stripe's ~2.9% + 30¢ is the unavoidable payment rail everywhere. What varies is the platform's cut on top:

| Platform | Platform take | Notes |
|---|---|---|
| **beehiiv** ✅ | **0% of subs** + flat ~$40–100/mo | Newsletter-native, Stripe underneath, referral engine, web archive, custom domain |
| Ghost | 0% + ~$9–25/mo or self-host | Own your data; more stack to maintain, no margin edge over beehiiv |
| Substack | **10% of subs** + Stripe | Zero setup + discovery network, but 10% forever — fine for a *free* list, bad paid home |
| Kit (ConvertKit) | small/flat | Strong automation |

beehiiv beats Substack on margin the moment subscription revenue clears ~$1k/mo, and never charges a % of subs. **Do not self-host email** — deliverability/spam-compliance is the one wheel worth *not* reinventing.

**Product is two-shaped:** the weekly **newsletter** fits beehiiv as-is; **real-time alerts** are not newsletter-shaped (time-sensitive pushes) — that's the one custom piece Code builds, and only when the paid tier goes live. At launch, alerts can piggyback on the platform broadcast. *(Verify beehiiv's current pricing before committing — tiers move.)*

---

## 6. Phased sequence

Phases are ordered so nothing waits on live capital until it must. The paid tier is gated on the Engine's readiness (≥60-day clean paper phase + go-live gates in the Engine roadmap); everything before it can ship now.

- **Phase 0 — Brand foundation** *(design only, no code dependency, start now)*
  Name, logo, visual system, voice, pricing philosophy. Output: the filled-in brief in §7.
- **Phase 1 — Branded proof site + free newsletter** *(pre-live, builds audience)*
  Restyle page, add hero/about/how-it-works, launch the free weekly newsletter.
- **Phase 2 — Free funnel** *(pre-live)*
  Regime lead-magnet + email capture + onboarding sequence.
- **Phase 3 — Paid tiers** *(gated on clean paper phase / go-live)*
  Real-time alerts (core) + narrative/reports (premium) + payments.

---

## 7. Design brief — what to produce, and the exact format to return it in

This section is self-contained: a designer needs nothing but this to deliver. **Return every value in the format below so it drops straight into code with zero translation.**

### 7a. Color — return as these exact CSS variable names
The page is already built on these tokens. Give a hex for each (provide **both** a dark and light value if we support light mode — see §9):

```
--bg       page background            (currently #0f1115)
--panel    card / section background  (currently #171a21)
--border   hairlines, dividers        (currently #262b36)
--text     primary text              (currently #e6e9ef)
--muted    secondary / labels        (currently #8b93a3)
--pos      gains / up                 (currently #3fb950)   ← keep distinct from --neg for color-blind users
--neg      losses / down             (currently #f85149)
--accent   brand, links, equity curve (currently #58a6ff)
```

### 7b. Type — return as font-family stacks for these two tokens
```
--sans   UI / body      (currently system sans stack)
--mono   numbers, tables, ledger  (currently system mono stack)
```
If using web fonts, name them and note the source; Code will self-host them (the page must stay dependency-free on GitHub Pages).

### 7c. Assets
- **Logo** (SVG preferred) + **favicon** + a **social/OG card image** (link-preview image — matters for a share-driven launch).

### 7d. Copy blocks
- **Hero** (headline + subhead), **About**, **How it works** (strategy in plain English — *no internals*), **tier names + prices** (when ready), and any **disclaimer polish** (keep the publisher framing — see §9).

### 7e. Constraints design must respect
- **Build against real data only** — use the actual fields in `DATA_CONTRACT.md`. A mockup that invents a metric the engine doesn't produce will break on contact.
- **Keep "How to verify" prominent** — it's the differentiator, not fine print.
- **Publisher, not adviser** — nothing may read as "we'll tell *you* what to buy" or "we'll manage it for you" (see §9).
- Page must stay **static / dependency-free** (GitHub Pages, no build step).

---

## 8. Working Agreement — staying aligned across chat, code & design

**These six rules are the whole game. Follow them and nothing drifts. If you only remember one thing, remember: everything flows back to this repo.**

1. **Round-trip every decision.** When chat/design settles something (a name, a hex, a price), paste it back to Code in one line; Code records it in `DECISIONS.md` and updates this roadmap. Nothing is "decided" until it's in the repo.
2. **Respect the ownership lines (§4).** Design hands over *values and copy*, not code. Code hands over *data schema and constraints*, not brand opinions. Neither tool edits the other's artifact.
3. **Design against real data.** Mockups use the fields in `DATA_CONTRACT.md`. No invented metrics.
4. **Use the token format (§7) as the design→code contract.** Colors/fonts come back as the CSS variable names in §7a/§7b. Zero translation.
5. **Date and supersede handoffs.** When you bring a new version from design, say "this replaces the palette from before" so Code never merges two conflicting states.
6. **Route engine-touching ideas through Code.** The only Engine→Product link is the ledger artifact (`DATA_CONTRACT.md`). A regular chat can't know that; if a feature needs new engine data, that's a change only Code can make in the private repo — don't assume it's free.

---

## 9. Open decisions (settle in the branding/strategy chat)

Record each answer in `DECISIONS.md` once made.

1. **Personal brand vs. product brand?** (e.g. "Harrison's momentum log" vs. a standalone product name.) Decide **first** — it cascades into everything.
2. **Platform:** beehiiv (recommended) vs. Ghost vs. Substack.
3. **Tone:** keep the current humble-auditable voice ("the point is not to be believed — it's to be checked") or something bolder?
4. **Public-ledger delay length** (the paid incentive — must stay shorter than time-to-outcome).
5. **Domain name.**
6. **Light mode?** The page is dark-only today; decide if we support both (affects whether §7a needs two palettes).
7. **Tier count + prices.**

---

*Companion to `momentum-screener-bot/docs/07_roadmap.md` (the Engine roadmap). That doc's "Product-track spec" defines the interface contract and the "sell latency + narrative, never internals" rule this plan inherits.*
