# Operating Rhythm

## Per Intake Batch

1. add or update sources
2. distill notes into learning-stage files
3. record what changed
4. run smoke evals

## Per Training Wave

1. define the wave scope
2. produce the wave brief
3. update the casebank
4. run regression minimum
5. run wave-specific suites
6. record state summary

## Per Hardening Pass

Use hardening passes when:

- one suite passes but stays compressed
- a domain concept is correct but not explicit enough
- the agent gives good answers for the wrong reasons

Outputs:

- targeted anchors
- stronger short-form wording
- more precise case coverage

## Per Runtime Orchestration Cycle

Use this cycle when the system has recurring or event-driven operational work.

1. evaluate the trigger or cadence
2. run the deterministic job
3. gather evidence
4. decide whether an agent task is necessary
5. route the task into the agent work queue
6. let the agent write output, recommendation, or proposal
7. route proposals to human review when required
8. apply change only after the proper boundary is crossed

## Promotion Cadence

Promote only when:

- multiple suites agree
- freshness risk is understood
- the principle is stable across several prompts
- the result is not dependent on one narrow wording

## Review Questions

At the end of each cycle ask:

1. did retrieval get sharper or just noisier
2. did reasoning improve or only verbosity
3. did safety and boundaries stay intact
4. did the agent become more tool-drifty
5. is the improvement domain truth or only runtime convenience
6. did a task, recommendation, or proposal get collapsed into the wrong object
7. did the system keep clock ownership, or did the agent implicitly self-schedule
