# Technical Analysis Framework Reference

This file provides detailed methodology guidance for the §9 Technical Structure Assessment appendix in SKILL.md. It synthesizes three authoritative sources into a structured analytical framework.

## Sources

1. **John J. Murphy — Technical Analysis of the Futures Markets** (期货市场技术分析): trend analysis, chart patterns, volume, moving averages, oscillators, Dow Theory
2. **Richard D. Wyckoff Method** (威科夫操盘法): supply/demand dynamics, accumulation/distribution, volume-price analysis, the Composite Man
3. **Steve Nison — Japanese Candlestick Charting Techniques** (日本蜡烛图技术): candlestick patterns, confirmation rules, integration with Western technical tools

## Layer 1: Trend Structure and Key Levels (Murphy)

### Dow Theory — Six Tenets

1. **Averages discount everything.** All known information is already reflected in the price.
2. **The market has three trends.** Primary (months to years), secondary (weeks to months), and minor (days to weeks).
3. **Major trends have three phases.** Accumulation phase (smart money buying), public participation phase (trend followers join), and distribution/excess phase (smart money selling into retail enthusiasm).
4. **Averages must confirm each other.** Sector or index confirmation strengthens signals.
5. **Volume must confirm the trend.** In an uptrend, volume should expand on rallies and contract on pullbacks. In a downtrend, volume should expand on declines and contract on rallies.
6. **A trend is presumed to continue until definitive reversal signals occur.** The burden of proof is on the reversal, not the continuation.

### Trend Identification

- **Uptrend:** series of higher highs and higher lows.
- **Downtrend:** series of lower highs and lower lows.
- **Sideways/range:** peaks and troughs at roughly the same level.

Assess on the weekly chart for primary trend and daily chart for secondary trend. The trend is defined by structure (peaks and troughs), not by a single candle or bar.

### Support and Resistance

- **Support:** a price level or zone where buying interest is sufficiently strong to overcome selling pressure. Identified from prior troughs, consolidation bases, round numbers, and high-volume price areas.
- **Resistance:** a price level or zone where selling interest overcomes buying pressure. Identified from prior peaks, consolidation ceilings, round numbers, and high-volume price areas.
- **Role reversal:** once broken, support becomes resistance and vice versa.
- Report up to 3 levels for each. Use approximate zones, not exact prices.

### Classical Chart Patterns

#### Reversal Patterns

| Pattern | Direction | Key Feature | Volume Behavior |
|---------|-----------|-------------|-----------------|
| Head & Shoulders | bearish reversal | three peaks, middle highest | declining volume on right shoulder; breakout volume on neckline break |
| Inverse Head & Shoulders | bullish reversal | three troughs, middle lowest | increasing volume on right shoulder; breakout volume on neckline break |
| Double Top | bearish reversal | two peaks at similar level | second peak on lower volume; breakout below valley |
| Double Bottom | bullish reversal | two troughs at similar level | second trough on lower volume; breakout above peak |
| Triple Top/Bottom | reversal | three tests of level | declining volume on successive tests |
| Rounding Top/Bottom | reversal | gradual curve | volume mirrors the shape |

#### Continuation Patterns

| Pattern | Description | Volume Behavior |
|---------|-------------|-----------------|
| Symmetrical Triangle | converging trendlines | declining volume during formation; breakout on expanding volume |
| Ascending Triangle | flat top, rising bottom | declining volume during formation; upside breakout expected |
| Descending Triangle | flat bottom, declining top | declining volume during formation; downside breakout expected |
| Flag/Pennant | brief consolidation after sharp move | declining volume during formation; breakout resumes prior trend |
| Wedge | converging lines slanting against the trend | declining volume; breakout in direction of prior trend |
| Rectangle | horizontal trading range | volume spikes at boundaries |

### Moving Average Systems

- **50-day MA:** intermediate trend indicator.
- **200-day MA:** long-term trend indicator.
- **Golden Cross:** 50MA crosses above 200MA — bullish signal.
- **Death Cross:** 50MA crosses below 200MA — bearish signal.
- **Price vs. MA:** price consistently above 50MA and 200MA = healthy uptrend. Price below both = downtrend. Between them = transitional.
- Moving averages are lagging indicators — they confirm trends, not predict them.

### Oscillators (Supplementary)

Use oscillators only as confirming tools, not as primary signals:

