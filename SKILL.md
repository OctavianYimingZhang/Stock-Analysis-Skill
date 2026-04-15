---
name: stock-analysis
description: >
  Fundamental stock analysis for public companies. Produces themed content blocks
  (business logic, operating logic, customers & orders, financial data, catalysts)
  that can be used standalone OR fed to the stock-research-report orchestrator.
  Uses authoritative sources (filings, exchange notices, regulators) and optional
  Bloomberg Terminal data. Emphasizes bottom-up unit economics, operating leverage
  decomposition, and named customers/contracts over generic end-market narratives.
triggers:
  - fundamental analysis
  - stock analysis
  - analyze stock
  - 基本面分析
  - company analysis
  - equity analysis
---

# Stock Analysis — Fundamental

## Overview

Analyze a public company from verified evidence. Produce **themed content blocks** that either (a) feed the `stock-research-report` orchestrator or (b) stand alone as a fundamental analysis. Emphasize:

- **Business logic transformation** (why this company is interesting RIGHT NOW)
- **Bottom-up operating logic** (capacity × utilization × unit economics)
- **Named customers and contract walks** (not generic end-market percentages)
- **Operating leverage decomposition** (incremental margin walk)
- **Dated management quotes** (speaker + date always preserved)

This skill is **gate-driven**: block weak commercial evidence, untagged capacity claims, incomplete capital-structure work, unsupported semantic claims (`moat`, `network effect`), and terminal-only valuation inputs the user has not supplied.

## Output Format

This skill has **two output modes**:

- **Content Block Mode** (default when called by `stock-research-report`): Output themed content blocks with ALL material facts preserved. The orchestrator will weave them into a final narrative. Do NOT self-format as a complete report with headers.
- **Standalone Mode** (when called directly): Produce a themed analyst-style output that follows the report format in `references/report-format.md` and ends with a trade plan.

In both modes: strip Claude-voice vocabulary (see Style section). Preserve all named customers, dated quotes, contract numbers, and catalyst dates. Do not pre-compress.

---

## Mandatory Workflow

### 1. Scope the Request

- Identify company, ticker, exchange, and analysis scope.
- Resolve ticker/exchange ambiguity from authoritative sources before starting. Ask a short clarifying question only if unresolvable.
- Classify the company into ONE archetype:
  - `mature` — stable operations, focus on margin and capital allocation
  - `frontier` — pre-revenue or early commercialization
  - `turnaround` — balance sheet repair, operational restructuring
  - `b2b_software_platform` — SaaS, ARR/NRR-driven
  - `digital_bank_or_lender` — funding stack, credit quality
  - `lending_marketplace` — capital partners, take rate
  - `provider_reimbursement` — site economics, payer policy
  - `resource_policy` — permit path, offtake, processing capacity
  - `industry_chain_context` — thematic context, no standalone valuation
  - `consumer_health_platform` — product mix, retention, regulatory
- Read `references/angle-library.yaml` for runtime routing and `references/claim-gates.yaml` before writing semantic claims.

### 2. Build Evidence Gating Tables (Silent — Used Internally)

Build these internally, surface only when they materially affect the thesis. Do NOT output them as tables in the final report.

**Commercial Evidence** — for each material commercial claim, internally record:
- `claim`, `source_side` (issuer_only / bilateral / regulator), `contract_form` (mou / pilot / framework / commercial_agreement / binding_po / backlog / recognized_revenue), `disclosed_value`, `valuation_usability`

Hard rules:
- `mou`, `pilot`, `framework`, management aspiration are NOT valuation denominators
- Only `binding_po`, `backlog`, `recognized_revenue` are strong economic visibility

**Capacity and Milestone** — for each capacity claim, internally record:
- `metric`, `status` (planned / ordered / under_construction / mechanically_complete / ramping / operational), `monetization_status` (uncontracted / partially_contracted / contracted), `date`

Hard rule: `planned`, `ordered`, `under_construction`, `uncontracted` capacity is NOT a valuation denominator. Distinguish physical completion from commercial monetization.

