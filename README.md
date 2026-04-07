# Stock Analysis Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

Source-led fundamental stock analysis skill for AI coding agents. Covers global markets with explicit source-quality controls, gate-driven valuation logic, and a structured technical analysis appendix.

## Quick Start

Point your AI agent at this skill and prompt it:

```
Analyze TER after earnings and tell me whether valuation is supported by public sources alone.
```

```
Analyze ACHR and focus on certification, manufacturing readiness, runway, and partner quality.
```

```
Analyze uranium-chain context only and force a company bridge before any stock conclusion.
```

The skill will classify the company into an archetype, build mandatory gating tables, search authoritative sources, and produce a structured analysis with a technical structure appendix.

## What It Does

1. **Source-first analysis** — prioritizes issuer filings, exchange notices, regulators, government datasets, and official counterparty disclosures
2. **Gate-driven valuation** — blocks valuation when capital structure is unverified, commercial evidence is weak, or regulatory gates are unresolved
3. **Semantic claim controls** — prevents unearned labels like `moat`, `platform`, `data flywheel`, or `network effect` without minimum evidence
4. **Archetype routing** — adapts the analysis structure to the company type (mature, frontier, turnaround, fintech, healthcare, resource, etc.)
5. **Technical structure assessment** — appends a three-layer technical analysis (Murphy trend + Wyckoff volume-price + Nison candlestick) as a supplementary appendix, isolated from the fundamental body
6. **Evidence separation** — explicitly separates verified facts, inferences, scenario assumptions, and opinions

## Repository Structure

```
.
├── SKILL.md                              # Main skill instructions (§1-§9)
├── references/
│   ├── source-policy.md                  # Source hierarchy, market routers, exclusions
│   ├── angle-library.yaml                # Machine-readable archetype routing and gates
│   ├── angle-library.md                  # Human-readable angle guidance (26 companies)
│   ├── claim-gates.yaml                  # Semantic claim controls (moat, flywheel, etc.)
│   ├── report-digests.yaml               # Offline report digests and locators
│   ├── proprietary-data.md               # Terminal-data gap handling
│   └── technical-analysis-framework.md   # Murphy/Wyckoff/Nison methodology reference
├── evals/
│   ├── README.md                         # Eval case guide
│   ├── cases/                            # 18 YAML regression cases
│   └── fixtures/                         # Frozen source bundles (sanitized)
├── agents/
│   └── openai.yaml                       # UI metadata
├── .github/
│   ├── workflows/validate.yml            # CI checks
│   ├── pull_request_template.md
│   └── ISSUE_TEMPLATE/
├── CONTRIBUTING.md
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
└── LICENSE
```

## Archetypes

Each company is classified into one archetype that determines required sections and gates:

| Archetype | Use When | Key Sections |
|-----------|----------|--------------|
| `mature` | Established, profitable companies | business logic, operating metrics, valuation |
| `frontier` | Pre-revenue or early-revenue | certification, cash runway, dilution ladder |
| `turnaround` | Distressed or restructuring | maturity wall, refi path, covenant headroom |
| `consumer_health_platform` | DTC health/wellness | retention, regulatory distribution, fulfillment |
| `b2b_software_platform` | Enterprise SaaS | NRR, SBC, legal/accounting quality |
| `digital_bank_or_lender` | Bank charter holders | funding stack, NIM, capital ratios |
| `lending_marketplace` | Non-bank lending platforms | securitization, partner funding, take rate |
| `provider_reimbursement` | Healthcare services | reimbursement mechanics, policy sensitivity |
| `resource_policy` | Mining, energy, critical minerals | permits, offtake, processing capacity |
| `industry_chain_context` | Sector/theme analysis only | supply-demand, no standalone valuation |

## Gate Tables

Three mandatory gating tables are built before any thesis writing:

- **Commercial Evidence Table** — tags each claim with contract form (`mou` through `recognized_revenue`) and valuation usability
- **Capacity and Milestone Table** — distinguishes planned vs. operational, uncontracted vs. contracted
- **Regulatory / Qualification / Legal Gate Table** — tracks approval status, economic dependency, and next observables

## Technical Structure Assessment (§9)

The skill appends a three-layer technical analysis as a supplementary appendix:

| Layer | Source | What It Covers |
|-------|--------|----------------|
| Layer 1 | Murphy | Trend structure, support/resistance, chart patterns, moving averages |
| Layer 2 | Wyckoff | Market phase (accumulation/distribution), volume-price analysis, effort vs. result |
| Layer 3 | Nison | Candlestick patterns at key levels, confirmation status |

This section cannot override fundamental conclusions or unblock a blocked valuation. It is skipped for `industry_chain_context`, pre-IPO, and pre-de-SPAC targets.

## Validation

### YAML Syntax Check

```bash
python3 -c "import yaml; yaml.safe_load(open('references/angle-library.yaml'))"
python3 -c "import yaml; yaml.safe_load(open('references/claim-gates.yaml'))"
```

### Behavior Regression

Use the frozen cases under `evals/cases/` with their matching fixture directories. Each case asserts:

- correct archetype selected
- required tables and tags present
- source router selected correctly
- valuation allowed or blocked for the correct reason
- forbidden evidence or trading language absent

See `evals/README.md` for the full eval case guide.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for ground rules, branching strategy, and PR requirements.

## License

MIT License. See [LICENSE](LICENSE).
