# Behavior Regression Evals

These evals test runtime gate behavior for `stock-analysis`.

## What They Check

- archetype routing
- commercial evidence layering
- capacity and milestone tagging
- source-router selection
- valuation blocking logic
- rejection of forbidden evidence patterns

## What They Do Not Check

- prose quality
- formatting preferences
- live-web freshness

## Directory Layout

- `cases/`: one YAML file per regression case
- `fixtures/`: one directory per case family for frozen official-source bundles

## Review Rule

A case passes only if the output behavior matches the case assertions. If the skill produces a polished answer but violates a gate, the case fails.
