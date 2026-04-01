---
id: data.DOMAIN_NAME-eval-framework
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

# DOMAIN_NAME Eval Framework

This file defines how to evaluate the agent on `DOMAIN_NAME`.

## Eval Families

1. retrieval
2. reasoning
3. boundaries
4. translation
5. diagnosis
6. integration
7. domain-specific safety

## Scoring Rubric

- `2`: correct, well-framed, and calibrated
- `1`: partially correct, too generic, or compressed
- `0`: wrong, flattened, unsafe, or overconfident

## Required Behaviors

- prefer trusted source families
- preserve domain-native semantics
- flag freshness risk when needed
- separate stable truth from temporary workaround

## Failure Modes To Watch

- generic advice that flattens subdomains
- overconfident feature-level certainty
- strong answers for the wrong reasons
- temporary runtime shortcuts treated as permanent doctrine

