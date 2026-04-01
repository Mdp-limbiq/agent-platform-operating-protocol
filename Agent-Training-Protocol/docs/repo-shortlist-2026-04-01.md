# Repo Shortlist for Training + Evals Templates

Date: `2026-04-01`

This note captures a practical shortlist of open-source repositories that can
help us build a reusable `training + evals + optional evolution` pipeline for
`Mirai` and later for other domains.

The goal here is not to pick a single magical framework.

The goal is to identify the best building blocks for:

- eval definitions
- regression runs
- multi-turn agent testing
- structured graders
- prompt or runtime optimization
- safe execution for tool-using agents

## Selection Criteria

The shortlist below favors repos that help with at least one of these:

1. reusable eval structure
2. multi-turn or stateful agent support
3. YAML or JSONL friendliness
4. CI and regression compatibility
5. agent or tool-use evaluation
6. active enough maintenance to be worth adopting
7. good fit for a domain-specific system like `NN-Mirai`

## Tier 1: Best Fit for Mirai

### 1. `UKGovernmentBEIS/inspect_ai`

Repo:

- [UKGovernmentBEIS/inspect_ai](https://github.com/UKGovernmentBEIS/inspect_ai)

Why it matters:

- strongest open-source backbone in this shortlist for serious agent evals
- explicitly supports prompt engineering, tool usage, multi-turn dialog, and
  model-graded evaluations
- better fit than simple prompt-testing tools if we want to evaluate agent
  trajectories later

Best use for us:

- main backbone for a future `Mirai` agent-eval harness
- especially valuable if we later test tool use, browser use, or sandboxed
  workflows

Tradeoff:

- heavier than lightweight YAML-first tools
- more framework to learn up front

### 2. `UKGovernmentBEIS/inspect_evals`

Repo:

- [UKGovernmentBEIS/inspect_evals](https://github.com/UKGovernmentBEIS/inspect_evals)

Why it matters:

- companion library of real eval implementations for `inspect_ai`
- useful more as a pattern library than as something we would adopt wholesale
- contains examples from coding, agent, and terminal-style evaluations

Best use for us:

- copy structure and conventions
- study how they package tasks, scorers, and sandboxes

Tradeoff:

- not a domain template by itself
- much broader than what `Mirai` needs right now

### 3. `promptfoo/promptfoo`

Repo:

- [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo)

Why it matters:

- fastest path for local regression gates and CI-friendly prompt testing
- declarative and easy to operationalize
- supports automated evals, multi-model comparisons, red teaming, and CI/CD
- repo claims evals run locally and integrates well with command-line workflows

Best use for us:

- quick regression layer on top of `Mirai` prompts and casebanks
- perfect for a first practical gate before adopting a heavier agent framework

Tradeoff:

- less opinionated about complex agent trajectory evaluation than `inspect_ai`
- stronger for prompt/app testing than for full agent environments

### 4. `langchain-ai/openevals`

Repo:

- [langchain-ai/openevals](https://github.com/langchain-ai/openevals)

Why it matters:

- excellent evaluator primitives
- good for structured outputs, tool calls, exact match, rubric judging, and
  multi-turn simulation
- especially relevant for `Mirai` because our evals often care about structured
  reasoning and trajectory-level grading, not only raw string matching

Best use for us:

- borrow or wrap evaluator logic
- use for structured graders and multi-turn simulation
- potentially a better evaluator library than a full top-level harness

Tradeoff:

- not a full opinionated benchmark system on its own
- better as a component than as the whole stack

## Tier 2: Strong Supporting Options

### 5. `confident-ai/deepeval`

Repo:

- [confident-ai/deepeval](https://github.com/confident-ai/deepeval)

Why it matters:

- very strong for LLM-unit-test style workflows
- good metric coverage
- familiar pytest-like mental model
- useful when we want fast test-case based evaluation around concrete prompts or
  app outputs

Best use for us:

- targeted component tests
- regression testing of individual behaviors
- fast experimentation with rubric or relevance metrics

Tradeoff:

- less naturally aligned than `inspect_ai` for future sandboxed agent evals
- can become metric-heavy without solving the full pipeline architecture

### 6. `letta-ai/letta-evals`

Repo:

- [letta-ai/letta-evals](https://github.com/letta-ai/letta-evals)

Why it matters:

- very attractive if we care about stateful agents and memory
- supports YAML configs, JSONL datasets, multi-turn conversations, per-turn
  grading, multi-model runs, and cached trajectories
- has a clean eval-kit feel instead of a benchmark-research feel

Best use for us:

- inspiration for stateful `Mirai` evals
- especially useful if memory behavior becomes a first-class eval target

Tradeoff:

- more tied to the Letta ecosystem than the others
- promising, but I would still prefer `inspect_ai` or `promptfoo` as our main
  backbone unless we lean hard into Letta-style agent structure

### 7. `openai/evals`

Repo:

- [openai/evals](https://github.com/openai/evals)

Why it matters:

- still one of the best public references for eval templates and registry shape
- supports basic and model-graded evals with JSON data and YAML parameters
- useful when we want canonical examples of how to structure an eval library

Best use for us:

- reference design
- template inspiration
- evaluation registry conventions

Tradeoff:

- more focused on the `OpenAI Evals` ecosystem than on broader agent-runtime
  orchestration
- helpful as a design reference, not my first choice as the main Mirai stack

## Tier 3: Optimization / Evolution Repos

These are useful later, once the benchmark is solid.

### 8. `stanfordnlp/dspy`

Repo:

- [stanfordnlp/dspy](https://github.com/stanfordnlp/dspy)

Why it matters:

- one of the strongest repos for building self-improving LM pipelines
- conceptually aligned with a future `Mirai` evolution layer
- especially interesting once we want to optimize prompts, demonstrations, or
  program structure against evals

Best use for us:

- later-stage optimization experiments
- compile or optimize specific `Mirai` reasoning modules

Tradeoff:

- not an eval-template repo first
- should come after benchmark discipline, not before

### 9. `microsoft/PromptWizard`

Repo:

- [microsoft/PromptWizard](https://github.com/microsoft/PromptWizard)

Why it matters:

- directly relevant for prompt optimization
- supports optimization without examples, with synthetic examples, or with
  training data
- practical if we want a bounded prompt-improvement loop later

Best use for us:

- prompt hardening after we have trustworthy cases
- controlled optimization for one subsystem at a time

Tradeoff:

- narrower than the full pipeline we need
- useful as a subcomponent, not as the top-level architecture

### 10. `zou-group/textgrad`

Repo:

- [zou-group/textgrad](https://github.com/zou-group/textgrad)

Why it matters:

- strong research inspiration for feedback-driven optimization
- relevant if we want to experiment with automated critique loops

Best use for us:

- research branch for optimization
- inspiration for future evolution of prompts or intermediate artifacts

Tradeoff:

- more researchy than operational
- not the right foundation for the first `Mirai` training pipeline

## Lower Priority / Caution

### `openai/simple-evals`

Repo:

- [openai/simple-evals](https://github.com/openai/simple-evals)

Useful because:

- very small and easy to understand

But caution:

- the repo README says on `2025-07` that it will no longer be updated for new
  models or benchmark results
- good as a lightweight reference implementation, not as a living foundation

### `microsoft/promptbench`

Repo:

- [microsoft/promptbench](https://github.com/microsoft/promptbench)

Useful because:

- good research reference around prompt robustness and adversarial evaluation

But caution:

- it is more benchmark-research oriented than pipeline-template oriented
- better as a reference for robustness testing than as the main Mirai stack

## Optional Sandbox Layer

If we later evaluate tool-using or code-executing agents, these become relevant:

- [UKGovernmentBEIS/aisi-sandboxing](https://github.com/UKGovernmentBEIS/aisi-sandboxing)
- [UKGovernmentBEIS/inspect_k8s_sandbox](https://github.com/UKGovernmentBEIS/inspect_k8s_sandbox)
- [UKGovernmentBEIS/inspect_proxmox_sandbox](https://github.com/UKGovernmentBEIS/inspect_proxmox_sandbox)

These are not needed for the first `Mirai` knowledge-eval pipeline, but they
matter if we later test agents that can browse, mutate files, or execute code.

## Recommended Stack for Mirai

If we optimize for practicality, not maximal novelty:

### Option A: Best balanced stack

1. `promptfoo` for fast local regressions and CI gating
2. `inspect_ai` as the long-term agent-eval backbone
3. `openevals` for structured graders and multi-turn evaluator helpers
4. `DSPy` or `PromptWizard` later for optimization loops

Why I like this:

- fast to start
- strong long-term ceiling
- flexible enough for both knowledge evals and future agent evals

### Option B: Heavier but cleaner agent-first stack

1. `inspect_ai`
2. `inspect_evals`
3. `aisi-sandboxing`
4. optional `DSPy`

Why I would choose this:

- if we already know `Mirai` will become a more tool-using, stateful agent with
  environments, traces, and safety constraints

Why I would not choose it first:

- slower ramp
- probably overkill for the current paid-media knowledge pipeline

### Option C: Simpler stateful-agent eval stack

1. `letta-evals`
2. `promptfoo`
3. optional `PromptWizard`

Why I would consider it:

- if we want a YAML/JSONL-first workflow with strong multi-turn support and
  easier stateful-agent abstractions

Why I would still rank it lower:

- less general than the `inspect_ai + promptfoo + openevals` combination

## My Recommendation

For `NN-Mirai` specifically, I would use:

1. `promptfoo` now
2. `openevals` selectively for graders
3. `inspect_ai` as the next serious backbone
4. `DSPy` or `PromptWizard` only after the eval registry is trusted

That sequencing preserves speed while keeping a clean path toward a stronger
agent-eval architecture later.

## Practical Next Step

If we adopt this shortlist, the next implementation move should be:

1. create a minimal `Mirai Evals Sandbox` repo or folder
2. port 5 to 10 existing paid-media cases into `promptfoo`
3. define one structured grader path inspired by `openevals`
4. reserve `inspect_ai` for a second phase focused on multi-turn and tool-use
