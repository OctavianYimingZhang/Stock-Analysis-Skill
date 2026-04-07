---
name: stock-analysis
description: Fundamental stock analysis for public companies using authoritative sources first and explicit source-quality controls. Use when Codex needs to analyze a stock, ticker, public company, peer set, thesis update, post-earnings change, or industry context for a stock across global markets. Prioritize issuer filings, exchange notices, regulators, government or official industry datasets, and user-provided Bloomberg/FactSet/CapIQ data when needed.
---

# Stock Analysis

## Overview

Analyze a public company from verified evidence, not from memory or recycled writeups. This skill is gate-driven: it must block weak commercial evidence, untagged capacity claims, incomplete capital-structure work, unsupported semantic claims such as `moat` or `network effect`, and terminal-only valuation inputs that the user has not supplied.

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
  - `consumer_health_platform`
  - `b2b_software_platform`
  - `digital_bank_or_lender`
  - `lending_marketplace`
  - `provider_reimbursement`
  - `resource_policy`
  - `industry_chain_context`
- Read [angle-library.yaml](./references/angle-library.yaml) first for runtime routing.
- Read [claim-gates.yaml](./references/claim-gates.yaml) before writing any semantic claim such as `moat`, `platform`, `data flywheel`, or `network effect`.
- Read [report-digests.yaml](./references/report-digests.yaml) for offline report summaries. Do not reread the raw research corpus at runtime.
- Read [angle-library.md](./references/angle-library.md) only as human-readable backup context.

### 2. Build the mandatory gating tables before writing a thesis

Create these tables whenever the thesis depends on commercial claims, milestones, capacity, regulatory gating, reimbursement, qualification, litigation, or accounting quality.

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

#### Regulatory_Qualification_Legal_Gate_Table

Create this table whenever the thesis depends on certification, permits, reimbursement, qualification, litigation, accounting quality, product approval, telehealth or pharmacy distribution rules, or regulatory distribution.

- `gate`
- `gate_type`: `regulator | qualification | legal`
- `authority_or_counterparty`
- `status`: `not_started | submitted | under_review | approved | qualified | contested`
- `economic_dependency`: `low | medium | high`
- `next_observable`
- `source`

Hard rules:

- `under_review`, `qualified_pending`, and `contested` are not realized economic facts.
- If `economic_dependency` is `high` and status is not `approved` or `qualified`, downgrade valuation to scenario framing.
- If active litigation, restatement, material weakness, or revenue-recognition challenge exists, surface it here rather than only in risks.

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

For every material quantitative or semantic claim, capture:

- value or claim text
- date or period
- source
- source class

Separate content into four buckets while you work:

- verified facts
- inference from verified facts
- scenario assumptions
- opinions or judgments

Do not let inference or assumptions drift into fact statements.

### 5. Run semantic claim gates before thesis writing

- When the output uses `data_flywheel`, `network_effect`, `moat`, or `platform`, check [claim-gates.yaml](./references/claim-gates.yaml).
- If the minimum evidence is incomplete, do not state the strong label as fact.
- Downgrade to the configured fallback label or mark the statement as inference.
- Do not use downgraded semantic claims as valuation support by themselves.

### 6. Detect proprietary data and capital-structure gaps early

- Before writing valuation, verify the capital structure from authoritative disclosures.
- Read [proprietary-data.md](./references/proprietary-data.md) whenever valuation, ownership, consensus, peer-multiple, or debt-market work is involved.
- If the user has not supplied terminal-only data required for peer multiples, valuation bands, or consensus, allow scenario framing only.
- If fully diluted share count, dilution stack, debt stack, or net-debt bridge is incomplete, block valuation.

### 7. Write the analysis as base structure plus archetype routing

Start with a `Data Sufficiency` note:

- what was verified
- what was inferred
- what is blocked by missing proprietary data
- what is blocked by weak commercial, capacity, regulatory, qualification, or legal evidence

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

#### `consumer_health_platform`

- product concentration
- retention_cross_sell
- marketing_efficiency
- regulatory_distribution_risk
- fulfillment_margin

#### `b2b_software_platform`

- customer_concentration
- nrr_or_expansion
- sbc_and_true_fcf
- legal_accounting_quality
- data_privacy

#### `digital_bank_or_lender`

- funding_stack
- asset_liability_sensitivity
- credit_quality
- capital_ratios
- regulatory_status

#### `lending_marketplace`

- funding_stack
- partner_funding_quality
- credit_quality
- securitization_dependence
- take_rate_or_fee_model

#### `provider_reimbursement`

- site_or_facility_economics
- reimbursement_mechanics
- collections_quality
- policy_sensitivity
- payer_or_idr_dependency

#### `resource_policy`

- permit_path
- offtake
- realized_pricing
- processing_capacity
- working_capital

#### `industry_chain_context`

- supply_demand_balance
- bottleneck_map
- policy_catalysts
- company_bridge
- no_valuation

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

