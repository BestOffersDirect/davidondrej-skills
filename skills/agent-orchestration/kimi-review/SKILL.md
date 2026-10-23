---
name: kimi-review
description: Launch an independent Kimi K3.1 Pro Max code review through Pi and Vercel AI Gateway, and return it verbatim. Use only when the user explicitly invokes /kimi-review.
disable-model-invocation: true
triggers: [user, model]
---

# Kimi Review

Always use **Kimi K3.1 Pro at Max reasoning** through the Pi harness and the `vercel-ai-gateway` provider, orchestrated by [Cloudroom](https://www.cloudroom.dev). No other model, route, effort, or harness, ever. Vercel serves it with zero data retention and no training; OpenRouter only routes it to Moonshot directly, so never use OpenRouter.

Pi's built-in catalog lacks this model. It comes from a custom entry in `~/.pi/agent/models.json` under `providers.vercel-ai-gateway.models` (OpenAI-compatible API at `https://ai-gateway.vercel.sh/v1`, `reasoning_effort` `max`).

## Run

Read `/room-cli` and follow its launch checks. Reuse the current environment, including uncommitted work, and use `--parent-self` when coordinating.

Always spawn with exactly these flags:

```bash
--provider pi --model vercel-ai-gateway/moonshotai/kimi-k3.1-pro --reasoning-level max
```

- Before spawning, confirm `room-cli provider models pi --json` lists `vercel-ai-gateway/moonshotai/kimi-k3.1-pro` with `max` in `supportedReasoningEfforts`.
- After spawning, confirm with `room-cli thread show` that the thread runs `vercel-ai-gateway/moonshotai/kimi-k3.1-pro` at `max`.
- If either check fails, stop and report the blocker. Never fall back to another model, route (such as OpenRouter or fx), effort, or harness.

## Review brief

Give neutral context: scope, paths, intended behavior, and diff/base revision. Ask for a thorough senior-developer review, including related code and tests, without steering toward suspected bugs, solutions, or verdicts. Review only; do not change files. Request a concise plain-English report of serious or critical issues, fixes, and production merge readiness. Distinguish verified findings from uncertainty and identify validation gaps.

## Result

Use `room-cli thread wait` and `room-cli thread output`. Verify this review actually completed; idle status, timeouts, gateway errors (including an empty Vercel balance), and queued retries are not completion. Report blockers rather than presenting partial output as a finished review.

Return the completed reviewer's full final response verbatim.
