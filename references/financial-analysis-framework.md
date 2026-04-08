# Financial Analysis Framework Reference

This file provides detailed methodology guidance for the financial quality section in SKILL.md §7. It draws on variance decomposition, financial statement quality, and cash flow analysis methodologies.

## Section 1: Revenue Quality Decomposition

### Revenue Type Taxonomy

| Type | Definition | Examples |
|------|-----------|----------|
| `value_creating` | Revenue from proprietary products, IP, or services where the company controls pricing and captures margin | SaaS subscription, licensed IP, fee-based advisory, proprietary product sales |
| `pass_through` | Revenue from procurement on behalf of clients or resale at cost-plus-minimal-markup where the company bears little pricing power | EPC materials procurement, hardware resale at near-cost, sub-contractor pass-through, cost-reimbursable contract revenue |
| `agency` | Revenue where the company acts as agent per ASC 606 — recognized net, not gross | Marketplace transaction fees (when reported gross), ticketing commissions, referral fees |
| `mixed` | Bundled contracts with both value-creating and pass-through components | Managed services with hardware attach, turnkey projects with third-party equipment |

### Pass-Through Identification from Filings

Check in order:

1. **MD&A — cost of revenue composition**: look for language like "materials purchased on behalf of," "sub-contracted services," "equipment procured for"
2. **Segment footnotes**: compare gross margin across segments — a segment with structurally low margin (< 5%) often contains pass-through
3. **ASC 606 disclosures**: check principal vs. agent determination — if the company presents gross but acknowledges agent characteristics, the true economic margin is different
4. **Earnings call transcripts**: search for "hardware attach," "procurement," "pass-through," "cost-plus," "EPC materials"
5. **Gross margin stability**: if a segment shows stable but very low margin (1-3%) over multiple periods, it likely reflects contractual pass-through with a fixed markup

### Core Margin Calculation

1. Identify pass-through revenue from filings (per the checklist above)
2. Subtract pass-through revenue from total revenue to get **core revenue**
3. Subtract pass-through COGS (roughly equal to pass-through revenue) from total COGS to get **core COGS**
4. **Core gross margin** = (core revenue - core COGS) / core revenue
5. Sensitivity test: recalculate with pass-through share estimate +/- 5 percentage points

When the exact pass-through amount is not disclosed, use segment-level data as a proxy: if one segment has gross margin < 5% and another > 30%, the low-margin segment likely contains pass-through.

### Archetype-Specific Revenue Quality Patterns

| Business Model | Typical Pass-Through Risk | What to Check |
|---------------|--------------------------|---------------|
| EPC / engineering services | High — materials procurement, sub-contracting | Cost-of-revenue breakdown, project-type footnotes |
| Marketplace / platform | Medium — principal vs. agent (gross vs. net) | ASC 606 agent determination, take-rate trends |
| Hardware + software bundlers | Medium — hardware may be near-zero margin | Segment margins, attached vs. standalone pricing |
| Contract manufacturing | Varies — toll processing (low pass-through) vs. buy-sell (high) | Input cost structure, customer-furnished materials |
| Distribution / logistics | High — gross vs. net presentation | Revenue recognition policy, commission vs. resale |
| Managed services / outsourcing | Medium — labor sub-contracting, equipment procurement | Headcount model (employees vs. contractors), cost structure |

## Section 2: Earnings Quality Assessment

### GAAP vs. Non-GAAP Bridge

Build the bridge from filings:

1. Start with **GAAP operating income** (or net income)
2. List each adjustment item with sign (+/-) and dollar magnitude
3. Common adjustment items:
   - Stock-based compensation (SBC)
   - Amortization of acquired intangibles
   - Restructuring and reorganization charges
   - Acquisition and integration costs
   - Litigation settlements or reserves
   - Impairment charges
   - Foreign exchange gains/losses
   - Gain/loss on debt extinguishment
4. Calculate: **adjusted income as % of GAAP income**
   - If ratio exceeds 2x (adjusted is more than double GAAP), flag earnings quality concern
   - If the same "non-recurring" items recur every period, they are recurring — flag the pattern

### Revenue Recognition Quality Checks

Based on ASC 606 five-step framework:

1. **Performance obligations**: are they clearly identified in filings?
2. **Bill-and-hold indicators**: rising DSO, receivables concentration, revenue spikes at quarter-end
3. **Revenue timing**: point-in-time vs. over-time recognition — over-time uses estimates that management can influence
4. **Deferred revenue trends**: growing = positive sign (backlog building); declining may mean less forward visibility
5. **Contract assets vs. contract liabilities**: growing contract assets (unbilled revenue) relative to contract liabilities (deferred revenue) may signal aggressive recognition

### SBC Impact Analysis

| Metric | Calculation | Threshold |
|--------|------------|-----------|
| SBC as % of revenue | SBC expense / total revenue | > 15% warrants disclosure |
| SBC as % of operating income | SBC / GAAP operating income | > 10% triggers mandatory bridge |
| Dilution rate | Annual share grants / diluted share count | > 3% annually is significant |
| True FCF | GAAP FCF minus SBC expense | Always calculate when SBC is material |

### Accrual Ratio

**Accrual ratio** = (net income - operating cash flow) / average total assets

- Rising accrual ratio over consecutive periods = deteriorating earnings quality
- High positive accrual ratio = earnings are driven by accruals, not cash
- Negative accrual ratio = cash generation exceeds reported earnings (generally healthy)

## Section 3: Cash Flow Decomposition

### Operating Cash Flow Quality

Start with net income, then analyze the bridge to OCF:

