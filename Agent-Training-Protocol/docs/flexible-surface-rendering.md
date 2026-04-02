# Flexible Surface Rendering

## Goal

Design surfaces that can present meaningful agent output without forcing every future output into a rigid UI shape.

## Core rule

The software should control layout.
The agent should control content.

This means:
- the agent should not write visual coordinates
- the agent may author ordered sections, labels, and messages
- the UI should render those sections in a consistent system

## Problem

Rigid surfaces often assume:
- one fixed field for rationale
- one fixed field for risk
- one fixed field for each platform
- one fixed field for every configuration block

This breaks when:
- the agent needs a new section
- one section grows much deeper than expected
- one platform needs more detail than another
- the same entity needs different review shapes over time

## Recommended pattern

Use section-driven rendering for complex agent-authored surfaces.

### Preferred model

The agent may return:
- ordered sections
- section title
- optional description
- fields
- field kind
- field tone

The UI renders:
- section container
- typography
- chips
- lists
- rows
- text blocks

### Suggested field kinds

- `text`
- `rows`
- `chips`
- `list`

These cover most product cases without overfitting the UI.

## Fallback rule

If agent-authored sections are not present yet:
- derive sections from structured canonical state
- keep those derived sections coherent and stable

This gives a safe transition path:
- early system: mostly derived
- mature system: increasingly agent-authored

## Benchmarks and observed reality

Surfaces should clearly separate:
- initial benchmark
- observed factual state

Rule:
- benchmark is hypothesis or expectation
- observed state is learned from real runtime behavior
- do not render benchmark copy as if it were factual evidence

## Recommended use cases

Section-driven rendering works especially well for:
- review surfaces
- canon review
- agent recommendations
- strategic summaries
- platform translation previews
- approval modals

It is less necessary for:
- simple factual tables
- raw logs
- compact execution dashboards

## Design rules

### 1. Separate content from chrome

Keep:
- visual layout in the app
- content blocks from the agent

### 2. Keep tones limited

Do not let every section invent its own color system.

Use a small set such as:
- neutral
- slate
- blue
- violet
- emerald
- danger

### 3. Keep labels human

The agent should avoid:
- internal keys
- debug terms
- generic labels like `risk_1`

### 4. Allow incomplete structures

A surface should still render well if:
- one section is missing
- one field is empty
- only one platform exists

### 5. Prefer ordered sections over giant prose

Long prose is harder to review and harder to compare.

Ordered sections make it easier to:
- scan
- approve
- compare variants
- evolve the schema later

## Minimal rendering contract

At minimum, a flexible surface should know:
- section order
- section title
- section tone
- field kind
- field content

Everything else can remain app-owned.

