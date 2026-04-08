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
- §9 Technical Structure Assessment isolation and three-layer structure

## What They Do Not Check

- prose quality
- formatting preferences
- live-web freshness

## Directory Layout

- `cases/`: one YAML file per regression case
- `fixtures/`: one directory per case family for frozen official-source bundles (see `fixtures/README.md`)

## Case Structure

Each YAML case file contains:

```yaml
id: unique-case-id
title: "Human-readable title"
description: >
  What this case tests and why it matters.

fixture_dir: fixtures/<family>

input:
  ticker: XXXX
  archetype: <archetype>
  user_request: "The prompt to test"

assertions:
  - type: <assertion_type>
    rule: "What must be true"

notes:
  - "Additional context for reviewers"
```

## Assertion Types

| Type | Description |
|------|-------------|
| `archetype_match` | Output must classify the company as the expected archetype |
| `table_present` | A specific gating table must appear in the output |
| `tag_present` | A specific tag or label must appear |
| `valuation_allowed` | Valuation section produces a numeric conclusion |
| `valuation_blocked` | Valuation is blocked with a stated reason |
| `source_router` | The correct source router is selected |
| `forbidden_output` | Specific patterns must NOT appear in the output |
| `forbidden_in_section` | Patterns must not appear in specific sections |
| `forbidden_everywhere` | Patterns must not appear anywhere |
| `section_present` | Named sections must exist |
| `section_order` | Sections must appear in a specific order |
| `text_present` | Specific text must appear |
| `logical_gate` | A logical condition must hold |
| `archetype_skip` | A section must be absent for a specific archetype |

## Review Rule

A case passes only if the output behavior matches the case assertions. If the skill produces a polished answer but violates a gate, the case fails.

## Coverage Areas

The suite covers:

- mature archetype routing and valuation
- frontier archetype with certification and cash-runway gates
- turnaround archetype with debt and maturity-wall gates
- commercial evidence layering with contract-form taxonomy
- capacity-state gating with monetization status
- semantic claim gates (moat, flywheel, network effect, platform)
- source-router selection for US and non-US markets
- valuation hard gates (dilution stack, debt stack, share count)
- `consumer_health_platform` claim-gate behavior
- `digital_bank_or_lender` rate-sensitivity gating
- `b2b_software_platform` legal-accounting quality gating
- `industry_chain_context` no-valuation behavior
- `resource_policy` study-standard, qualification-status, and inventory-realization layering
- §9 Technical Structure Assessment appendix isolation, three-layer structure, and archetype skip rules
- Revenue quality decomposition with pass-through identification and core margin reporting
- Earnings quality assessment with GAAP-to-adjusted bridge and SBC impact disclosure
- Cash flow decomposition with maintenance vs. growth capex and working capital analysis

## Adding a New Case

1. Create a new YAML file in `cases/` following the structure above
2. Add a fixture directory if source data is needed
3. Define assertions that test gate behavior, not prose
4. Update this README if the case covers a new area
5. Update `CHANGELOG.md`