- **Non-cash add-backs**: depreciation, amortization, SBC, impairment, deferred taxes
- **Working capital changes**: the swing factor — can inflate or deflate OCF relative to earnings
- **Quality signal**: when OCF consistently exceeds net income, cash quality is high; when OCF trails net income, investigate the accrual composition

### Capex Classification

| Method | When to Use | Calculation |
|--------|-------------|-------------|
| Management disclosure | When company reports maintenance vs. growth split | Use as disclosed |
| Depreciation proxy | When split not disclosed | Maintenance capex ~ depreciation; growth capex = total capex - depreciation |
| Industry benchmark | When depreciation proxy seems unreasonable | Use sector average maintenance-capex-to-revenue ratio |

Always state which method was used.

### Free Cash Flow Variants

| Variant | Formula | Use Case |
|---------|---------|----------|
| FCF | OCF - total capex | General purpose |
| Maintenance FCF | OCF - maintenance capex | Measures cash available after sustaining the business |
| Levered FCF | FCF - mandatory debt service | Cash available to equity after debt obligations |
| Unlevered FCF | NOPAT + D&A - capex - change in working capital | For WACC-based valuation (pre-debt cash flow) |

State which definition is used in every instance.

### Working Capital Decomposition

When working capital change is a material driver of OCF:

| Metric | Formula | What It Reveals |
|--------|---------|----------------|
| DSO (days sales outstanding) | Receivables / (revenue / 365) | Collection efficiency; rising DSO = potential revenue quality issue |
| DIO (days inventory outstanding) | Inventory / (COGS / 365) | Inventory management; rising DIO = potential demand issue |
| DPO (days payable outstanding) | Payables / (COGS / 365) | Supplier terms; rising DPO = stretching payments |
| Cash conversion cycle | DSO + DIO - DPO | Overall working capital efficiency |

Trend the metrics over 4+ quarters. A single quarter can be noisy; the trend reveals structural changes.

## Section 4: Return Metrics Framework

### ROIC Calculation

1. **NOPAT** = operating income × (1 - effective tax rate)
2. **Invested capital** = total equity + total debt - excess cash
3. **ROIC** = NOPAT / average invested capital
4. **Tangible ROIC** = NOPAT / (invested capital - goodwill - acquired intangibles)
   - Calculate when goodwill > 30% of total assets

Compare ROIC to estimated cost of capital:
- ROIC > WACC = value creation
- ROIC < WACC = value destruction

### ROE DuPont Decomposition

**ROE = net profit margin x asset turnover x equity multiplier**

| Component | Formula | What It Reveals |
|-----------|---------|----------------|
| Net profit margin | Net income / revenue | Profitability |
| Asset turnover | Revenue / average total assets | Capital efficiency |
| Equity multiplier | Average total assets / average equity | Financial leverage |

Identify which component is driving ROE changes over time. High-leverage-driven ROE is lower quality than high-margin-driven ROE.

## Section 5: Variance Analysis Methodology

### Price / Volume / Mix Decomposition

When comparing revenue across periods:

- **Volume effect** = (current volume - prior volume) x prior price
- **Price effect** = (current price - prior price) x current volume
- **Mix effect** = residual, or calculated from segment-level data when available

### Rate / Mix Decomposition for Blended Metrics

For metrics like NIM, take-rate, ASP, blended yield:

- **Rate effect** = change in rate x prior-period base
- **Mix effect** = change in mix x base-period rate differential
- **Interaction** = residual

### Materiality Thresholds

| Comparison Type | Threshold for Mandatory Decomposition |
|----------------|--------------------------------------|
| Actual vs. prior period | 15% variance |
| Actual vs. budget/guidance | 10% variance |
| Actual vs. forecast | 5% variance |
| Sequential (QoQ) | 20% variance |

Below threshold: note the variance but do not require full decomposition.

### Waterfall Presentation Format

Present variance drivers as:

1. Starting value (prior period / budget / guidance)
2. Each driver as a signed delta with source citation
3. Ending value (current period / actual)

Every driver must be sourced from filings, earnings releases, or official transcripts. Do not attribute variance to a driver based on inference alone.

## Section 6: Leverage and Solvency Framework

### Debt Metrics

| Metric | Formula | Warning Level |
|--------|---------|---------------|
| Net debt / EBITDA | (Total debt - cash) / LTM EBITDA | > 3x for most industries; > 5x high risk |
| Gross debt / EBITDA | Total debt / LTM EBITDA | Context-dependent |
| Interest coverage | EBIT / interest expense | < 2x is danger zone |
| Fixed charge coverage | (EBIT + lease payments) / (interest + lease payments) | < 1.5x is tight |

### Maturity Profile

Assess from debt footnotes:

- **Near-term** (next 12 months): immediate refinancing need
- **Medium-term** (1-3 years): upcoming wall
- **Weighted average maturity**: overall profile health
- **Refinancing risk**: assess against current credit spreads and market conditions

### Covenant Analysis

When financial maintenance covenants are disclosed:

1. Identify the covenant metric (e.g., net debt/EBITDA < 4.0x)
2. Calculate current headroom (current metric vs. covenant limit)
3. Stress test: how much would EBITDA need to decline before breach?
4. Check for step-downs (covenants that tighten over time)

## Integration with Gate Architecture

The financial analysis framework feeds into the existing gate system:

- Revenue quality decomposition may cause re-evaluation of commercial evidence table values
- Cash flow decomposition provides data for capital-structure verification gates
- Leverage metrics feed into turnaround archetype maturity-wall assessment
- Working capital analysis supports resource_policy archetype working-capital section
- Earnings quality flags (material weakness, restatement risk) feed into the regulatory/qualification/legal gate table
- Pass-through revenue findings must be reflected in the Data Sufficiency note when material