**Regulatory/Qualification/Legal** — for any thesis-gating regulatory item, internally record:
- `gate`, `gate_type`, `authority`, `status`, `economic_dependency`, `next_observable`, `source`

Hard rule: `under_review`, `qualified_pending`, `contested` are NOT realized economic facts.

### 3. Search Authoritative Sources

Start with:
- Issuer filings and investor relations
- Exchange notices and filing systems (SEC EDGAR, HKEX, SSE, SZSE, TSE, LSE)
- Regulators and government databases
- Official partner/customer/counterparty disclosures when directly relevant
- sec-parser library for 10-K semantic extraction (optional — yields risk-factor diffing)

**Data confidence assessment:**

| Confidence | Definition | Action |
|-----------|-----------|--------|
| `high` | Exact figures from filings, exchange, or regulator with clear dates | Proceed |
| `moderate` | From IR materials or earnings calls; lacks precision or is 1+ quarter old | Proceed with staleness note inline |
| `low` | Secondary sources only; figures conflict; or 2+ quarters old | Request Bloomberg Terminal data |
| `not_found` | Terminal-only field (consensus, peer multiples, ownership, debt pricing) | Request Bloomberg Terminal data |

When requesting Bloomberg data, use `references/bloomberg-request-templates.md`. Continue writing all non-blocked sections while waiting; mark blocked sections inline with a brief note ("因数据限制，此处仅做框架性估算").

**Do NOT start the final report with a "数据充分性说明" section.** Confidence notes are embedded inline where relevant, not at the top.

### 4. Build an Evidence Ledger

For every material quantitative or semantic claim, capture:
- Value or claim text
- Date or period
- Source
- Source class

Keep four buckets while working (not as output):
- Verified facts
- Inference from verified facts
- Scenario assumptions
- Opinions or judgments

Do not let inference or assumptions drift into fact statements.

### 5. Produce Themed Content Blocks

The output is organized as THEMED BLOCKS, not numbered parts. In Content Block Mode, emit each block with a clear label so the orchestrator can weave. In Standalone Mode, these become the sections of the report.

#### Block A: 业务逻辑 (Business Logic Transformation)

**Length**: 2-4 paragraphs
**Purpose**: Tell the transformation story — why is this company interesting RIGHT NOW?

**Must answer four questions in narrative form (not as a bullet list):**
1. What was the OLD value driver 2-3 years ago? (with specific data)
2. What is the NEW value driver now or near future? (with specific data)
3. What structural change is forcing/enabling the transformation?
4. If successful, what does the company look like in 3-5 years?

**Hard rules:**
- Never output as four bullet points — write cohesive prose
- Support each claim with specific data (e.g., "计算类收入从 2023 年 10% 提升至 2025 年 80%")
- Include management quotes with dates (e.g., "Greg Smith 在 2026 年 1 月 Q4 电话会中指出...")
- Weave in industry chain context naturally
- If no transformation is happening (stable mature), state "公司处于稳定运营模式" and describe the steady-state logic plus what's changing at the margin

**Template:**
```
[OLD LOGIC paragraph — 1 paragraph]
在 2023 年之前，[Company] 主要靠 [old value driver]。[Supporting data with source and date]. 这个模式的核心特征是 [characteristic] — 高度依赖 [dependency], 利润弹性受限于 [constraint].

[NEW LOGIC paragraph — 1 paragraph]
从 2024 年开始，业务逻辑发生了结构性变化。[New value driver] 取代 [old] 成为核心收入来源。具体表现在 [specific data points — shift in revenue mix, new customer wins, new products]. [Management quote with date and speaker] 证实了这一转变。

[WHY NOW + ENDGAME — 1-2 paragraphs]
这一转变不是偶然的 — [structural driver such as AI buildout, trade war, technology inflection, policy change]. [Industry data point showing the structural change is real].
如果这个转变顺利完成，[Company] 将在 [time window] 成为 [endgame description] — 估值框架也将从 [old multiple framework] 重估为 [new multiple framework].
```

#### Block B: 运营逻辑 (Operating Logic)

**Length**: 2-4 paragraphs + 1-2 tables
**Purpose**: HOW does the business logic convert into P&L, and when?

