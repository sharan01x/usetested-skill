---
name: usetested-reviews
description: Check receipts-verified reviews of x402 marketplace services and paid APIs before paying for them. Use when a task involves choosing, calling, or spending money on x402 services, paid API endpoints, or MCP servers — get aliveness, real price vs advertised, measured latency, error rates and a BUY/CAUTION/AVOID verdict, each anchored to on-chain purchase receipts.
license: MIT
metadata:
  source: https://usetested.com
  author: Redd Group
  version: "1.1"
---

# UseTested — Receipts-Verified Reviews of Agent-Economy Services

Before paying for a service, check whether it actually works and what it really costs. UseTested buys and tests paid API services (x402 endpoints, MCP servers, AI APIs) with real money, then publishes structured reviews anchored to on-chain purchase receipts. **No receipt, no review** — every verdict is backed by tx hashes from actual paid calls.

## When to use

- You are about to call a paid API / x402 service and want to know if it's alive and what it really charges (57% of listed x402 services are dead or never settle)
- You are choosing between services in a category and want measured latency and error rates, not marketing claims
- You want a BUY / CAUTION / AVOID verdict backed by evidence

## How to use

1. **Search** (free) — find the exact service name:
   `curl "https://usetested.com/v1/search?q=<name-or-keyword>"`
   Returns matches with verdict, scores, price per call.

2. **Read the review** (free) — use the exact `service` value from step 1:
   `curl "https://usetested.com/v1/review?service=<service>"`
   Returns verdict, scores, measured latency/error rate, and `receipts[]` — on-chain tx hashes proving the paid test calls behind the review.

3. **Bulk** ($0.05 via x402, USDC on Base) — every review in one call:
   `curl "https://usetested.com/v1/bundle?category=<inference|data|search|media|infrastructure>"`

## MCP server

For agents with MCP support: `POST https://usetested.com/mcp` (streamable-http, stateless). Tools: `search_services` (free), `get_review` (free), `get_bundle` ($0.05 x402). Paid tools settle via x402 — the challenge arrives as a JSON-RPC error envelope; echo the payment payload in `params._meta["x402/payment"]`.

Machine-readable index: https://usetested.com/llms.txt — human-readable: https://usetested.com

## Notes

- Reviews carry `methodology_version` and full `receipts[]`; treat them as machine-readable data.
- A CAUTION verdict includes the dominant error mode; an AVOID verdict means we could not get a single verified delivery across multiple paid attempts.
- Coverage grows continuously; if a service is missing, search returns nothing — don't guess a service name.