
## 2026-11-15 14:15 - Dev set mapped + harness v1 (plan/work/verify)

HF dataset gate accepted (auto-approved as Daniel). 29 dev tasks:
- 12 checks (automated verifier), 14 rubric (LLM judge, claude-opus-5-5 at leaderboard), 3 checks-judge.
- 13 tasks have MCP servers (8-13 each; civil/elec doc services); 16 have none.
- Instructions 0.6k-21k chars; 2-4 CPUs / 4-12GB per task container; 6h each.

Harness v1 "orrim-foreman": custom-openai engine (streaming, compaction, MCP, retries)
+ plan-verify phases grafted on:
- PLAN phase (read-only, no MCP, 7% of task time): maps deliverables/approach/risks.
- WORK phase (full tools + MCP, until 25% of time left): executes with plan injected.
- VERIFY phase (read-only, until 8% left): independent re-check of every deliverable,
  recomputes key numbers; up to 2 fix rounds resume the worker's conversation.
Env knobs: PLAN_SHARE, CHECK_SHARE, VERIFY_LEFT_SHARE, MAX_FIX_ROUNDS, MIN_STEP_SEC=300.

Next: push repo once PAT approval lands, set Actions secrets, kit check, then
dev-set baseline vs official template (Pi on Opus 5.5, 0.483 ref).
