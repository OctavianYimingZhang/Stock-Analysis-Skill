# Contributing

## Purpose

This repository hardens a Codex skill for source-led stock analysis. Contributions should improve:

- source quality controls
- runtime gates
- archetype routing
- valuation blocking logic
- evaluation coverage

Do not contribute trading tips, hype language, or weak-source material.

## Ground Rules

- Prefer issuer filings, exchange disclosures, regulators, governments, and official counterparties.
- Do not add Discord, YouTube, self-media PDFs, content farms, or uncited numbers as evidence sources.
- Do not weaken valuation gates for convenience.
- Do not add target-price logic that depends on unverified dilution, debt, terminal-only consensus, or uncontracted capacity.
- Keep the research corpus as angle guidance only, never as a factual source base.

## What To Update When You Change Behavior

- Update `SKILL.md` when runtime behavior changes.
- Update `references/*.md` or `references/*.yaml` when routing, gates, or digests change.
- Update `evals/cases/` when a change affects gate behavior, routing, or blocked-output rules.
- Update `README.md` when external usage or validation workflow changes.

## Pull Request Checklist

- Explain the behavior change in one paragraph.
- State whether the change affects:
  - archetype routing
  - commercial evidence gating
  - capacity-state gating
  - valuation blocking
  - source routing
- Add or update at least one eval case when runtime behavior changes.
- Confirm the repository still passes:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py /path/to/stock-analysis
```

- Confirm all YAML files still parse.

## Good Contribution Examples

- Add a new market router with official filing systems and sector regulators.
- Tighten a valuation gate that previously allowed weak denominators.
- Add a new golden case for a failure mode the current suite misses.
- Improve report digests to reduce runtime rereading without inventing facts.

## Bad Contribution Examples

- Add self-media or social content as an accepted source.
- Add technical-analysis templates.
- Add target-price framing without capital-structure verification.
- Loosen blocked-output behavior because a narrative “sounds right.”
