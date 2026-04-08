# Proprietary Data Handling — Bloomberg Terminal Request System

Use this file whenever the analysis involves valuation, ownership, analyst consensus, debt markets, peer comparison, or any quantitative claim where online search results are insufficient, stale, conflicting, or unverifiable.

## Core Principle

The agent must self-assess data confidence during research. When online sources are insufficient to meet the skill's evidence standards, the agent must **stop, explain the gap, and request Bloomberg Terminal data from the user** rather than proceeding with weak data.

## Data Confidence Assessment

After searching authoritative online sources (§3), the agent evaluates each material data point:

### Confidence Levels

| Level | Definition | Action |
|-------|-----------|--------|
| `high` | Data found in issuer filings, exchange disclosures, or regulator databases with exact figures and clear dates | Proceed — no terminal data needed |
| `moderate` | Data found in issuer IR materials, earnings calls, or official presentations but lacks full precision or is 1+ quarter old | Proceed with caution — flag staleness, consider requesting terminal update |
| `low` | Data found only in secondary sources, news articles, or aggregator sites; figures conflict across sources; or data is 2+ quarters old | **Request Bloomberg Terminal data** — do not use low-confidence data for valuation or key claims |
| `not_found` | Data not available from any online source; typically terminal-only fields (consensus, peer multiples, ownership snapshots, debt pricing) | **Request Bloomberg Terminal data** — block the dependent section |

### Triggers for Bloomberg Terminal Request

The agent must request terminal data when ANY of these conditions are met:

1. **Conflicting figures**: two or more online sources report materially different numbers for the same metric (e.g., share count differs by > 2%, revenue differs by > 5%)
2. **Stale data**: the most recent available data is 2+ quarters old and the analysis requires current figures
3. **Missing precision**: online sources provide ranges or rounded figures but the analysis requires exact numbers (e.g., fully diluted shares, exact debt balances)
4. **Terminal-only fields**: the data type is inherently proprietary (consensus estimates, peer multiples, ownership snapshots, debt yields, credit spreads)
5. **Unverifiable claims**: a material claim cannot be cross-referenced against any authoritative source
6. **Incomplete capital structure**: any component of the dilution stack or debt stack cannot be verified from public filings

## Capital-Structure Verification Gates

Block the valuation section if any of these are unverified from authoritative disclosures:

- fully diluted share count
- dilution stack (options, RSUs/PSUs, warrants, convertibles, preferreds, earnouts, contingent shares)
- debt stack (drawn debt, convertibles, preferred/hybrid, lease liabilities when EV is used, restricted cash offsets)
- net-debt bridge
- near-term maturities relevant to refinancing risk

If the valuation denominator depends on an unverified capital-structure input, block valuation.

## Commercial and Capacity Denominator Gates

Block target-price style valuation when the denominator depends on:

- `mou`, `pilot`, `framework`, management aspiration
- planned capacity, uncontracted capacity

In those cases, allow scenario framing only.

## Bloomberg Terminal Data Categories

### Category 1: Consensus and Forecasts

**When to request**: valuation requires forward estimates; online consensus data is stale, conflicting, or unavailable.

Fields to request:
- Forward revenue consensus (current FY, next FY)
- Forward EPS consensus (current FY, next FY)
- Forward EBITDA consensus (if relevant to valuation method)
- Number of analysts covering
- Consensus revision trend (up/down over 30/90 days)
- Segment-level forecasts (if available and relevant)

### Category 2: Peer Valuation and Multiples

**When to request**: peer comparison needed; online multiple data is inconsistent or methodology unknown.

Fields to request:
- Peer company names and tickers
- Market cap or enterprise value
- Forward and trailing multiples (P/E, EV/EBITDA, EV/Revenue, P/B)
- Methodology and period used
- As-of date

### Category 3: Ownership and Positioning

**When to request**: ownership claim is material to thesis; online ownership data is 1+ quarter old or conflicting.

Fields to request:
- Top institutional holders with share counts and % ownership
- Holder changes (QoQ)
- Short interest (shares short, days to cover, % of float)
- Insider ownership summary

### Category 4: Debt and Capital Markets

**When to request**: debt analysis needed; bond pricing, yields, or spreads are not available from public filings.

Fields to request:
- Bond/note pricing and yields by maturity
- Credit spreads vs. benchmark
- Credit rating and outlook
- Debt maturity schedule (if not fully disclosed in filings)
- Covenant details (if not in public filings)

### Category 5: Capital Structure Detail

**When to request**: online search cannot verify the full dilution or debt stack.