- **RSI (14-period):** above 70 = overbought; below 30 = oversold. Look for divergence (price makes new high but RSI does not).
- **MACD:** signal-line crossover and histogram direction. MACD divergence from price is a warning signal.
- **Stochastic:** %K/%D crossover. Effective in range-bound markets; less useful in trending markets.

## Layer 2: Volume-Price Analysis and Market Phase (Wyckoff)

### Three Laws of Wyckoff

1. **Law of Supply and Demand:** when demand exceeds supply, prices rise; when supply exceeds demand, prices fall. Price is the arbiter.
2. **Law of Cause and Effect:** the "cause" is built in the trading range (accumulation or distribution). The "effect" is the subsequent trending move. The duration and width of the cause determines the magnitude of the effect.
3. **Law of Effort vs. Result:** volume is the effort, and price change is the result. They should be in harmony. When effort and result diverge, a change in trend direction may be near.

### Wyckoff Market Cycle

The market moves through four repeating phases:

```
Accumulation → Markup → Distribution → Markdown → (repeat)
```

Within trending phases, **re-accumulation** (continuation pauses in a markup) and **re-distribution** (continuation pauses in a markdown) may occur.

### Accumulation Schematic (Bottom Formation)

Events in sequence:

1. **Preliminary Support (PS):** The first notable buying after a long decline. Volume picks up, price range widens, signaling the decline may be ending.
2. **Selling Climax (SC):** Panicked selling on heavy volume. Price drops sharply but recovers by the close or next session. Marks the rough bottom boundary.
3. **Automatic Rally (AR):** A relief rally as selling pressure subsides. Volume may decrease. The AR high sets the upper boundary of the trading range.
4. **Secondary Test (ST):** Price returns to the SC area, but on less volume and narrower spread. Tests whether selling pressure is exhausted.
5. **Spring (or Shakeout):** Price briefly dips below the SC/ST support level on low volume, then recovers sharply. This "false breakdown" shakes out weak holders and is a signature Wyckoff signal of accumulation.
6. **Sign of Strength (SOS):** Price advances on expanding volume, breaking above resistance within the trading range. Confirms accumulation.
7. **Last Point of Support (LPS):** A final pullback on declining volume. This is the last low before the markup phase begins.

### Distribution Schematic (Top Formation)

Events in sequence:

1. **Preliminary Supply (PSY):** The first notable selling after a long advance. Volume increases and price stalls or dips.
2. **Buying Climax (BC):** A sharp price spike on heavy volume — retail enthusiasm peaks. Marks the approximate top boundary.
3. **Automatic Reaction (AR):** A pullback after the BC. Sets the lower boundary of the trading range.
4. **Secondary Test (ST):** Price revisits the BC area, but on less volume. Tests whether buying pressure is exhausted.
5. **Upthrust (UT):** Price briefly rises above the BC/ST resistance on low volume, then reverses sharply. This "false breakout" traps late buyers and is a signature Wyckoff signal of distribution.
6. **Sign of Weakness (SOW):** Price drops on expanding volume, breaking below support within the trading range. Confirms distribution.
7. **Last Point of Supply (LPSY):** A final weak rally on declining volume. This is the last high before the markdown phase begins.

### Composite Man

The "Composite Man" concept treats the market as if a single large operator is orchestrating price action. This is a mental model for interpreting volume-price behavior — it does not imply actual manipulation. The question is: what would a large, well-informed participant be doing at this price and volume level? Accumulating or distributing?

### Effort vs. Result Analysis

| Scenario | Effort (Volume) | Result (Price) | Interpretation |
|----------|-----------------|----------------|----------------|
| Normal uptrend | Rising | Rising | Trend is healthy |
| Volume-price divergence (bearish) | Rising | Flat or falling | Supply is overcoming demand — potential distribution |
| Normal downtrend | Rising | Falling | Trend is healthy |
| Volume-price divergence (bullish) | Rising | Flat or rising from lows | Demand is absorbing supply — potential accumulation |
| Low volume advance | Declining | Rising | Advance lacks conviction — vulnerable to reversal |
| Low volume decline | Declining | Falling | Decline lacks selling pressure — may be a corrective pullback, not trend change |

## Layer 3: Candlestick Pattern Recognition (Nison)

### Confirmation Rules

1. A candlestick pattern is a **signal**, not a trigger. Confirmation from subsequent price action is required.
2. Patterns are meaningful only at **key technical levels** (support, resistance, trendline, moving average). A hammer in the middle of a range is noise.
3. **Weekly patterns** carry more weight than daily patterns.
4. **Volume** reinforces patterns: a hammer with above-average volume is stronger than one on low volume.
5. **Multi-candle patterns** (engulfing, morning/evening star) are more reliable than single-candle patterns.

