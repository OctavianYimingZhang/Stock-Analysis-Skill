# Evals

This directory holds frozen prompt-plus-fixture regression cases for `stock-analysis`.

## Goal

Test gate behavior, source routing, archetype routing, and valuation blocking logic. Do not use this suite to score prose quality.

## Files

- `cases.yaml`: case definitions, fixture bundles, expected archetypes, required gates, and forbidden outputs

## What Each Case Must Assert

- selected archetype
- required tables or tags present
- source router selected correctly
- valuation allowed or blocked for the correct reason
- forbidden evidence or trading language absent

## Structural vs Behavior Validation

Structural validation:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py /path/to/stock-analysis
```

Behavior regression:

- load the fixture bundle for a case
- run the case prompt through the skill
- check only the required assertions in `cases.yaml`

## Fixture Guidance

- Prefer frozen official-source excerpts or snapshots over live-web outputs.
- Include user-provided terminal tables only in cases that explicitly test terminal-data blocking or unblocking.
- Keep fixtures minimal so failures are easy to localize.
