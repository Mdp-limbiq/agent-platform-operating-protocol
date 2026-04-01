# Operations: Scheduler and Watcher

## Goal

Run the training stack as an actual operating system for the agent, not as a
set of ad hoc scripts.

This means:

- named recurring jobs
- clear job ownership
- health checks
- incident classification
- safe repair actions
- graceful degradation

## Operational Components

### Scheduler

The scheduler runs:

- intake freshness checks
- index sync jobs
- session consolidation
- eval suites
- backups
- report generation

This can be implemented with:

- `cron`
- `launchd`
- `systemd timers`
- a local job runner if preferred

### Watcher

The watcher monitors:

- service health
- stale indexes
- failed eval jobs
- backup recency
- disk pressure
- model endpoint availability
- runtime error spikes

It should be deterministic first and optionally LLM-assisted second.

### Repair Executor

The repair executor performs only allowlisted actions such as:

- restarting a service
- re-running an idempotent job
- rebuilding an index
- re-embedding changed files
- rolling back the runtime workspace to the last known good snapshot
- switching the system into degraded read-only mode

## Recommended Job Cadence

Use this as a strong default and then adapt by domain volatility.

| Job | Recommended cadence | Purpose | Needs LLM |
| --- | --- | --- | --- |
| `health_watch` | every 5 minutes | detect failing services and stale dependencies | no |
| `session_consolidation` | hourly | summarize new sessions into episodic and relational candidates | yes |
| `index_sync` | every 6 hours | update retrieval index for changed approved files | embeddings yes, BM25 no |
| `freshness_audit` | daily | detect stale source areas and flag domains needing re-verification | no |
| `smoke_eval` | daily | ensure the runtime still answers safely | runtime yes |
| `targeted_regression` | nightly | test changed domains or recent patch surfaces | runtime yes |
| `full_regression` | weekly | compare the full benchmark against baseline | runtime yes |
| `promotion_digest` | weekly | prepare review packet for possible promotions | optional |
| `backup_snapshot` | daily | snapshot knowledge, reports, runtime, and exports | no |
| `restore_drill` | monthly | verify that backups actually restore | no |

## Example Cron Schedule

```cron
*/5 * * * *      python3 scripts/ops/watchdog.py --mode health
7 * * * *        python3 scripts/ops/consolidate_sessions.py
17 */6 * * *     python3 scripts/ops/sync_index.py
30 2 * * *       python3 scripts/ops/freshness_audit.py
0 3 * * *        python3 scripts/run_eval.py --suite smoke
30 3 * * *       python3 scripts/run_eval.py --suite regression_minimum
0 4 * * 1        python3 scripts/run_eval.py --suite weekly_full
30 4 * * 1       python3 scripts/ops/build_promotion_digest.py
0 2 * * *        python3 scripts/ops/backup_snapshot.py
0 6 1 * *        python3 scripts/ops/restore_drill.py
```

## Recommended Watcher Signals

### Service Health

- runtime adapter health
- retrieval service health
- relational memory health
- trace store health
- scheduler heartbeat freshness

### Data Freshness

- knowledge areas with expired freshness windows
- retrieval index lag versus the repo
- missing embeddings for changed files
- missing trace uploads

### Quality Signals

- repeated failures in the same suite
- failure spikes after a runtime patch
- tool errors concentrated in one service
- unusual drops in answer completeness

### Resource Signals

- disk almost full
- large backup drift
- runaway logs
- model service unavailable or overloaded

## Watcher Decision Ladder

1. detect a signal
2. collect basic local evidence
3. classify the incident family
4. check whether the action is allowlisted
5. apply the smallest safe repair
6. verify the repair
7. log the incident and outcome
8. escalate if verification fails

## Incident Families

### `service_down`

Examples:

- `QMD` not responding
- `Honcho` unreachable
- trace store unavailable

Typical repair:

- restart service
- re-run health check
- switch to degraded mode if unavailable after retries

### `index_drift`

Examples:

- knowledge repo changed but the retrieval index is stale
- embeddings missing for new documents

Typical repair:

- run index sync
- force re-embed changed paths only

### `job_failure`

Examples:

- smoke eval job exited non-zero
- session consolidation crashed

Typical repair:

- inspect recent logs
- retry once if idempotent
- create incident record

### `runtime_regression`

Examples:

- canary suite passed but nightly suite dropped
- tool error rate spiked after workspace mutation

Typical repair:

- rollback runtime workspace
- freeze automatic mutation
- queue a diagnosis packet for review

### `backup_risk`

Examples:

- backup snapshot too old
- restore drill failed

Typical repair:

- force new snapshot
- block promotion until restore health is green

## Watcher and LLM Usage

### Should not require an LLM

- heartbeat checks
- file age checks
- endpoint health checks
- restart logic
- index lag detection
- backup recency checks
- rollback execution

### May use an LLM optionally

- incident summarization for humans
- clustering similar failures
- suggesting likely root-cause areas
- proposing a draft patch candidate

Do not make repair execution depend on an LLM.

## Safe Auto-Remediation Rules

Watcher auto-remediation is allowed only for:

- restarts
- retries of idempotent jobs
- index rebuilds
- cache cleanup
- re-embedding changed files
- runtime rollback to a known-good snapshot
- degraded-mode switching

Watcher auto-remediation is not allowed for:

- editing canon
- editing policy
- promoting knowledge
- deleting primary data
- applying unreviewed high-impact prompt rewrites

## Degraded Modes

### Retrieval Degraded Mode

If semantic search is unavailable:

- keep BM25 if available
- keep runtime read-only
- mark answers as lower-confidence internally

### Memory Degraded Mode

If relational memory is unavailable:

- continue serving from knowledge and session search
- queue relational writes for later replay if supported

### Eval Degraded Mode

If the main model backend is unavailable:

- suspend mutation jobs
- keep backups and freshness audits running
- keep watcher active

## Runbook Outline

Each deployment should define scripts for:

- `doctor`
- `restart_service`
- `sync_index`
- `reembed_changed`
- `run_smoke_eval`
- `rollback_workspace`
- `backup_snapshot`
- `restore_drill`

These scripts should be callable by both a human operator and the watcher.
