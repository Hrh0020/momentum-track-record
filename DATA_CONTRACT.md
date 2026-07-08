# Data Contract — build against these fields only

**For design & chat.** These are the *only* data fields the site has. Every mockup, stat tile, chart, and newsletter template must use fields from this page. **Do not invent metrics** (e.g. "Sharpe," "annualized return," "win streak") — if it's not below, the engine doesn't publish it and it will render blank.

If you need a metric that isn't here, that's an **engine change** — route it through Code (see Working Agreement rule 6 in the roadmap). Don't design around it as if it exists.

---

## `track_record.json` — the computed summary the page renders

| Field | Type | Meaning | Notes for design |
|---|---|---|---|
| `generated_at_utc` | string (ISO) | When the summary was last rebuilt | Shown as "updated …" |
| `record_start` | string (date) | First day of the clean record | Currently `2026-07-06` |
| `as_of` | string (date) | Data through this date | |
| `starting_capital` | number | Paper capital at start | Currently `15000` |
| `equity` | number | Current paper equity | Headline stat |
| `total_return_pct` | number | % return since start | Color by sign (`--pos`/`--neg`) |
| `closed_trades` | int | Count of closed trades | Currently `0` — **design for the empty state** |
| `open_trades` | int | Count of open positions | Currently `10` |
| `hit_rate_pct` | number \| **null** | % winners | **null until trades close** — must render "—" |
| `profit_factor` | number \| **null** | gross win / gross loss | **null until trades close** — render "—" |
| `equity_curve` | array | `[{date, equity}, …]` | The line chart. Currently 1 point — chart needs a "not enough data yet" state |
| `trades` | array | see below | The trades table |
| `disclaimer` | string | Publisher disclaimer text | Render verbatim; do not paraphrase |

### `trades[]` entries
| Field | Type | Meaning |
|---|---|---|
| `ticker` | string | e.g. `OSCR` |
| `entry_date` | string (date) | |
| `entry` | number \| null | Fill price |
| `status` | string | `OPEN` \| `CLOSED` \| `STOPPED` |
| `exit_date` | string \| null | null while open |
| `exit` | number \| null | null while open |
| `reason` | string \| null | exit reason, null while open |
| `pct_return` | number \| null | null while open; color by sign |

---

## `ledger.jsonl` — the raw proof log (one JSON object per line)

Append-only; the tamper-evidence artifact. One line per ENTRY/EXIT event, published *before* the outcome is known. The page derives from it; design generally renders `track_record.json`, but link to `ledger.jsonl` from the "How to verify" section as the raw source.

---

## Design implications you must handle

- **The record is brand new: 0 closed trades, 1 equity point.** The most important states to design are the **empty/early states** — "no closed trades yet," "equity curve appears once trades close," null hit-rate/profit-factor as "—". These are what a visitor sees *today*, not a full curve.
- **Nulls are normal**, not errors — render as "—", never "0" or "NaN".
- **Money vs. percent vs. count** are different formats: `$` + thousands separator for equity, `+/-%` for returns, bare integers for counts.
- **Numbers use the `--mono` font** (tabular alignment); labels/prose use `--sans`.
