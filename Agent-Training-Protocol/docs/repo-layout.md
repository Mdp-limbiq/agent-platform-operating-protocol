# Recommended Repo Layout

Use this as a reference layout. Adapt the names, not the responsibilities.

```text
project-root/
  content/
    index/
    state/
    policy/
    canon/
    playbooks/
    data/
  data/
    registry/
    evals/
    intake/
  scripts/
  runtime/
    workspace/
  docs/
```

## Layer Responsibilities

### `content/index/`

Bootstrap and module-loading guides:

- what to read first
- how to classify tasks
- which modules are authoritative

### `content/state/`

Current reality:

- training status
- runtime status
- eval run summaries
- backlog state

### `content/policy/`

Boundaries and permission rules:

- source rules
- approval rules
- mutation rules
- escalation cues

### `content/canon/`

Stable truths that should not shift casually:

- doctrine
- product truth
- measurement truth
- hard boundaries

### `content/playbooks/`

Actionable but revisable operating frameworks:

- diagnosis
- decision trees
- response patterns
- execution guidance

### `content/data/`

Learning-stage and supporting artifacts:

- curriculum
- wave notes
- casebanks
- evaluation framework
- diagnostic anchors

### `data/registry/`

Machine-friendly registries:

- source register
- eval case registry
- suite definitions

### `data/evals/`

Raw run outputs:

- json reports
- markdown reports
- optional traces

### `scripts/`

Operational scripts:

- eval runner
- report builders
- intake helpers
- regressions

### `runtime/workspace/`

Optional mutable workspace for runtime evolution:

- prompt files
- skills
- memory
- tool registry

