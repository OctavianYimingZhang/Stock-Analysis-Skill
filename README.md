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
- `references/angle-library.md`: reusable analysis angles distilled from the research corpus
- `references/source-policy.md`: source hierarchy, exclusions, and evidence rules
- `references/proprietary-data.md`: terminal-data gap handling and user request templates

## Default Behavior

- Single-stock deep dive by default
- Industry-chain and theme work only as context for the stock under review
- Final output follows the user's language when possible
- Tickers, filing names, and source names remain in their original language

## Install

Copy this directory into your Codex skills directory:

```bash
${CODEX_HOME:-$HOME/.codex}/skills/stock-analysis
```

Or clone the repository directly into that path.

## Validation

This skill passes:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py /path/to/stock-analysis
```

## License

No license file has been added yet. The repository is public, but reuse terms are not granted until a license is specified.
