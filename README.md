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

## Validation

Structural validation:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py /path/to/stock-analysis
```

Behavior regression:

- read `evals/README.md`
- run the frozen prompt-plus-fixture cases in `evals/cases.yaml`
- verify archetype routing, required tables, source routing, valuation blocking, and forbidden-output rejection

## License

No license file has been added yet. The repository may be public, but reuse terms are not granted until a license is specified.
