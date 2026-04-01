---
id: data.DOMAIN_NAME-regression-runbook
layer: data
domain: DOMAIN_NAME
status: active
update_mode: manual_only
owner: OWNER_NAME
last_verified: YYYY-MM-DD
confidence: high
publish: true
source_of_truth: manual
---

# DOMAIN_NAME Regression Runbook

Keep progress measurable and catch regressions after new training waves,
source-intake batches, routing changes, or runtime mutations.

## Minimum Eval Set

1. one retrieval case
2. one reasoning case
3. one diagnosis case
4. one boundary case
5. one integration case
6. one applied scenario

## When To Run

- after each new wave
- after each hardening pass
- before promoting canon or policy
- before accepting runtime mutations

## Minimum Commands

```bash
python3 scripts/run_eval.py --suite regression_minimum
python3 scripts/run_eval.py --suite smoke
python3 scripts/run_eval.py --suite applied_scenarios
```

## Reports

Write reports to:

- `data/evals/DOMAIN_NAME/*.json`
- `data/evals/DOMAIN_NAME/*.md`

