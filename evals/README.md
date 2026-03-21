# Behavior Regression Evals

These evals test runtime gate behavior for `stock-analysis`.

## What They Check

- archetype routing
- commercial evidence layering
- capacity and milestone tagging
- regulatory, qualification, and legal gating
- semantic claim downgrades for moat, flywheel, network effect, and platform language
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

## New Coverage Areas

The suite also covers:

- `consumer_health_platform` claim-gate behavior
- `digital_bank_or_lender` rate-sensitivity gating
- `b2b_software_platform` legal-accounting quality gating
- `industry_chain_context` no-valuation behavior
- `resource_policy` study-standard, qualification-status, and inventory-realization layering
