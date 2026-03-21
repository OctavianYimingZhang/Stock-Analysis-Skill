---
name: stock-analysis
description: Fundamental stock analysis for public companies using authoritative sources first and explicit source-quality controls. Use when Codex needs to analyze a stock, ticker, public company, peer set, thesis update, post-earnings change, or industry context for a stock across global markets. Prioritize issuer filings, exchange notices, regulators, government or official industry datasets, and user-provided Bloomberg/FactSet/CapIQ data when needed.
---

# Stock Analysis

## Overview

Analyze a public company from verified evidence, not from memory or recycled writeups. This skill is gate-driven: it must block weak commercial evidence, untagged capacity claims, incomplete capital-structure work, and terminal-only valuation inputs that the user has not supplied.

## Default Scope

- Default to a single-stock deep dive.
- Use industry-chain or theme analysis only as context for the stock under review.
- Write the final answer in the user's language when possible. Keep tickers, filing names, source names, and regulatory body names in their original form.
- Treat the research corpus as an angle library only. Do not inherit factual claims from it without re-sourcing them from authoritative sources at runtime.

## Mandatory Workflow

### 1. Scope the request

- Identify the company, ticker, exchange, and analysis scope.
- Resolve ambiguity before valuation or peer work. If ticker or exchange is unclear and cannot be resolved from authoritative sources, ask a short clarifying question.
- Classify the company into one archetype before building the thesis:
  - `mature`
  - `frontier`
  - `turnaround`
  - `platform_fintech`
  - `resource_policy`
- Read [angle-library.md](./references/angle-library.md) for human guidance and [angle-library.yaml](./references/angle-library.yaml) for runtime fields.
- Read [report-digests.yaml](./references/report-digests.yaml) for offline report summaries. Do not reread the raw research corpus at runtime.

### 2. Build the mandatory gating tables before writing a thesis

Create both tables whenever the stock has commercial claims, milestones, capacity claims, deployments, facilities, fleets, satellites, rigs, GPUs, EH/s, MW, manufacturing lines, project pipelines, or contract language.

#### Commercial Evidence Table

For each material commercial claim, record:

- `claim`
- `source_side`: `issuer_only | bilateral | regulator`
- `contract_form`: `mou | pilot | framework | commercial_agreement | binding_po | backlog | recognized_revenue`
- `disclosed_value`: `yes | no`
- `valuation_usability`: `no | limited | yes`

Hard rules:

- `mou`, `pilot`, `framework`, and management aspiration are not valuation denominators.
- `issuer_only` evidence is weaker than bilateral or regulator-backed evidence. If bilateral or regulator evidence should exist and is missing, downgrade confidence.
- Only `binding_po`, `backlog`, or `recognized_revenue` may be treated as strong economic visibility by default.

#### Capacity and Milestone Table

For each material capacity, deployment, or infrastructure claim, record:

- `metric`
- `status`: `planned | ordered | under_construction | mechanically_complete | ramping | operational`
- `monetization_status`: `uncontracted | partially_contracted | contracted`
- `date_or_in_service_date`

Hard rules:

- `planned`, `ordered`, `under_construction`, or `uncontracted` capacity cannot be used as a valuation denominator.
- Distinguish physical completion from commercial monetization. `operational` is not the same as `contracted`.

### 3. Search authoritative sources first

- Search online before relying on memory.
- Start with market-specific official sources and issuer materials:
  - issuer filings and investor relations
  - exchange notices and filing systems
  - regulators and government databases
  - official partner, customer, or counterparty disclosures when directly relevant
- For commercial claims, seek bilateral confirmation when possible.
- Read [source-policy.md](./references/source-policy.md) at the start of every analysis.

### 4. Build an evidence ledger

For every material quantitative claim, capture:

- value
- date or period
- source
- source class

Separate content into four buckets while you work:

- verified facts
- inference from verified facts
- scenario assumptions
- opinions or judgments

Do not let inference or assumptions drift into fact statements.

### 5. Detect proprietary data and capital-structure gaps early

- Before writing valuation, verify the capital structure from authoritative disclosures.
- Read [proprietary-data.md](./references/proprietary-data.md) whenever valuation, ownership, consensus, peer-multiple, or debt-market work is involved.
- If the user has not supplied terminal-only data required for peer multiples, valuation bands, or consensus, allow scenario framing only.
- If fully diluted share count, dilution stack, debt stack, or net-debt bridge is incomplete, block valuation.

### 6. Write the analysis as base structure plus archetype routing

Start with a `Data Sufficiency` note:

- what was verified
- what was inferred
- what is blocked by missing proprietary data
- what is blocked by weak commercial or capacity evidence

Then write the base structure:

- Core thesis
- Business model and segment structure
- Industry and policy context
- Operating metrics and milestones
- Financial quality, liquidity, and capital structure
- Valuation or scenario framing
- Risks
- Missing-data request, if blocked

Add archetype-specific mandatory sections:

#### `frontier`

- certification status
- commercialization gates
- cash runway
- dilution ladder
- partner quality

#### `turnaround`

- maturity wall
- refi path
- interest burden
- covenant headroom
- asset-sale dependency

#### `platform_fintech`

- funding stack
- credit quality
- partner concentration
- ABS, deposit, or funding-source dependence
- cohort or unit economics

#### `resource_policy`

- permit path
- offtake
- realized pricing
- processing capacity
- working capital

#### `mature`

- business logic
- operating metrics
- customers and channels
- orders or backlog
- capital structure
- valuation
- risks

In the valuation section, always state:

- method
- period
- numerator and denominator
- capital-structure convention
- major assumptions
- source basis for inputs

### 7. Run quality gates before answering

- Reject excluded sources and patterns listed in [source-policy.md](./references/source-policy.md).
- Do not use technical analysis, chart patterns, position sizing, stop-loss, stop-gain, or trading plans in the main output.
- Do not output a target price unless the user explicitly asks for one and the valuation section clears all hard gates.
- Block valuation if:
  - fully diluted share count is unverified
  - any part of the dilution stack is unverified
  - the debt stack or net-debt bridge is unverified
  - the denominator depends on `mou`, `pilot`, `framework`, management aspiration, planned capacity, or uncontracted capacity
  - terminal-only consensus or peer data are required and the user has not provided them
- If valuation is blocked, downgrade to scenario framing and ask for the exact missing fields.
- If evidence is insufficient to verify a claim, leave it out or label it as uncertain.

## Output Rules

- Be direct and evidence-led.
- Prefer primary and official sources over summaries.
- Cite the source class for every material figure.
- State when a conclusion is an inference rather than a disclosed fact.
- If commercial evidence or capacity status is not investment-grade, block valuation rather than forcing a numeric conclusion.

## Reference Files

- Read [angle-library.md](./references/angle-library.md) for human-readable angle guidance.
- Read [angle-library.yaml](./references/angle-library.yaml) for runtime field-level routing and gates.
- Read [report-digests.yaml](./references/report-digests.yaml) for offline report digests.
- Read [source-policy.md](./references/source-policy.md) for source hierarchy, global market routing, sector routing, and exclusions.
- Read [proprietary-data.md](./references/proprietary-data.md) whenever valuation or market-data work might depend on terminal-only fields.
