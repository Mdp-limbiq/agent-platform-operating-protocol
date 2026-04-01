# Training Protocol

## Purpose

This protocol defines how an agent improves without confusing:

- domain truth
- runtime convenience
- personal memory
- experiment noise

Use it for domains such as paid media, support quality, troubleshooting, or
policy interpretation.

## Protocol Invariants

1. Knowledge must be versioned in files before it is trusted.
2. Every meaningful change must produce eval evidence.
3. Runtime mutation is allowed only on bounded surfaces.
4. Personal or relational memory must not be mixed into canon.
5. Promotion and rollback must both be operationally easy.

## Artifact States

### Knowledge Artifact States

1. `raw_evidence`
2. `distilled_candidate`
3. `learning_stage`
4. `benchmarked`
5. `promoted`
6. `deprecated`

### Runtime Artifact States

1. `candidate_patch`
2. `canary_ready`
3. `accepted`
4. `rolled_back`

### Memory Artifact States

1. `unclassified`
2. `relational_candidate`
3. `episodic_candidate`
4. `approved_memory`
5. `expired_or_rejected`

## Training Flows

### Flow 1: Source Intake to Knowledge

1. ingest approved sources
2. record provenance, date, freshness, and capture path
3. distill into structured notes or modules
4. mark as `distilled_candidate`
5. run smoke evals against the changed area
6. move into `learning_stage` if the smoke passes
7. include in broader suites before any promotion

Output:

- reusable domain files with evidence lineage

### Flow 2: Knowledge to Benchmark

1. identify the concepts changed by the new knowledge
2. add or update cases in the registry
3. classify each case by suite and risk level
4. run the minimum regression
5. run changed-domain suites
6. compare against baseline reports

Output:

- comparable benchmark evidence

### Flow 3: Runtime Improvement

1. identify repeated misses from evals or live traces
2. localize the failure to prompt, skill, memory, routing, or knowledge gap
3. patch only the smallest mutable surface
4. run canary evals
5. if improved, run broader regressions
6. accept or rollback

Output:

- bounded runtime improvements with evidence

### Flow 4: Live Session Learning

1. capture session traces
2. classify extracted learnings:
   - domain truth
   - relational preference
   - episodic rationale
   - reusable procedure
   - temporary noise
3. route to exactly one primary store
4. require review for anything that might become doctrine

Primary routing:

- domain truth -> knowledge repo
- relational preference -> relational memory
- episodic rationale -> session search
- reusable procedure -> skills
- noise -> discard

### Flow 5: Promotion

Promotion into canon or policy requires:

- repeated support across more than one suite
- freshness awareness
- no contradiction with stronger sources
- manual review for high-impact domains

## Mutation Surface

### Mutable by Training Loop

- prompts
- skills
- short memory summaries
- retrieval hints
- tool routing hints

### Not Mutable by Training Loop

- canon
- policy
- approval matrix
- source register rules
- hard safety boundaries

## Evidence Requirements

Every accepted change should be traceable to:

- the input source or failing case
- the changed artifact
- the run that validated it
- the decision that accepted it

## Gating Protocol

### Reject

Use when:

- a regression appears in high-priority suites
- a patch improves style but worsens judgment
- the change only helps one narrow wording

### Hold for Review

Use when:

- the change touches unstable facts
- safety is preserved but evidence is weak
- promotion may be correct but source strength is mixed

### Accept Into Learning Stage

Use when:

- the change helps and does not yet qualify as stable truth
- the domain is still shifting
- the improvement needs more repetition

### Promote

Use when:

- the principle appears stable
- the benchmark support is broad enough
- the result survives rewording and applied cases

## Continuous Improvement Loop

Use this loop as the default operating cycle:

1. collect failures and near-misses
2. cluster them by failure type
3. choose the smallest fix surface
4. patch and canary
5. run regression
6. archive evidence
7. update the state report

## Degraded Mode Rules

If part of the stack is unhealthy:

- freeze automatic mutation
- keep retrieval read-only where possible
- keep runtime answering from the last known good workspace
- continue writing incidents and traces
- do not silently promote anything

## Mirai Example Mapping

For a paid-media agent such as `Mirai`:

- platform doctrine lives in the knowledge repo
- user-specific continuity lives in relational memory
- prior campaign reasoning lives in session search
- optimization patches live in the runtime workspace
- eval evidence determines whether paid-media behavior truly improved
