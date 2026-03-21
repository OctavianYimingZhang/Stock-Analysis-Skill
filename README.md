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
- `references/report-digests.yaml`: offline section-level digests for the report corpus
- `references/source-policy.md`: source hierarchy, routers, exclusions, and evidence rules
- `references/proprietary-data.md`: terminal-data gap handling and hard valuation blocks
- `evals/`: frozen prompt-plus-fixture regression cases

## Default Behavior

- Single-stock deep dive by default
- Industry-chain and theme work only as context for the stock under review
- Final output follows the user's language when possible
- Tickers, filing names, and source names remain in their original language

## Example Prompts

- `Analyze TER after earnings and tell me whether valuation is supported by public sources alone.`
- `Analyze ACHR and focus on certification, manufacturing readiness, runway, and partner quality.`
- `Analyze IREN, but block valuation if consensus or dilution-stack inputs are incomplete.`
- `Analyze UUUU and ignore technical-analysis or self-media material.`

## Non-Investment-Advice Notice

This repository is for source-quality control, analysis structure, and evaluation design. It is not investment advice, not a solicitation, and not a substitute for your own legal, financial, or tax judgment.

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

## Contributing

Read `CONTRIBUTING.md` before opening a pull request. The short version:

- keep new claims source-led
- do not add self-media, technical-analysis, or uncited-number patterns
- update `evals/` whenever behavior changes
- keep runtime gates stricter, not looser

## Project Health

- `CONTRIBUTING.md`: contribution rules and review checklist
- `SECURITY.md`: how to report repository-security issues
- `.github/ISSUE_TEMPLATE/`: bug report and feature request templates
- `.github/workflows/validate.yml`: structural and fixture validation on push and pull request

## License

This repository is licensed under the MIT License. See `LICENSE` for the full text.
