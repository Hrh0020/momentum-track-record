# Decisions Log

Append-only record of product/publishing decisions, so chat, code, and design stay in sync from one place. **Newest at top.** When a decision is made in any tool, add a row here (Code writes it; you paste the one-liner).

Format: `YYYY-MM-DD · [DECIDED | RECOMMENDED | OPEN] · topic — decision · (where/why)`

---

## Log

- **2026-07-08 · DECIDED · Visual direction — "Antique brass"** — Warm/luxurious, non-neon; minimal/precise. Both dark and sand-light palettes built. *(Design center; replaces placeholder palette in `index.html`.)*
- **2026-07-08 · DECIDED · Color tokens (§7a)** — Dark/sand hexes delivered for `--bg/--panel/--border/--text/--muted/--accent/--pos/--neg`. `--accent` is two values (`#B8933D` dark / `#93701F` sand) for AA contrast on each ground. See `Ledger_Line__Brand_Handoff.md`.
- **2026-07-08 · DECIDED · Type (§7b)** — `--sans` = "Instrument Sans", `--mono` = "IBM Plex Mono"; both OFL, self-hosted (no CDN — Pages stays dependency-free).
- **2026-07-08 · DECIDED · Brand assets delivered** — Production logo (mark + lockup, dark/sand), favicons (svg/32/180/512), and OG card received from Design. Ready to wire into the page.
- **2026-07-08 · OPEN · Default mode (sand vs dark)** — Which palette loads first is unsettled; light-mode §9 item now scoped to two full palettes + a toggle.
- **2026-07-08 · DECIDED · Brand name — "Ledger Line"** — Standalone product brand (not personal). Momentum stays in tagline/copy, not the name, to preserve room for future strategies under the same brand. *(Web-search diligence only: no SEC-registered adviser/fund found; two unrelated small bookkeeping/accounting businesses use similar names, different category, low collision risk. Formal USPTO TESS + state business-registry search still pending before filing an LLC or trademark.)*
- **2026-07-08 · DECIDED · Voice/tone** — Lands between the humble-auditable draft voice ("not to be believed — to be checked") and something bolder. Not deadpan, not hype-y.
- **2026-07-08 · DECIDED · Alignment model** — This repo is the single source of truth. Decisions made in chat/design are recorded here + in `PRODUCT_ROADMAP.md`; no rival master copies. *(Working Agreement, roadmap §8.)*
- **2026-07-08 · DECIDED · Design→code handoff format** — Colors/fonts returned as the CSS variable names in roadmap §7 (`--bg`, `--panel`, `--border`, `--text`, `--muted`, `--pos`, `--neg`, `--accent`, `--sans`, `--mono`). *(Zero-translation contract.)*
- **2026-07-08 · DECIDED · Design builds against `DATA_CONTRACT.md` only** — No invented metrics; new metrics require an engine change routed through Code.
- **2026-07-08 · RECOMMENDED · Newsletter + payments platform** — beehiiv (0% of subs + flat fee; Stripe underneath). Alternatives: Ghost (own-the-stack), Substack (free list only). *Awaiting confirmation — verify current pricing first.*
- **2026-07-08 · DECIDED · Positioning** — Publisher, not investment adviser. Impersonal market commentary; never personalized advice or managed money. *(Regulatory spine; constrains all copy.)*
- **2026-07-08 · DECIDED · Tier boundaries** — Time, breadth, convenience only. Never sell scores/gates/internals at any tier. Public-ledger delay is the paid incentive but must stay shorter than time-to-outcome.
- **2026-07-08 · DECIDED · Repo split** — Product lives in this public repo; Engine (`momentum-screener-bot`) stays private and unaware of it. Only coupling is the published ledger artifact.

---

## Open (see roadmap §9)

- [x] Personal brand vs. product brand — **"Ledger Line"**, standalone product brand
- [ ] Platform confirmation (beehiiv / Ghost / Substack)
- [x] Voice/tone — between humble-auditable and bolder
- [ ] Public-ledger delay length
- [ ] Domain name (ledgerline.com or similar — check availability, grab it soon)
- [ ] Formal trademark/business-registry check on "Ledger Line" before filing
- [x] Light mode? — **both dark + sand palettes built**; default (which loads first) still open
- [ ] Default mode — sand-light or dark loads first (blocks the restyle apply)
- [ ] Tier count + prices
