---
name: muse-review
description: Launch an independent Meta Muse Wonder Max code review through Pi and OpenRouter, and return it verbatim. Use only when the user explicitly invokes /muse-review.
disable-model-invocation: true
triggers: [user, model]
---

# Muse Review

Always use **Meta Muse Wonder at Max reasoning** through the Pi harness and the `openrouter` provider, orchestrated by the orchestration service. No other model, route, effort, or harness, ever. Only OpenRouter offers `max` for this model; Pi sends it through unchanged.

## Run

Read the orchestration CLI's documentation and follow its launch checks. Reuse the current environment, including uncommitted work, and use its parent-session coordination option when coordinating.

Always select exactly:

```text
provider: pi
model: openrouter/meta/muse-wonder
reasoning level: max
```

- Before spawning, confirm the orchestration CLI's provider model listing includes `openrouter/meta/muse-wonder` with `max` among its supported reasoning efforts.
- After spawning, confirm through the orchestration CLI's thread details that the thread runs `openrouter/meta/muse-wonder` at `max`.
- If either check fails, stop and report the blocker. Never fall back to another model, route (such as `vercel-ai-gateway/meta/muse-wonder-1.0`), effort, or harness.

## Review brief

Give neutral context: scope, paths, intended behavior, and diff/base revision. Ask for a thorough senior-developer review, including related code and tests, without steering toward suspected bugs, solutions, or verdicts. Review only; do not change files. Request a concise plain-English report of serious or critical issues, fixes, and production merge readiness. Distinguish verified findings from uncertainty and identify validation gaps.

## Result

Wait for the review thread to finish and retrieve its output using the orchestration CLI. Verify this review actually completed; idle status, timeouts, gateway errors, and queued retries are not completion. Report blockers rather than presenting partial output as a finished review.

Return the completed reviewer's full final response verbatim.
