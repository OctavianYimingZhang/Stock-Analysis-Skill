# Source Policy

Use this file on every stock-analysis task. It defines the required source hierarchy, evidence standards, and source exclusions.

## Core Rule

Search authoritative online sources first. Do not rely on memory, recycled research reports, or secondary summaries when primary or official sources are available.

## Source Hierarchy

### Tier 1: Issuer and Exchange Sources

Use these first whenever available:

- Issuer filings: `10-K`, `10-Q`, `20-F`, `6-K`, `8-K`, annual reports, interim reports, proxy statements, offering documents
- Issuer IR materials: investor presentations, shareholder letters, earnings releases, official earnings-call transcripts, event transcripts, prepared remarks
- Exchange or filing-system sources:
  - `SEC/EDGAR`
  - `SEDAR+`
  - `HKEXnews`
  - `SSE`
  - `SZSE`
  - the relevant exchange or official filing portal for the issuer's market

### Tier 2: Regulators, Governments, and Official Counterparties

Use these when the thesis depends on regulation, approvals, contracts, subsidies, or official statistics:

- General regulators and agencies: competition authorities, banking regulators, healthcare regulators, energy regulators, communications regulators, defense agencies, procurement portals
- Common sector examples from the corpus:
  - `FAA`
  - `FCC`
  - `NRC`
  - `DOE`
  - `CMS`
  - `HHS`
  - `DoD`
  - `USGS`
  - `IAEA`
  - `WNA`
- Official partner or customer disclosures are acceptable when the relationship, contract, or award is material and directly attributable.

### Tier 3: Official Industry and Public Datasets

Use these when the primary published dataset for an industry is maintained by an official or recognized body:

- Government statistical series
- Recognized industry bodies with attributable methodology
- Official market operators or exchange-published data

Use these carefully:

- Treat them as industry context or benchmark inputs.
- Do not let them override issuer disclosures for company-specific facts.

### Tier 4: Secondary Sources

Use only for non-critical context when no primary or official source exists, and label them as secondary.

Do not use secondary sources for:

- core financial figures
- segment data
- capital structure
- regulatory status
- contract terms
- market-share claims
- valuation inputs

## Market-Specific Guidance

- For US issuers, start with `SEC/EDGAR`, the issuer IR site, and sector regulators.
- For Canadian issuers, start with `SEDAR+`, issuer IR, and relevant provincial or federal regulators.
- For Hong Kong issuers, start with `HKEXnews`, issuer IR, and market-specific regulators.
- For mainland China issuers, start with `SSE` or `SZSE`, issuer disclosures, and sector regulators.
- For other markets, use the local exchange or filing portal before searching broader web sources.

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
