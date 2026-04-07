# Contributing

## Purpose

This repository hardens an AI skill for source-led stock analysis. Contributions should improve:

- source quality controls
- runtime gates
- archetype routing
- valuation blocking logic
- technical structure methodology
- evaluation coverage

Do not contribute trading tips, hype language, or weak-source material.

## Ground Rules

- Prefer issuer filings, exchange disclosures, regulators, governments, and official counterparties.
- Do not add Discord, YouTube, self-media PDFs, content farms, or uncited numbers as evidence sources.
- Do not weaken valuation gates for convenience.
- Do not add target-price logic that depends on unverified dilution, debt, terminal-only consensus, or uncontracted capacity.
- Keep the research corpus as angle guidance only, never as a factual source base.
- Technical analysis belongs exclusively in §9 — do not mix it into the fundamental body.

## Branching Strategy

- `main` — stable, release-ready. All PRs target `main`.
- `feat/<name>` — feature branches for new gates, routers, archetypes, or eval cases.
- `fix/<name>` — bugfix branches for broken gates or wrong routing.
- `docs/<name>` — documentation-only changes.

Create your branch from `main`, keep it focused, and open a PR when ready.

## Local Validation

Before opening a PR, confirm:

### 1. YAML files parse

```bash
python3 -c "import yaml; yaml.safe_load(open('references/angle-library.yaml')); print('OK')"
python3 -c "import yaml; yaml.safe_load(open('references/claim-gates.yaml')); print('OK')"
python3 -c "import yaml; yaml.safe_load(open('references/report-digests.yaml')); print('OK')"
```

### 2. Eval cases parse

```bash
for f in evals/cases/*.yaml; do
  python3 -c "import yaml; yaml.safe_load(open('$f')); print('OK: $f')"
done
```

### 3. No forbidden patterns in fundamental body

Search for accidental leakage of technical analysis into §1-§7:

```bash
grep -n "wyckoff_phase\|candlestick\|golden.cross\|death.cross\|stop.loss\|position.siz" SKILL.md
```

Lines should only appear in §8 (the ban statement) and §9 (the appendix).

## What To Update When You Change Behavior

| Change Type | Files to Update |
|-------------|-----------------|
| Runtime behavior | `SKILL.md`, relevant `evals/cases/` |
| Routing or gates | `references/*.yaml`, `evals/cases/` |
| Source hierarchy | `references/source-policy.md` |
| Technical analysis | `references/technical-analysis-framework.md`, `SKILL.md` §9 |
| External docs | `README.md` |
| All changes | `CHANGELOG.md` |

## Pull Request Requirements

- Explain the behavior change in one paragraph.
- State whether the change makes the skill stricter, looser, or only clearer.
- Add or update at least one eval case when runtime behavior changes.
- Confirm YAML files parse and no forbidden patterns leak.
- Use the PR template — fill in all sections.

## Good Contribution Examples

- Add a new market router with official filing systems and sector regulators.
- Tighten a valuation gate that previously allowed weak denominators.
- Add a new eval case for a failure mode the current suite misses.
- Improve the Wyckoff or candlestick framework with additional pattern detail.
- Add a new archetype with required sections and gates.

## Bad Contribution Examples

- Add self-media or social content as an accepted source.
- Add position sizing, stop-loss, or trading plan templates.
- Add target-price framing without capital-structure verification.
- Loosen blocked-output behavior because a narrative "sounds right."
- Mix technical analysis into the fundamental body (§1-§7).

## YAML Style Guide

When editing `.yaml` files:

- Use 2-space indentation.
- Use `snake_case` for all field names.
- Keep lists on separate lines (not inline) when they have more than 3 items.
- Add a comment above non-obvious fields.
- Maintain alphabetical order within taxonomy lists.
