---
name: stock-analysis
description: Fundamental stock analysis for public companies using authoritative sources first and explicit source-quality controls. Use when Codex needs to analyze a stock, ticker, public company, peer set, thesis update, post-earnings change, or industry context for a stock across global markets. Prioritize issuer filings, exchange notices, regulators, government or official industry datasets, and user-provided Bloomberg/FactSet/CapIQ data when needed.
---

# Stock Analysis

## Overview

Analyze a public company from verified evidence, not from memory or recycled writeups. Use this skill to turn a user request like "analyze this stock" into a source-led fundamental analysis with explicit data sufficiency, citations, and hard stops when proprietary data are missing.

## Default Scope

- Default to a single-stock deep dive.
- Use industry-chain or theme analysis only as context for the stock under review.
- Write the final answer in the user's language when possible. Keep tickers, filing names, source names, and regulatory body names in their original form.
- Treat the provided research corpus as an angle library only. Do not inherit factual claims from it without re-sourcing them from authoritative sources at runtime.

## Mandatory Workflow

### 1. Scope the request

- Identify the company, ticker, exchange, and analysis scope.
- Resolve ambiguity before doing valuation or peer work. If the ticker or exchange is unclear and cannot be resolved from authoritative sources, ask a short clarifying question.
- Classify the company into an analysis archetype before collecting data:
  - Mature operating company
  - Frontier or pre-revenue company
  - Platform, software, or fintech company
  - Resource, energy, or policy-driven company
  - Turnaround or balance-sheet repair case
- Read [angle-library.md](./references/angle-library.md) when selecting the primary angle and likely evidence set.

### 2. Search authoritative sources first

- Search online before relying on memory.
- Start with market-specific official sources and issuer materials:
  - Issuer filings and investor relations
  - Exchange notices and filing systems
  - Regulators and government databases
  - Official partner, customer, or counterparty disclosures when directly relevant
- Read [source-policy.md](./references/source-policy.md) at the start of every analysis.

### 3. Build an evidence ledger

- For every material quantitative claim, capture:
  - value
  - date or period
  - source
  - source class
- Separate content into four buckets while you work:
  - Verified facts
  - Inference from verified facts
  - Scenario assumptions
  - Opinions or judgments
- Do not let inference or assumptions drift into fact statements.
- Omit any number that cannot be tied to an authoritative source or a clearly labeled user-provided proprietary dataset.

### 4. Detect proprietary data gaps early

- Before writing the valuation or market-data section, check whether the missing fields require Bloomberg, FactSet, Capital IQ, LSEG, or a similar terminal product.
- Read [proprietary-data.md](./references/proprietary-data.md) whenever you need:
  - forward consensus
  - historical valuation bands
  - peer-screen tables
  - analyst revision or target distributions
  - ownership or flows snapshots
  - debt pricing or yield tables
  - certain commodity or industry time series not available from official public datasets
- If those data are required and no authoritative public source exists, stop and ask the user for the exact fields. Do not fill gaps with finance portals, self-media, blogs, or uncited estimates.

### 5. Write the analysis in a fixed structure

- Start with a `Data Sufficiency` note:
  - what was verified
  - what was inferred
  - what is blocked by missing proprietary data
- Then write:
  - Core thesis
  - Business model and segment structure
  - Industry and policy context
  - Operating metrics and milestones
  - Financial quality, liquidity, and capital structure
  - Valuation
  - Risks
  - Missing-data request, if blocked
- In the valuation section, always state:
  - method
  - period
  - numerator and denominator
  - capital-structure convention
  - major assumptions
  - source basis for inputs

### 6. Run quality gates before answering

- Reject excluded sources and patterns listed in [source-policy.md](./references/source-policy.md).
- Do not use technical analysis, chart patterns, position sizing, stop-loss, stop-gain, or trading plans in the main output.
- Do not output a target price unless the user explicitly asks for one and the valuation method, assumptions, and data quality are sufficient.
- Do not write claims like "institutions are buying aggressively" or "consensus expects" unless the underlying dataset is cited or supplied by the user.
- If the evidence is insufficient to verify a claim, leave it out or label it as uncertain.

## Output Rules

- Be direct and evidence-led.
- Prefer primary and official sources over summaries.
- Cite the source class for every material figure.
- State when a conclusion is an inference rather than a disclosed fact.
- If a request cannot be completed without proprietary data, ask for the missing data instead of silently downgrading the analysis.

## Reference Files

- Read [angle-library.md](./references/angle-library.md) to select the right analysis angle and avoid reusing weak patterns from the corpus.
- Read [source-policy.md](./references/source-policy.md) for source hierarchy, allowed evidence, and exclusions.
- Read [proprietary-data.md](./references/proprietary-data.md) whenever valuation or market-data work might depend on terminal-only fields.
