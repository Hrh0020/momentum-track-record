# Decisions Log

Append-only record of product/publishing decisions, so chat, code, and design stay in sync from one place. **Newest at top.** When a decision is made in any tool, add a row here (Code writes it; you paste the one-liner).

Format: `YYYY-MM-DD · [DECIDED | RECOMMENDED | OPEN] · topic — decision · (where/why)`

---

## Log

- **2026-07-08 · DECIDED · Alignment model** — This repo is the single source of truth. Decisions made in chat/design are recorded here + in `PRODUCT_ROADMAP.md`; no rival master copies. *(Working Agreement, roadmap §8.)*
- **2026-07-08 · DECIDED · Design→code handoff format** — Colors/fonts returned as the CSS variable names in roadmap §7 (`--bg`, `--panel`, `--border`, `--text`, `--muted`, `--pos`, `--neg`, `--accent`, `--sans`, `--mono`). *(Zero-translation contract.)*
- **2026-07-08 · DECIDED · Design builds against `DATA_CONTRACT.md` only** — No invented metrics; new metrics require an engine change routed through Code.
- **2026-07-08 · RECOMMENDED · Newsletter + payments platform** — beehiiv (0% of subs + flat fee; Stripe underneath). Alternatives: Ghost (own-the-stack), Substack (free list only). *Awaiting confirmation — verify current pricing first.*
- **2026-07-08 · DECIDED · Positioning** — Publisher, not investment adviser. Impersonal market commentary; never personalized advice or managed money. *(Regulatory spine; constrains all copy.)*
- **2026-07-08 · DECIDED · Tier boundaries** — Time, breadth, convenience only. Never sell scores/gates/internals at any tier. Public-ledger delay is the paid incentive but must stay shorter than time-to-outcome.
- **2026-07-08 · DECIDED · Repo split** — Product lives in this public repo; Engine (`momentum-screener-bot`) stays private and unaware of it. Only coupling is the published ledger artifact.

---

## Open (see roadmap §9)

- [ ] Personal brand vs. product brand — **decide first**
- [ ] Platform confirmation (beehiiv / Ghost / Substack)
- [ ] Voice/tone
- [ ] Public-ledger delay length
- [ ] Domain name
- [ ] Light mode? (dark-only today)
- [ ] Tier count + prices
