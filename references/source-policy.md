# Source Policy

Use this file on every stock-analysis task. It defines the required source hierarchy, global market routers, sector routers, evidence standards, and source exclusions.

## Core Rule

Search authoritative online sources first. Do not rely on memory, recycled research reports, or secondary summaries when primary or official sources are available.

## Source Hierarchy

### Tier 1: Issuer and Exchange Sources

Use these first whenever available:

- issuer filings: `10-K`, `10-Q`, `20-F`, `6-K`, `8-K`, annual reports, interim reports, proxy statements, offering documents
- issuer IR materials: investor presentations, shareholder letters, earnings releases, official earnings-call transcripts, event transcripts, prepared remarks
- exchange or filing-system sources:
  - `SEC/EDGAR`
  - `SEDAR+`
  - `HKEXnews`
  - `SSE`
  - `SZSE`
  - the relevant exchange or official filing portal for the issuer's market

### Tier 2: Regulators, Governments, and Official Counterparties

Use these when the thesis depends on regulation, approvals, contracts, subsidies, permits, procurement, reimbursement, or official statistics:

- general regulators and agencies: competition authorities, banking regulators, healthcare regulators, energy regulators, communications regulators, defense agencies, procurement portals
- official partner or customer disclosures are acceptable when the relationship, contract, or award is material and directly attributable

### Tier 3: Official Industry and Public Datasets

Use these when the primary published dataset for an industry is maintained by an official or recognized body:

- government statistical series
- recognized industry bodies with attributable methodology
- official market operators or exchange-published data

Use them as context and benchmark inputs, not as overrides for issuer-specific facts.

### Tier 4: Secondary Sources

Use secondary sources only for non-critical context when no primary or official source exists, and label them as secondary.

Do not use secondary sources for:

- core financial figures
- segment data
- capital structure
- regulatory status
- contract terms
- market-share claims
- valuation inputs

## Global Market Routers

- US: `SEC/EDGAR`, issuer IR, applicable sector regulators
- Canada: `SEDAR+`, issuer IR, applicable federal or provincial regulators
- UK: `LSE` / `RNS`, issuer IR, `FCA` or sector regulators when relevant
- Australia: `ASX`, issuer IR, sector regulators
- Japan: `JPX` / `TDnet`, issuer IR, sector regulators
- Korea: `DART`, issuer IR, sector regulators
- Hong Kong: `HKEXnews`, issuer IR, sector regulators
- Mainland China: `SSE` or `SZSE`, issuer disclosures, sector regulators
- Euronext markets: `Euronext`, issuer IR, applicable national regulators
- France: `AMF`, issuer IR, sector regulators
- Germany: `BaFin`, issuer IR, sector regulators
- India: `NSE` / `BSE`, issuer IR, sector regulators
- Israel: `TASE`, issuer IR, sector regulators
- South Africa: `JSE`, issuer IR, sector regulators
- Other markets: use the applicable exchange, filing system, and sector regulator before broader web search

## Sector Routers

### Energy and Power

Prefer, in order:

- issuer filings and project disclosures
- `EIA`
- `FERC`
- ISO/RTO sources
- state utility or public utility commission sources
- official counterparties such as utilities or grid operators

### Government Contracts and Procurement

Prefer, in order:

- issuer filings
- `SAM.gov`
- `USASpending`
- agency procurement, award, or contract notices
- official counterparty disclosures

### Healthcare Reimbursement and Policy

Prefer, in order:

- issuer filings
- `CMS`
- `HHS`
- `No Surprises Act`
- `IDR`
- state insurance or reimbursement regulators

### Mining and Resources

Prefer, in order:

- issuer filings
- `NI 43-101`
- `S-K 1300`
- `USGS`
- mine, environmental, or permit regulators
- official project or offtake counterparties

### Aerospace and Satellite

Prefer, in order:

- issuer filings
- `FAA`
- `FCC`
- `ITU`
- official launch, spectrum, or government counterparties

## Hard Rule for Sector Claims

When a sector-specific official source exists, issuer IR alone is not sufficient for regulatory, reimbursement, procurement, permit, or certification claims.

## Evidence Standards by Claim Type

### Company Profile and Business Mix

Prefer:

- annual report
- segment footnotes
- investor presentation
- official product and business descriptions

### Financial Statements and Capital Structure

Prefer:

- audited annual reports
- quarterly or interim filings
- debt footnotes
- cash-flow statements
- maturity schedules
- official financing announcements

### Operating Metrics

Prefer:

- issuer KPI tables
- earnings releases
- official call transcripts
- regulator data when the KPI is regulatory in nature

Examples:

- backlog, bookings, utilization, subscribers, shipped units, installed base, visit volume, capacity, production, project pipeline, satellite launches, approvals

### Commercial Relationships

Prefer:

- bilateral disclosures
- issuer filings that define economic terms
- regulator or procurement evidence when relevant

Do not assume `partnership`, `pilot`, or `framework` means economic visibility equivalent to orders, backlog, or revenue.

### Policy, Regulation, and Certification

Prefer:

- regulator or agency publications
- official approval databases
- company filings that explicitly cite the regulatory event

### Industry Context

Prefer:

- official industry body datasets
- government datasets
- exchange or market-operator publications

Do not state company-specific conclusions from industry context alone.

### Valuation and Market Data

Prefer public authoritative inputs when available:

- company share count and dilution disclosures
- official debt balances
- company guidance
- clearly attributable commodity or benchmark series

When the task needs consensus, historical multiple bands, peer-screen tables, target distributions, ownership snapshots, or debt trading data, check [proprietary-data.md](./proprietary-data.md).

## Claim Taxonomy

Separate content into these categories:

- `Fact`: directly supported by a cited authoritative source
- `Inference`: reasoned interpretation of facts
- `Scenario assumption`: explicit modeling input, not a disclosed fact
- `Opinion`: judgment or view

Do not present inference, scenarios, or opinions as facts.

## Excluded Sources and Patterns

Do not rely on:

- Discord
- YouTube or KOL videos
- member-only trading diaries
- content farms
- Q&A platforms
- forum posts
- social-media threads
- unsourced screenshots
- unsourced charts
- copied numbers without attribution

Do not use these patterns as evidence:

- technical analysis
- chart patterns
- stop-loss or take-profit plans
- position sizing
- "institutions are buying"
- "the stock should double"
- uncited TAM claims
- uncited management quotes
- uncited peer multiples

## Corpus-Specific Lessons

The provided corpus contained useful angle selection but also repeated weak habits:

- technical-analysis sections mixed into fundamental reports
- position recommendations and stop-loss language
- self-media distribution and community links
- strong valuation conclusions with incomplete sourcing

Do not inherit those habits. Reuse only the angle, not the unsupported evidence style.
