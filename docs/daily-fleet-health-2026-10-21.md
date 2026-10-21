# Daily Fleet Health & Stability — 2026-10-21

## Action today
**Escalate one active budget incident and investigate a high-error agent (Nina R.).** The operational verdict is unhealthy because it reports 1 active budget incident and 134 recent failed/timed-out heartbeat runs. No existing open remediation issue was found by keyword search; create/route remediation through the board rather than treating this report as the work item.

## Current health (30-day windows unless noted)
- **Overall:** 6,802 completed/in-flight heartbeat runs: 6,537 succeeded, 124 failed, 131 cancelled, 10 timed out; success rate **96.1%**. 2 runs are currently queued/running according to the verdict; the raw heartbeat endpoint currently shows 1 running row.
- **Failure grouping:** Reliability slice is 226 runs with 3 failures (**1.3%**, below the 10% alert threshold): 1 `max_turns`, 2 `crash`. Provider split: OpenRouter 224 runs / 1 failure (0.4%); unknown provider 2 / 2 failures (100%). The broader verdict reports 124 failed + 10 timed out, so these are different telemetry scopes; do not merge denominators.
- **Agent outlier:** Nina R. has 6 runs and 2 errors (**33.3%**, active alert) in the reliability slice. Liz T. has the largest 30-day volume error count (38/1,195; 3%), but no active threshold alert in the reliability slice.
- **Stuck runs:** None reported by the operational-verdict `stuckRunning` field. Raw endpoint shows one currently running run (Rita A., started 11:19:45 UTC), too recent to classify as stuck.
- **Provider health:** No balance/quota failure is explicitly named. However, one active budget incident is present; provider/budget details are unknown from returned endpoint data and require owner investigation.
- **No-op / cost signal:** Work outcomes: 18,668 total outcomes; 3,392 changed (18.2%), 11,866 no-change (63.6%), 3,410 unknown (18.3%). This is a material no-change signal, but no-op causality is not available. Model usage totals **572,790 cents ($5,727.90)**: GPT-5.6 Luna Pro $3,133.10 (86% success), Luna $2,529.10 (90%), GPT-4o $65.70 (80%).

## Remediation findings
1. **Budget incident — high priority:** assign an infrastructure/operations owner to identify the active incident, provider, and cap impact; confirm whether throttling or spend controls are affecting runs.
2. **Nina R. reliability alert — high priority:** inspect the two failed runs and classify root cause; no generic retry or model change should be applied until run-level evidence is available.
3. **Telemetry reconciliation — medium priority:** reconcile the 6,802-run verdict denominator with the 226-run reliability slice and raw running count before trend comparisons.
4. **No-change rate — medium priority:** sample the 11,866 no-change outcomes to distinguish legitimate read-only work from wasted runs.

## Unknowns / evidence boundaries
- Failure/run endpoints do not expose per-run error detail in this response; root-cause assignment beyond `max_turns`/`crash` is unknown.
- No explicit budget amount, incident owner, or quota status returned.
- No existing open remediation issue matched `budget incident heartbeat failures Nina`.
- This report is an operational artifact; `done` status on other issues is not treated as delivery evidence.
