# Adaptation Guide

## Use This Template When

You want a reusable training pipeline for a domain where:

- knowledge quality matters
- the domain changes over time
- answers need benchmarks
- runtime behavior may need to evolve

## Step 1: Define the Domain

Write down:

- domain name
- source of truth
- unstable areas
- prohibited claims
- what "good" behavior looks like

## Step 2: Define Eval Families

Do not start with one giant generic suite.

Split by behavior:

- retrieval
- reasoning
- diagnosis
- boundaries
- translation
- integration or execution posture
- domain-specific risks

## Step 3: Pick the Mutable Surface

Choose what may change automatically:

- prompt
- skills
- memory
- routing hints

Choose what must stay stable:

- canon
- policy
- approval matrix
- high-risk operational rules

## Step 4: Add Read-Only Realism First

Before adding write operations:

- use read-only cases
- use snapshots
- use official docs
- use safe simulated tasks

Write-heavy training should arrive later.

## Step 5: Treat Freshness Explicitly

If the domain changes often:

- require fresh verification for feature-level claims
- score boundary behavior directly
- reward calibrated uncertainty

## Step 6: Add an Evolution Loop Last

Only add an automatic evolution loop when:

- the benchmark is trusted
- the reports are comparable across runs
- the mutable surface is clearly bounded
- rollback is easy

## Good Generic Domains

- platform operations
- policy QA
- support quality
- technical troubleshooting
- internal research synthesis
- connector selection and execution posture

## Harder Domains

These need stronger guardrails:

- medical
- legal
- financial advice
- production write operations
- any domain with irreversible actions

