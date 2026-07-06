# Momentum Screener — Public Track Record

A public, tamper-evident record of the signals produced by a systematic
momentum swing-trading screener covering ~800 US equities. Every trade is
**paper-traded** and published here automatically by a scheduled job.

**Live page:** _(GitHub Pages URL goes here once enabled)_

## Why this exists

Anyone can post screenshots of winning trades. This repository is the opposite:
an automated, timestamped, append-only log you can audit yourself. The point is
not to be believed — it's to be **checked**.

## How to verify it

- Each signal is written to [`ledger.jsonl`](ledger.jsonl) by an automated job
  **the session after it is generated** — that is, published *before its outcome
  is known*.
- Every update is a git commit. GitHub independently timestamps and
  cryptographically chains commits, so the
  [commit history](https://github.com/Hrh0020/momentum-track-record/commits/main)
  is an audit trail no one can quietly rewrite:
  any change to a past entry would show permanently in the diff.
- Don't trust the summary numbers on the page — read the ledger and the history.

## What's in this repo

| File | What it is |
|---|---|
| `ledger.jsonl` | One JSON line per ENTRY/EXIT event — the raw proof log. |
| `track_record.json` | Computed summary (equity curve, stats) rendered by the page. |
| `index.html` | The track-record dashboard, served via GitHub Pages. |

## Honest disclaimers

- **Paper trading.** No real capital is deployed. Fills are modeled — entries at
  the next session's open plus slippage, exits gap-aware — not live executions.
- This record is **impersonal market commentary published for transparency and
  research. It is not personalized investment advice, and not a solicitation or
  recommendation to buy or sell any security.** Past performance does not
  guarantee future results.
- The clean record begins **2026-07-06**. Any earlier experimentation is not
  part of this record.