### 8. Run quality gates before answering

- Reject excluded sources and patterns listed in [source-policy.md](./references/source-policy.md).
- Do not use technical analysis, chart patterns, or Wyckoff phase labels in the fundamental-analysis body (sections 1–7). Technical analysis is confined to the dedicated §9 Technical Structure Assessment appendix.
- Do not use position sizing, stop-loss, stop-gain, or trading plans anywhere in the output.
- Do not output a target price unless the user explicitly asks for one and the valuation section clears all hard gates.
- Block valuation if:
  - fully diluted share count is unverified
  - any part of the dilution stack is unverified
  - the debt stack or net-debt bridge is unverified
  - the denominator depends on `mou`, `pilot`, `framework`, management aspiration, planned capacity, or uncontracted capacity
  - terminal-only consensus or peer data are required and the user has not provided them
  - `economic_dependency` is `high` and the relevant regulatory, qualification, or legal gate is not `approved` or `qualified`
- If valuation is blocked, downgrade to scenario framing and ask for the exact missing fields.
- If evidence is insufficient to verify a claim, leave it out or label it as uncertain.

### 9. Technical Structure Assessment (Appendix)

After the fundamental analysis body is complete, append a **Technical Structure Assessment** section. This section is supplementary context only — it cannot override fundamental conclusions, block or unblock valuation, or serve as a standalone investment thesis.

Skip this section entirely for `industry_chain_context` archetype, pre-IPO targets, or SPACs that have not completed de-SPAC.

Read [technical-analysis-framework.md](./references/technical-analysis-framework.md) for detailed methodology guidance.

#### Scope and Data Requirements

- Use publicly available price and volume data only (daily and weekly timeframes).
- State the observation date and data source (exchange data, Yahoo Finance, etc.).
- Do not fabricate price levels or volume figures. If real-time data is unavailable, state so and skip this section.

#### Three-Layer Analysis Framework

The technical assessment integrates three complementary methodologies. All three layers must be addressed in order.

##### Layer 1: Trend Structure and Key Levels (Murphy)

Identify the current trend regime using Dow Theory and classical trend analysis principles:

| Field | Description |
|-------|-------------|
| `primary_trend` | `uptrend` / `downtrend` / `sideways` — based on sequence of higher highs/higher lows or lower highs/lower lows on weekly chart |
| `secondary_trend` | `uptrend` / `downtrend` / `sideways` — intermediate correction or rally within the primary trend on daily chart |
| `trend_maturity` | `early` / `middle` / `late` — based on Dow Theory three-phase model (accumulation phase → public participation phase → distribution/excess phase) |
| `key_support_levels` | Up to 3 price levels where prior troughs, consolidation bases, or high-volume nodes provide demand |
| `key_resistance_levels` | Up to 3 price levels where prior peaks, consolidation ceilings, or high-volume nodes provide supply |
| `ma_structure` | Relative position of price vs. 50-day and 200-day moving averages; whether 50MA is above or below 200MA (golden cross / death cross) |
| `chart_pattern` | If a classical pattern is identifiable (head & shoulders, double top/bottom, triangle, flag, wedge, cup & handle), name it and state completion status: `forming` / `confirmed` / `failed` |

Hard rules:

- A trend is defined by successive peaks and troughs, not by a single price move.
- Moving average signals are confirming indicators, not primary trend determinants.
- Chart patterns require volume confirmation: breakouts on rising volume are valid; breakouts on declining volume are suspect.
- Support and resistance are zones, not exact prices. State levels as approximate ranges when appropriate.

##### Layer 2: Volume-Price Analysis and Market Phase (Wyckoff)

Assess the supply/demand dynamics and identify the current Wyckoff market phase:

| Field | Description |
|-------|-------------|
| `wyckoff_phase` | `accumulation` / `markup` / `distribution` / `markdown` / `re-accumulation` / `re-distribution` |
| `phase_evidence` | Specific price-volume behaviors that support the phase classification (see checklist below) |
| `effort_vs_result` | Whether volume (effort) is producing proportional price movement (result), or whether divergence exists |
| `composite_man_read` | Inferred smart-money behavior based on volume at key price levels: is institutional activity consistent with accumulation or distribution? |
| `spring_upthrust` | Whether a Spring (false breakdown below support in accumulation) or Upthrust (false breakout above resistance in distribution) has occurred: `none` / `suspected` / `confirmed` |

Wyckoff Phase Identification Checklist:

**Accumulation signs:**

- Preliminary Support (PS): first significant buying after prolonged decline, with volume increase
- Selling Climax (SC): sharp price drop on heavy volume, marking potential bottom
- Automatic Rally (AR): bounce after SC with declining volume
- Secondary Test (ST): price revisits SC area on lighter volume
- Spring: brief dip below trading range support on low volume, followed by strong recovery
- Sign of Strength (SOS): price advances on expanding volume above resistance
- Last Point of Support (LPS): pullback on declining volume before markup phase

