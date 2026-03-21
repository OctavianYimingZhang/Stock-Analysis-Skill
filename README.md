# Stock Analysis Skill

Codex skill for source-led fundamental stock analysis across global markets.

## What It Does

- Analyzes public companies with authoritative sources first
- Prioritizes issuer filings, exchange notices, regulators, government datasets, and official counterparty disclosures
- Separates verified facts, inference, scenario assumptions, and opinions
- Stops and asks the user for Bloomberg, FactSet, or CapIQ-style data when those fields are required and no authoritative public source exists
- Rejects low-authority evidence such as technical analysis, self-media, Discord, YouTube, and uncited numbers

## Repository Contents

- `SKILL.md`: main skill instructions
- `agents/openai.yaml`: UI metadata
- `references/angle-library.md`: human-readable angle library
- `references/angle-library.yaml`: machine-readable angle and gate library
- `references/claim-gates.yaml`: semantic claim controls for `moat`, `platform`, `data_flywheel`, and `network_effect`
- `references/report-digests.yaml`: offline section-level digests for the report corpus
- `references/source-policy.md`: source hierarchy, routers, exclusions, and evidence rules
- `references/proprietary-data.md`: terminal-data gap handling and hard valuation blocks
- `evals/`: frozen prompt-plus-fixture regression cases

## Default Behavior

- Single-stock deep dive by default
- Industry-chain and theme work only as context for the stock under review
- Final output follows the user's language when possible
- Tickers, filing names, and source names remain in their original language

## Archetypes

- `mature`
- `frontier`
- `turnaround`
- `consumer_health_platform`
- `b2b_software_platform`
- `digital_bank_or_lender`
- `lending_marketplace`
- `provider_reimbursement`
- `resource_policy`
- `industry_chain_context`

## Gate Tables

The runtime workflow now uses three mandatory gate tables when relevant:

- `Commercial Evidence Table`
- `Capacity and Milestone Table`
- `Regulatory_Qualification_Legal_Gate_Table`

## Example Prompts

- `Analyze TER after earnings and tell me whether valuation is supported by public sources alone.`
- `Analyze ACHR and focus on certification, manufacturing readiness, runway, and partner quality.`
- `Analyze IREN, but block valuation if consensus or dilution-stack inputs are incomplete.`
- `Analyze UUUU and ignore technical-analysis or self-media material.`
- `Analyze HIMS, but do not call it a flywheel or moat unless retention or cross-sell evidence supports it.`
- `Analyze uranium-chain context only and force a company bridge before any stock conclusion.`

## Validation

This repository uses two validation layers.

### 1. Structural Validation

Use `quick_validate.py` to confirm the skill folder is well-formed.

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py /path/to/stock-analysis
```

This checks structure only. It does not test runtime behavior.

### 2. Behavior Regression

Use the frozen cases under `evals/cases/` with their matching fixture directories under `evals/fixtures/`.

Each case should assert only:

- selected archetype
- required tables or tags present
- source router selected correctly
- valuation allowed or blocked for the correct reason
- forbidden evidence or trading language absent

The eval suite is intended to test gate behavior, source routing, and valuation blocking logic, not prose style.

## Evals Layout

- `evals/cases/`: YAML case definitions
- `evals/fixtures/`: frozen official-source bundle directories
- `evals/README.md`: how to review the cases and what each case is asserting

Current coverage includes commercial layering, capacity-state gating, semantic claim downgrades, legal-accounting quality, industry-chain context-only routing, and resource study or inventory layering.

## License

This repository is licensed under the MIT License. See `LICENSE` for the full text.