### Reversal Pattern Catalog

#### Bullish Reversal Patterns (at or near support)

| Pattern | Candles | Description | Reliability |
|---------|---------|-------------|-------------|
| Hammer | 1 | Small body at top, long lower shadow (2x+ body), little or no upper shadow. After decline. | Moderate |
| Inverted Hammer | 1 | Small body at bottom, long upper shadow, little lower shadow. After decline. Needs confirmation. | Low-Moderate |
| Bullish Engulfing | 2 | Small bearish candle followed by larger bullish candle whose body engulfs the prior body. | High |
| Piercing Line | 2 | Bearish candle followed by bullish candle that opens below prior low and closes above midpoint of prior body. | Moderate |
| Morning Star | 3 | Bearish candle, small-body candle (gap down), bullish candle closing into first candle's body. | High |
| Three White Soldiers | 3 | Three consecutive bullish candles, each closing near its high. | High |
| Abandoned Baby (bullish) | 3 | Bearish candle, doji gapped below, bullish candle gapped above doji. | Very High (rare) |
| Tweezer Bottom | 2 | Two candles with matching lows. | Moderate |

#### Bearish Reversal Patterns (at or near resistance)

| Pattern | Candles | Description | Reliability |
|---------|---------|-------------|-------------|
| Hanging Man | 1 | Same shape as hammer but at top of uptrend. Warning signal. | Moderate |
| Shooting Star | 1 | Small body at bottom, long upper shadow, little lower shadow. After advance. | Moderate |
| Bearish Engulfing | 2 | Small bullish candle followed by larger bearish candle whose body engulfs the prior body. | High |
| Dark Cloud Cover | 2 | Bullish candle followed by bearish candle that opens above prior high and closes below midpoint of prior body. | Moderate |
| Evening Star | 3 | Bullish candle, small-body candle (gap up), bearish candle closing into first candle's body. | High |
| Three Black Crows | 3 | Three consecutive bearish candles, each closing near its low. | High |
| Abandoned Baby (bearish) | 3 | Bullish candle, doji gapped above, bearish candle gapped below doji. | Very High (rare) |
| Tweezer Top | 2 | Two candles with matching highs. | Moderate |

#### Indecision Patterns

| Pattern | Description | Context |
|---------|-------------|---------|
| Doji | Open and close at nearly the same price | At extremes: potential reversal. Mid-range: indecision, low-signal. |
| Spinning Top | Small body, moderate upper and lower shadows | Indecision. Significant after a strong move. |
| High Wave Candle | Small body, very long shadows both ways | Extreme indecision. More significant than spinning top. |

### Continuation Pattern Catalog

| Pattern | Candles | Description |
|---------|---------|-------------|
| Rising Three Methods | 5+ | Long bullish candle, 3+ small bearish candles within its range, then another long bullish candle. Bullish continuation. |
| Falling Three Methods | 5+ | Long bearish candle, 3+ small bullish candles within its range, then another long bearish candle. Bearish continuation. |
| Tasuki Gap (upward) | 3 | Bullish candle, gap up to another bullish candle, bearish candle that doesn't fill the gap. |
| Tasuki Gap (downward) | 3 | Bearish candle, gap down to another bearish candle, bullish candle that doesn't fill the gap. |

## Integration Rules

The three layers work together:

1. **Murphy (Layer 1)** establishes the structural context: what is the trend, where are the key levels?
2. **Wyckoff (Layer 2)** explains the narrative: who is accumulating or distributing, and is volume confirming the move?
3. **Nison (Layer 3)** provides timing signals: what are the most recent candle patterns saying at the key levels identified by Layer 1 and Layer 2?

When all three layers agree, confidence is higher. When they conflict, note the conflict and lean toward the higher-timeframe signal (weekly over daily, primary trend over secondary).

## Data Source Policy for §9

### Acceptable sources for price and volume data

- Exchange-provided historical OHLCV data
- Yahoo Finance, Google Finance (price/volume only)
- TradingView (chart observations, not user-generated ideas or community predictions)
- Bloomberg/FactSet terminal data when user-supplied

### Not acceptable

- Social media technical analysis
- YouTube or KOL chart analysis
- Forum or Discord chart posts
- Signal services or alert systems
- Any source mixing technical analysis with promotional content or position recommendations
