# Pipeline Stages

## Stage 0: Scope and Boundaries

Define:

- what domain is in scope
- what truths are out of scope
- what counts as freshness-sensitive
- what must never be auto-mutated

Outputs:

- domain bootstrap
- knowledge status
- intake policy

## Stage 1: Source Intake

Collect only from allowed source families.

Typical priority:

1. official docs
2. first-party product surfaces
3. verified operator evidence
4. curated internal sources
5. secondary commentary only when clearly labeled

Outputs:

- source register
- intake notes
- raw evidence snapshots

## Stage 2: Knowledge Distillation

Turn raw intake into reusable domain modules:

- curriculum
- wave briefs
- platform or subdomain bodies
- diagnostic anchors
- cross-domain synthesis

Outputs:

- content/data/*
- learning-stage notes

## Stage 3: Benchmark Design

Design eval families before optimizing behavior.

Useful families:

- retrieval
- reasoning
- boundaries
- translation
- diagnosis
- integration posture
- domain-specific safety

Outputs:

- eval framework
- casebanks
- registry

## Stage 4: Automated Eval Runner

Implement a runner that can:

- send prompts to the runtime
- extract the answer
- score it against categories
- save reports
- summarize verdicts by suite

Outputs:

- eval script
- run reports

## Stage 5: Gating

Decide what happens after a run.

Possible outcomes:

- reject
- hold for manual review
- accept into learning-stage knowledge
- promote into canon or policy

Do not promote based on one strong anecdote.

## Stage 6: Runtime Evolution

Only after the benchmark is stable:

- mutate prompt
- add or refine skills
- tighten memory routing
- sharpen short-form retrieval cues

Keep canon and policy out of the mutation surface unless explicitly approved.

## Stage 7: Regression Rhythm

After each meaningful change:

- run minimum regression
- run domain-specific hardening suite
- run applied scenarios
- compare against previous reports

## Stage 8: Productization

After recurring patterns stabilize:

- name connector candidates
- identify blueprint gaps
- separate temporary workarounds from permanent product surfaces

