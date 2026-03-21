# Proprietary Data Handling

Use this file whenever the analysis reaches valuation, ownership, analyst-consensus, or certain market-data questions.

## Hard Rule

If a needed field is not available from an authoritative public source and normally comes from Bloomberg, FactSet, Capital IQ, LSEG, Visible Alpha, or a similar professional dataset, stop and ask the user for that field. Do not replace it with a weaker source.

## Fields That Commonly Require User-Provided Proprietary Data

### Consensus and Forecasts

Ask the user for these when needed:

- forward revenue consensus
- forward EPS consensus
- forward EBITDA or EBIT consensus
- segment-level forecasts
- analyst estimate revisions

### Historical Valuation and Peer Tables

Ask the user for these when needed:

- historical valuation bands
- peer-screen tables with unified methodology
- forward and trailing peer multiples
- analyst target-price distribution
- standardized comp sets from terminal screens

### Ownership and Market Positioning

Ask the user for these when needed:

- ownership snapshots
- holder changes
- fund flows or positioning tables
- short-interest datasets if the requested analysis depends on a terminal-quality source

### Debt and Capital-Markets Detail

Ask the user for these when needed:

- debt pricing
- debt yields
- spread tables
- bond trading levels
- capital-structure screens that are not reconstructible from filings alone

### Commodity and Industry Series

Ask the user for these when needed:

- commodity price series that are not published by an official public source
- paywalled industry time series
- terminal-only industry share or benchmark tables

## What You Should Do Before Asking

- Confirm that the field is actually needed for the requested output.
- Confirm that the field cannot be obtained from:
  - issuer filings or IR materials
  - exchange filings
  - regulators
  - governments
  - official public datasets
- Narrow the request to the minimum blocking fields.

## Request Format

Ask for:

- exact fields needed
- as-of date
- currency and unit
- methodology if relevant
- peer list if the request concerns comps

Preferred user input order:

1. plain-text table
2. CSV
3. screenshot

## Request Templates

### Consensus Block

Use this pattern:

`I can complete the operating and risk sections from public sources, but the valuation section is blocked by missing terminal-style consensus data. Please provide forward revenue, EPS, and EBITDA consensus for [company/ticker] as of [date], ideally as a plain-text table or CSV.`

### Peer Valuation Block

Use this pattern:

`To keep the peer valuation section authoritative, please provide the comp table you want me to use, including company names, tickers, market caps or EV, and the exact multiples or forecast periods as of [date]. Plain-text table is preferred.`

### Ownership or Flows Block

Use this pattern:

`The ownership or positioning claim cannot be verified from authoritative public sources alone. Please provide the terminal-derived ownership or flows snapshot as of [date], preferably as a plain-text table or CSV.`

### Debt-Market Block

Use this pattern:

`The capital-markets section needs debt pricing or yield data that is typically terminal-only. Please provide the bond or debt table as of [date], including instrument name, maturity, coupon, and price or yield.`

## Output Behavior When Blocked

- Say exactly which section is blocked.
- Continue with the sections that can be completed from authoritative public sources.
- Do not invent proxies.
- Do not present stale or low-quality substitutes as equivalent to terminal data.