**Distribution signs:**

- Preliminary Supply (PSY): first significant selling after prolonged advance, with volume increase
- Buying Climax (BC): sharp price spike on heavy volume, marking potential top
- Automatic Reaction (AR): decline after BC
- Secondary Test (ST): price revisits BC area on lighter volume
- Upthrust (UT): brief move above trading range resistance on low volume, followed by reversal
- Sign of Weakness (SOW): price declines on expanding volume below support
- Last Point of Supply (LPSY): weak rally on declining volume before markdown phase

Hard rules:

- Wyckoff phases are interpretive frameworks, not guaranteed predictors. State confidence level: `high` / `moderate` / `low`.
- Effort vs. Result divergence is meaningful only at key support/resistance levels, not in mid-trend.
- The three Wyckoff laws must be referenced: (1) Supply and Demand determines price direction; (2) Cause and Effect — the trading range duration and width forecast the magnitude of the subsequent move; (3) Effort vs. Result — volume should confirm price movement.

##### Layer 3: Candlestick Pattern Recognition (Nison)

Identify significant candlestick patterns on the daily and weekly charts:

| Field | Description |
|-------|-------------|
| `daily_patterns` | List of significant patterns observed in the last 20 trading days, with date and pattern name |
| `weekly_patterns` | List of significant patterns observed in the last 8 weeks |
| `pattern_context` | Whether the pattern appears at a significant technical level (support, resistance, MA, or trendline) — patterns at random locations are low-signal |
| `confirmation_status` | Whether the pattern has been confirmed by subsequent price action: `pending` / `confirmed` / `failed` |

Pattern Classification (priority order):

**Reversal patterns (high priority when at key levels):**

- Single-candle: Hammer, Inverted Hammer, Hanging Man, Shooting Star, Doji (at extremes)
- Two-candle: Bullish/Bearish Engulfing, Piercing Line, Dark Cloud Cover, Tweezer Top/Bottom
- Three-candle: Morning Star, Evening Star, Three White Soldiers, Three Black Crows, Abandoned Baby

**Continuation patterns:**

- Rising/Falling Three Methods, Tasuki Gap, Side-by-Side White Lines

**Indecision patterns:**

- Doji (at mid-range), Spinning Top, High Wave Candle

Hard rules:

- A candlestick pattern is meaningful only when it appears at a key technical level (support, resistance, trendline, or moving average). Patterns in the middle of a range are noise.
- Reversal patterns require confirmation from the next candle(s). An unconfirmed pattern is labeled `pending`.
- Engulfing patterns and Morning/Evening Stars have higher reliability than single-candle patterns.
- Weekly patterns carry more weight than daily patterns.
- Combine with volume: a hammer on high volume is stronger than one on low volume.

#### Synthesis: Technical Structure Summary

After completing all three layers, produce a brief synthesis:

| Field | Value |
|-------|-------|
| `technical_posture` | `bullish` / `cautiously_bullish` / `neutral` / `cautiously_bearish` / `bearish` |
| `trend_volume_alignment` | `aligned` (trend and volume confirm each other) or `divergent` (volume contradicts trend) |
| `phase_trend_consistency` | Whether Wyckoff phase and Murphy trend classification are consistent |
| `key_inflection` | The single most important price level to watch, with rationale |
| `candlestick_signal` | The strongest candlestick signal observed, if any, with its location context |

#### Technical Structure Disclaimer

Always end this section with:

> This technical structure assessment is supplementary to the fundamental analysis above. It reflects historical price-volume patterns and does not predict future prices. Technical context should be used alongside — never in place of — fundamental, financial, and regulatory due diligence. This is not investment advice and does not constitute a trading recommendation.

## Output Rules

- Be direct and evidence-led.
- Prefer primary and official sources over summaries.
- Cite the source class for every material figure.
- State when a conclusion is an inference rather than a disclosed fact.
- If commercial evidence, capacity status, regulatory status, qualification status, or legal quality is not investment-grade, block valuation rather than forcing a numeric conclusion.
- `industry_chain_context` may provide context and company bridges only. It cannot produce standalone stock valuation.

## Reference Files

- Read [angle-library.yaml](./references/angle-library.yaml) for runtime field-level routing and gates.
- Read [claim-gates.yaml](./references/claim-gates.yaml) for semantic claim controls.
- Read [report-digests.yaml](./references/report-digests.yaml) for offline report digests and locators.
- Read [angle-library.md](./references/angle-library.md) for human-readable angle guidance.
- Read [source-policy.md](./references/source-policy.md) for source hierarchy, global market routing, sector routing, and exclusions.
- Read [proprietary-data.md](./references/proprietary-data.md) whenever valuation or market-data work might depend on terminal-only fields.
- Read [technical-analysis-framework.md](./references/technical-analysis-framework.md) when writing the §9 Technical Structure Assessment appendix.
