# AGENTS.md

## Purpose
Single source of truth for Codex/agents. Always read this file first. Pull extra context only from the artefacts below (no inlining of full files).

## Constraints
- Non-touch paths: /node_modules, /dist, /build, /vendor
- Change budget per phase: ≤2 files / ≤80 lines
- Security/perf: no secrets in logs; stable prefix (no timestamps)

## Artefacts   (/docs/context/)
SNAPSHOT.md  •  CONTEXT_PACK.md  •  PLAN.md  •  TODO.md  •  NOTES.md  •  PR_SUMMARY.md

## Workflow (LIGHT)
1) Snapshot + Context  →  2) Plan  →  3) Execute+Test+Compact (one phase, one diff)  →  4) Handoff
Rules:
- Use curated context only (CONTEXT_PACK + the files stated in PLAN).
- JIT-read by path/line range; never dump full files or logs.
- After each phase: ≤80-word summary into NOTES.md and update TODO.md (1–3 actions).
- Stop if tests fail or budgets/constraints are violated.

## Tools
File/Git (read/patch/commit), Shell/Runner (build/test). Search optional (ask permission; list sources first).

## End-of-cycle Output
One small diff + test summary + updated TODO/NOTES; optional PR_SUMMARY.md.
