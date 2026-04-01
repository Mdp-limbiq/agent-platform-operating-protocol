---
id: data.DOMAIN_NAME-casebank
layer: data
domain: DOMAIN_NAME
status: active
update_mode: manual_only
owner: OWNER_NAME
last_verified: YYYY-MM-DD
confidence: high
publish: true
source_of_truth: manual
validation_stage: eval
---

# DOMAIN_NAME Casebank

Use this file to describe the intent behind a suite of cases.

## Purpose

What this suite is trying to test:

- retrieval
- reasoning
- diagnosis
- boundaries
- integration

## What Good Looks Like

- the agent names the right surface or source family
- the agent preserves subdomain differences
- the agent uses calibrated language when freshness matters
- the agent avoids turning workarounds into doctrine

## What Failure Looks Like

- generic advice
- unsafe certainty
- wrong surface choice
- no diagnosis before recommendation

## Notes

The actual machine-readable cases should live in the eval registry.

