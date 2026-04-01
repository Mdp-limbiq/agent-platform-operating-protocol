---
id: index.DOMAIN_NAME-bootstrap
layer: index
domain: DOMAIN_NAME
status: active
update_mode: manual_only
owner: OWNER_NAME
last_verified: YYYY-MM-DD
confidence: high
publish: true
source_of_truth: PROJECT_NAME
---

# DOMAIN_NAME Bootstrap

Read this file first when operating in the `DOMAIN_NAME` domain.

## Purpose

Orient the agent before deeper work.

## Order

1. Read `module-map.md`
2. Read `decision-order.md`
3. Read `knowledge-status.md`
4. Classify the task
5. Load only the minimum required modules
6. Route to the correct playbook or policy

## First Modules

- `../state/DOMAIN_NAME-knowledge-status.md`
- `../state/DOMAIN_NAME-training-status.md`
- `../data/DOMAIN_NAME-curriculum.md`
- `../data/DOMAIN_NAME-eval-framework.md`

## Do Not Assume

- unstable details are not permanent truth
- runtime convenience is not canon
- missing data is not permission to invent certainty

