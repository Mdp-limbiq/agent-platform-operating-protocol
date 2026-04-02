# Agent Training Protocol

This folder is a reusable design pack for building an agent training pipeline
without fine-tuning model weights.

It is based on the shape of the current `NN-Mirai` paid-media pipeline, but it
is intentionally generalized so it can be reused for other domains such as:

- platform operations
- customer support quality
- policy interpretation
- product strategy
- sales enablement
- research synthesis

## What This Template Covers

- source intake from official and high-trust sources
- knowledge distillation into structured domain files
- benchmark and casebank design
- automated eval and regression runs
- gating and promotion rules
- runtime orchestration objects such as tasks, queues, recommendations, and proposals
- section-driven surface rendering for agent-authored output
- scheduler ownership of cadence and work handoff to the agent
- optional evolution loop over prompts, skills, and memory
- reusable reporting artifacts

## Core Design Rule

Separate these layers on purpose:

1. source of truth
2. learning-stage operating knowledge
3. runtime workspace
4. evaluation evidence
5. promoted canon and policy

Do not let the runtime mutate canon or policy directly.

## Suggested Flow

1. Define scope, boundaries, and freshness rules.
2. Register sources and intake them in a disciplined order.
3. Distill knowledge into reusable modules.
4. Build casebanks before claiming mastery.
5. Run automated evals and save reports.
6. Gate promotions into canon, playbooks, or policies.
7. Optionally evolve the runtime workspace.
8. Re-run regressions before accepting any change.

## Folder Map

- `docs/`: architecture and operating design
- `templates/content/`: reusable markdown templates
- `templates/registry/`: registry skeletons for evals and sources
- `templates/config/`: pipeline config skeleton
- `templates/evolution-workspace/`: optional workspace scaffold for an
  evolution loop over prompts, skills, memory, and tools
- `examples/`: concrete mapping from the generic template to a live system

## Quick Start

1. Copy this folder into a new project.
2. Replace `DOMAIN_NAME`, `OWNER_NAME`, and placeholder values.
3. Fill the templates under `templates/content/` for your domain.
4. Build a case registry from `templates/registry/eval_cases.template.json`.
5. Implement a runner that can score answers against your categories.
6. Start with read-only evals before adding any write-capable workflows.
7. Only add the evolution workspace after the benchmark is trustworthy.

## Recommended Order

If you are starting from zero, read these first:

1. `docs/architecture.md`
2. `docs/infra-blueprint.md`
3. `docs/training-protocol.md`
4. `docs/ops-scheduler-and-watcher.md`
5. `docs/runtime-orchestration-objects.md`
6. `docs/flexible-surface-rendering.md`
7. `docs/repo-layout.md`
8. `docs/pipeline-stages.md`
9. `docs/adaptation-guide.md`
10. `examples/nn-mirai-pipeline-map.md`
11. `docs/repo-shortlist-2026-04-01.md`