**Must include:**
- Named facilities with current capacity and ramp schedule
- Capex cadence (quarterly or annual capex with guidance)
- Utilization targets with dates (e.g., "2026 末预计达到 85% 利用率")
- Product mix shifts with specific revenue numbers
- **Bottom-up unit economics** for commodity/industrial/capacity-driven companies:
  - Production volume × realized price × unit margin = EBITDA contribution
  - See `references/commodity-math-template.md` or use this pattern:
    - Unit output (tons / lb / GW / # chips / TWh)
    - Realized price (spot-adjusted or long-term contract)
    - Unit cost (AISC or cash cost)
    - Unit margin = price − cost
    - EBITDA = unit margin × volume − fixed costs
- **Operating leverage decomposition** (incremental margin walk):
  - "From Q1 to Q4, revenue +$XM, gross profit +$YM, incremental gross margin = Y/X = Z%"
  - "EBITDA change: +$WM, incremental EBITDA margin: W/X = V%"
- **Byproduct credits** if applicable (sulfuric acid, silver from JV, vanadium from uranium ops, etc.) — NEVER skip these for mining/industrial companies

**Capacity ramp table (when applicable):**
```
| Facility | Current | 2026 Target | 2027 Target | Investment | Status |
|----------|---------|-------------|-------------|-----------|--------|
| Thompson Falls | 100 t/mo | 300 t/mo | 500 t/mo | $35M | Q1 2026 投产 |
```

**Hard rules:**
- If production guidance is not disclosed, ASK for Bloomberg data — do NOT fall back to consensus without a bottom-up walk
- Operating leverage MUST be quantified if the thesis relies on margin expansion. "Operating leverage release" without numbers is a buzzword.
- Byproduct credits require a dollar value, not just acknowledgment

#### Block C: 客户与订单 (Customers & Orders)

**Length**: 1-2 paragraphs + 1-2 tables
**Purpose**: Who pays this company, and how locked-in is the revenue?

**Must include:**
- **Top-5 customers by NAME** (from 10-K customer disclosures or Bloomberg SPLC data). If customer names are not disclosed, use named segments or geographies as proxy AND explicitly state the limitation.
- Revenue share per customer (%)
- Strategic significance per customer (one phrase)
- Customer CAPEX trend (are they in expansion mode?)
- **Contract/backlog walk** — contract-by-contract if disclosed:
  - Contract value, counterparty, contract form (firm / IDIQ / framework)
  - 2025 delivery, 2026 delivery, remaining
- **Customer concentration risk** — top-5 share and 3-year trend
- **Supply chain bottleneck** — single most critical dependency (one sentence)

**Customer table format:**
```
| 客户 | 营收占比 | 趋势 | 战略意义 |
|------|---------|------|---------|
| NVIDIA | ~15% | 快速增长 | AI GPU 测试核心客户 |
| Samsung | 12% | 稳定 | 存储 + SoC 双线供货 |
```

**Contract walk format:**
```
| 合约 | 总额 | 2025 交付 | 2026 交付 | 状态 |
|------|------|----------|----------|------|
| DLA IDIQ | $245M | $10M | $50-60M | 首批发货 |
| Bolivia | $75M | 0 | $30M | 2026 Q2 启动 |
```

**Hard rules:**
- Do NOT substitute end-market percentages ("computing 27%") for named customers unless customer names are legitimately undisclosed
- When using segment/geography as proxy, state: "Top customer names not disclosed in 10-K; using geographic proxy"

#### Block D: 财务数据 (Financial Data)

**Length**: Tables + 2-3 paragraphs commentary
**Purpose**: Show the numbers that support the thesis and flag quality concerns.

**Must include:**
- **3-year financial comparison table** (Revenue, Gross Margin, EBITDA, Net Income, EPS, FCF, FCF Margin)
- **Forward model table** with explicit growth drivers in column headers (not just "consensus"):

```
| 指标 | 2026E | 驱动力 |
|------|-------|-------|
| 收入 | $1,680M | 汽车 +24% × 占比 19% + 计算 +25% × 27% + 其他持平 |
| 毛利率 | 34% | 内部晶圆厂利用率 72%→82%，摊销降 +300bp |
| EBITDA | $244M | 14.5% 利润率 |
```

- Management guidance (with date of guidance)
- **2-3 key earnings call quotes with dates and speakers** — these are critical. Preserve exact dates and speaker names.
- Variance analysis (volume / price / mix decomposition) for material revenue changes
- Accrual ratio: (net income − OCF) / average total assets — rising ratio is a quality concern

**Financial Quality Sub-analysis (silent unless material):**

Build these internally; surface findings inline when they affect the thesis:
- **Revenue quality**: value_creating vs pass_through vs agency. If pass-through > 30%, report core margin separately.
- **Earnings quality**: GAAP vs adjusted bridge. If GAAP-to-adjusted bridge has >3 items, list each. If SBC > 10% of operating income, disclose impact on both operating margin and FCF.
- **Cash flow decomposition**: OCF, maintenance capex (or depreciation as proxy), growth capex, FCF, maintenance FCF, cash conversion ratio (OCF / net income).
- **Return metrics**: ROE (with DuPont decomposition when material), ROIC (NOPAT / average invested capital), gross / operating / net margin trends.
- **Leverage metrics**: Net debt / EBITDA, interest coverage.

Hard rule: Do NOT create lettered sub-sections ("Financial Quality Sub-Component A/B/C/D/E") in the final output. These are analysis buckets, not report sections.

#### Block E: 催化剂 (Forward Catalyst Calendar)

**Length**: Table + 1-2 paragraphs
**Purpose**: What events could move the stock in the next 6-12 months?

**Must include:**
- At least 3 forward catalysts in the next 6-12 months
- For each: specific date (or QX 2026), event, bull case outcome, bear case outcome, monitoring source

```
| 日期 | 事件 | 预期影响 | 监控源 |
|------|------|---------|--------|
| 2026-02-10 | Q4 财报 | 毛利率回升确认 | IR 网站 |
| 2026-03 | Thompson Falls 投产 | 产能提升 100→300 t/mo | 季度运营更新 |
| 2026-04 | DoD Phase 2 订单决定 | $50-100M incremental | DoD 公告 |
```

**Prioritize catalysts that could move the stock >5%.**

#### Block F: Valuation Hand-off (Content Block Mode only)

When called by the orchestrator, emit one paragraph identifying:
- The archetype-appropriate primary valuation method (NOT 9 methods)
- Key inputs for that method (2026E EBITDA, 2027E EPS, diluted share count, net debt)
- The catalyst that re-rates the multiple

Do NOT produce a full valuation model — that's the `valuation-calculator` skill's job. Just hand off the inputs.

#### Block G: Unresolved Items

**Length**: 3-5 items
**Purpose**: Every honest analysis has questions it can't fully answer.

```
| 问题 | 什么证据可以解答 | 何时可得 | 影响级别 |
|------|----------------|---------|---------|
| 内部晶圆厂利用率当前水平 | 下次电话会或 10-K 披露 | Q1 2026 | Serious |
```

Hard rules:
- "Fatal" = entire thesis could be wrong; "Serious" = direction unchanged but magnitude affected; "General" = local adjustment only
- If the unresolved items list is empty, the analysis is not honest enough — every company has blind spots
- Do NOT use vague language ("expected to improve") to mask uncertainty

---

### 6. Archetype-Specific Extensions

Add archetype-specific blocks when relevant. These extend (not replace) the core blocks above.

#### `frontier`
- Certification status, commercialization gates, cash runway, dilution ladder, partner quality

#### `turnaround`
- Maturity wall, refi path, interest burden, covenant headroom, asset-sale dependency

#### `consumer_health_platform`
- Product concentration, retention/cross-sell, marketing efficiency, regulatory distribution risk, fulfillment margin

#### `b2b_software_platform`
- Customer concentration, NRR/expansion, SBC and true FCF, legal/accounting quality, data privacy

#### `digital_bank_or_lender`
- Funding stack, asset-liability sensitivity, credit quality, capital ratios, regulatory status

#### `lending_marketplace`
- Funding stack, partner funding quality, credit quality, securitization dependence, take rate / fee model

#### `provider_reimbursement`
- Site/facility economics, reimbursement mechanics, collections quality, policy sensitivity, payer/IDR dependency

#### `resource_policy`
- Permit path, offtake, realized pricing, processing capacity, working capital
- **Commodity math block is MANDATORY** for this archetype — see `references/commodity-math-template.md`

#### `industry_chain_context`
- Supply-demand balance, bottleneck map, policy catalysts, company bridge, NO valuation

---

### 7. Quality Gates Before Answering

- Reject excluded sources and patterns listed in `references/source-policy.md`
- Do NOT use technical analysis, chart patterns, or Wyckoff phase labels — that's the `technical-analysis` skill's job
- **Target price IS allowed** when running in Standalone Mode (hand off to valuation-calculator or state your own)
- Block fundamental analysis conclusions if:
  - Fully diluted share count is unverified
  - Dilution stack is unverified
  - Debt stack or net-debt bridge is unverified
  - Any claim depends on `mou` / `pilot` / `framework` / management aspiration / planned capacity / uncontracted capacity
  - `economic_dependency` is `high` and the relevant regulatory gate is not `approved` or `qualified`
- When pass-through revenue > 50% of total, surface the core-margin figure inline
- Semantic claims (`moat`, `network effect`, `platform`, `data flywheel`) require claim-gate verification per `references/claim-gates.yaml`. If minimum evidence is incomplete, downgrade to inference label.

---

## Style Rules

### DO

- Write as one analyst with a clear point of view
- Use "我们"/"我认为"/"从数据看" for opinions and observations
- Reference Bloomberg screenshots naturally when provided
- Use **bold** for key numbers and conclusions
- Keep paragraphs to 3-5 sentences max
- Preserve dated management quotes verbatim with speaker names
- End with forward-catalyst calendar and unresolved items

### DO NOT

- Do NOT start with "数据充分性说明" section
- Do NOT use "Commercial Evidence Table", "Claim Gate", "value_creating", "Financial Quality Sub-Component A/B/C/D/E" as visible section headers
- Do NOT use "第一部分/第二部分" numbering
- Do NOT write "Meta-Question Self-Reflection" in the output (use it as a private sanity check)
- Do NOT write "Conditional Judgment" framing as a visible section
- Do NOT use `target_price` language at the end in Content Block Mode — hand off to valuation-calculator
- Do NOT duplicate technical analysis — that's a separate skill
- Do NOT end with a matrix. End with unresolved items and catalyst calendar in prose.

---

## Supporting Files

- `references/angle-library.yaml` — Runtime routing and archetype angles
- `references/angle-library.md` — Human-readable backup
- `references/claim-gates.yaml` — Semantic claim evidence thresholds
- `references/source-policy.md` — Allowed and excluded source types
- `references/proprietary-data.md` — Bloomberg data request protocol
- `references/report-digests.yaml` — Offline summaries of research corpus
- `references/financial-analysis-framework.md` — Detailed financial quality methodology
- `references/bloomberg-request-templates.md` — Standard data request templates
- `references/commodity-math-template.md` — (NEW) Bottom-up unit economics template for mining/industrial
- `references/sec-parser-integration.md` — (NEW) 10-K semantic extraction patterns, including risk-factor YoY diffing

---

## Anti-Truncation Verification (Before Emission)

Before emitting content blocks, verify:

- [ ] Every named customer from research is in Block C
- [ ] Every dated management quote is in Block A or D with speaker + date preserved
- [ ] Every forward catalyst with a date is in Block E
- [ ] Every unresolved item is in Block G
- [ ] Bottom-up unit math is in Block B for commodity/industrial archetypes
- [ ] Byproduct credits are in Block B (mining/industrial only)
- [ ] Operating leverage is quantified in Block B if the thesis depends on margin expansion
- [ ] 3-year P&L table + forward model table in Block D
- [ ] Contract walk in Block C if backlog exists

If any item fails, regenerate the relevant block — do NOT silently omit.