Fields to request:
- Fully diluted share count (with breakdown)
- Options outstanding with weighted average strike
- RSU/PSU shares outstanding
- Warrants and convertible details (shares, conversion price, maturity)
- Preferred shares and conversion terms
- Total debt balance with instrument-level detail

### Category 6: Commodity and Industry Series

**When to request**: the analysis depends on a price series, industry benchmark, or market share dataset that is paywalled or terminal-only.

Fields to request:
- Specific commodity price series with dates
- Industry market share or benchmark tables
- Paywalled industry time series

## Request Protocol

### Step 1: Explain Why

Before requesting data, the agent must explain:
- What it searched for and where
- Why online results are insufficient (conflicting, stale, missing, imprecise)
- Which section of the analysis is blocked or degraded
- What specific Bloomberg function or screen would provide the data (when known)

### Step 2: Request with Precision

Use this format for every Bloomberg Terminal data request:

```
Bloomberg Terminal 数据请求

需要的数据：[exact fields]
公司/标的：[ticker / company name]
截止日期：[as-of date, e.g., "最新可用" or specific date]
货币/单位：[currency and unit]
Bloomberg 功能参考：[e.g., BEst for consensus, RELS for peers, OWN for ownership]

原因：[1-2 sentences explaining why online data is insufficient]
影响：[which section is blocked — e.g., "估值部分被阻断" or "同行比较不可用"]

请以以下格式提供：
1. 纯文本表格（首选）
2. CSV
3. 截图
```

### Step 3: Continue Non-Blocked Sections

While waiting for terminal data:
- Complete all sections that can be done from public sources
- Mark blocked sections with `[待Bloomberg数据]` placeholder
- In the Data Sufficiency note, list exactly which fields are pending

## Request Templates

### Consensus Request

```
Bloomberg Terminal 数据请求

需要的数据：Forward Revenue, EPS, EBITDA consensus (FY1, FY2), analyst count, 30/90-day revision trend
公司/标的：[TICKER]
截止日期：最新可用
Bloomberg 功能参考：BEst (Bloomberg Estimates)

原因：在线搜索发现的一致预期数据来源不一致/已过时（[具体说明]），无法满足估值分析的精度要求。
影响：估值部分被阻断，仅可提供情景框架。
```

### Peer Valuation Request

```
Bloomberg Terminal 数据请求

需要的数据：Peer comp table — company, ticker, market cap, EV, FY1 P/E, EV/EBITDA, EV/Revenue, P/B
公司/标的：[TICKER] 及其可比公司
截止日期：最新可用
Bloomberg 功能参考：RELS (Related Securities), RV (Relative Value)

原因：在线可比公司估值倍数来源方法论不明确，无法确保口径一致。
影响：同行估值比较部分不可用。
```

### Ownership Request

```
Bloomberg Terminal 数据请求

需要的数据：Top 20 institutional holders (name, shares, % ownership, QoQ change), short interest (shares, days to cover, % float)
公司/标的：[TICKER]
截止日期：最新可用
Bloomberg 功能参考：OWN (Ownership), SI (Short Interest)

原因：在线持仓数据已过时（最新为[date]），且不同来源数据存在冲突。
影响：持仓分析和机构动向部分的可信度不足。
```

### Capital Structure Request

```
Bloomberg Terminal 数据请求

需要的数据：Fully diluted share count, dilution stack (options w/ avg strike, RSUs, warrants, convertibles, preferreds), total debt by instrument, maturity schedule
公司/标的：[TICKER]
截止日期：最新可用
Bloomberg 功能参考：DES (Description), DDIS (Debt Distribution), CACS (Capital Structure)

原因：公开披露文件中[具体说明缺失项]无法验证，在线来源与年报数据存在差异。
影响：资本结构未验证，估值部分被阻断。
```

### Debt Market Request

```
Bloomberg Terminal 数据请求

需要的数据：Bond/note prices, yields, spreads by maturity; credit rating and outlook
公司/标的：[TICKER]
截止日期：最新可用
Bloomberg 功能参考：SRCH (Bond Search), RATD (Ratings)

原因：债券市场定价数据为终端专有数据，无法从公开来源获取。
影响：债务分析和再融资风险评估受限。
```

## Output Behavior When Blocked

- Say exactly which section is blocked and why
- Complete all sections that can be done from authoritative public sources
- Mark blocked sections clearly with `[待Bloomberg数据]`
- Do not invent proxies or use stale/conflicting data as substitutes
- Do not output a target price when consensus, peer multiples, dilution stack, or debt stack remain incomplete
- When Bloomberg data arrives, integrate it and complete the blocked sections
