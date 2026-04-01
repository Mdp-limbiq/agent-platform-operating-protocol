# NN-Mirai Pipeline Map

This file shows how the generic template maps onto the current `NN-Mirai`
paid-media pipeline.

## Domain

- domain: paid media and adjacent `NoNarcissAI` acquisition reasoning
- runtime name today: `NN-Mirai`

## Source Intake Layer

Current examples:

- official platform docs
- internal source registers
- Hyperbrowser-assisted verification

Representative artifacts:

- `Mirai-Knowledge/content/index/paid-media-bootstrap.md`
- `Mirai-Knowledge/content/state/paid-media-knowledge-status.md`

## Distilled Knowledge Layer

Current examples:

- paid-media curriculum
- wave training notes
- platform bodies
- diagnostic anchors
- cross-platform synthesis

Representative artifacts:

- `Mirai-Knowledge/content/data/paid-media/paid-media-curriculum.md`
- `Mirai-Knowledge/content/data/paid-media/platform-mastery-expansion-plan.md`

## Eval Layer

Current examples:

- eval framework
- multiple casebanks
- machine-readable registry
- automated runner
- saved reports

Representative artifacts:

- `Mirai-Knowledge/content/data/paid-media/paid-media-eval-framework.md`
- `Mirai-Knowledge/data/registry/paid_media_eval_cases.json`
- `Mirai-Knowledge/scripts/paid_media_eval.py`

## State and Evidence Layer

Current examples:

- baseline report
- platform-depth report
- integration-judgment report
- applied-scenarios report

Representative artifacts:

- `Mirai-Knowledge/content/state/paid-media-automation-baseline-2026-03-25.md`
- `Mirai-Knowledge/content/state/platform-depth-evals-2026-03-26.md`
- `Mirai-Knowledge/content/state/integration-judgment-evals-2026-03-26.md`
- `Mirai-Knowledge/content/state/applied-platform-scenarios-evals-2026-03-26.md`

## Runtime Layer

Current reality:

- live Hermes runtime
- prompt and routing behavior
- paid-media knowledge loading

Missing future layer:

- a separate bounded mutation surface for prompts, skills, and memory that can
  be evolved automatically under regression gating

## What This Means

`NN-Mirai` already has most of the pipeline except the last closed-loop runtime
evolution layer.

That is why this template is structured to:

1. preserve the current knowledge-and-eval architecture
2. add a generic evolution surface later
3. stay reusable for non-paid-media domains

