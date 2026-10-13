---
name: muse-review
description: Launch an independent Meta Muse Wonder High code review through Pi and Vercel AI Gateway, and return it verbatim. Use only when the user explicitly invokes /muse-review.
disable-model-invocation: true
triggers: [user, model]
---

# Muse Review

Always use **Meta Muse Wonder at High reasoning** through the Pi harness and the `vercel-ai-gateway` provider, orchestrated by the orchestration tool. No other model, route, effort, or harness, ever. High is the highest effort this route offers.

## Run

Read the orchestration CLI instructions and follow its launch checks. Reuse the current environment, including uncommitted work, and coordinate through the parent thread.

Always spawn with exactly these flags:

```bash
--provider pi --model vercel-ai-gateway/meta/muse-wonder-1.0 --reasoning-level high
```

- Before spawning, confirm the orchestration CLI's model listing includes `vercel-ai-gateway/meta/muse-wonder-1.0` with `high` in its supported reasoning efforts.
- After spawning, confirm in the thread details that it runs `vercel-ai-gateway/meta/muse-wonder-1.0` at `high`.
- If either check fails, stop and report the blocker. Never fall back to another model, route (such as `openrouter/meta/muse-wonder`), effort, or harness.

## Review brief

Give neutral context: scope, paths, intended behavior, and diff/base revision. Ask for a thorough senior-developer review, including related code and tests, without steering toward suspected bugs, solutions, or verdicts. Review only; do not change files. Request a concise plain-English report of serious or critical issues, fixes, and production merge readiness. Distinguish verified findings from uncertainty and identify validation gaps.

## Result

Wait for the thread to finish and retrieve its output using the orchestration CLI. Verify this review actually completed; idle status, timeouts, gateway errors, and queued retries are not completion. Report blockers rather than presenting partial output as a finished review.

Return the completed reviewer's full final response verbatim.
