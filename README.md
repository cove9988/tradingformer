# Plan
Fine-Tuning an LLM for Forex Trading
1. Model Selection Choose a large language model (LLM) suitable for fine-tuning in the context of Forex trading. The model should demonstrate strong understanding of price movements, financial indicators, and trading strategies.
2. Forex Data and Signal Definition
   * Select a Forex trading pair (e.g., EUR/USD) and use historical data with 5-minute bar intervals.
   * Identify and use multiple technical indicators (e.g., MACD, RSI, Bollinger Bands) to define entry and exit signals for trades.
3. LLM Fine-Tuning for Trading Decisions
   * Trade Plan Generation: Train the LLM to generate trade plans based on the technical indicators and market signals. Each plan should include entry points, profit-taking thresholds, and stop-loss levels.
   * Real-time Plan Adjustment: Fine-tune the LLM to dynamically update trade plans as new 5-minute bars are received, with the goal of maximizing profit and minimizing risk in real-time trading scenarios.
   

Background
About Bars in Trading
In trading, price movements over a specific time interval are typically condensed into a structure known as a bar—commonly visualized as a candlestick. In this context, we use the term bar to represent such condensed time-based price data.

A bar encapsulates both random fluctuations and patterned movements (such as trends) within a time period. Therefore, we can think of a bar as a rich source of information that can be embedded into a vector space—an approach we refer to as bar2vec.

Candlesticks represent a time interval using four price points: open, close, high, and low. However, they do not capture the distribution of price movements within that interval. To address this, during bar preprocessing, we can extract additional features, such as statistical descriptors (e.g., normality indicators or intra-bar price distribution), which may not be visually informative for technical analysis but could be highly beneficial for machine learning models.

A sequence of bars over time, regardless of the time unit, forms the language of price movement. However, unlike sequences in NLP, not every bar carries meaningful information. Many bars—especially in short timeframes—are dominated by random noise rather than predictive patterns. The shorter the bar interval (e.g., 1-minute vs 5-minute), the greater the ratio of noise (white noise) to signal.

Given that noise is unpredictable, only clear, strong price movements carry meaningful predictive signals in short timeframes. This is why models based on 5-minute bars often outperform 1-minute bar models—5-minute bars better express trends rather than noise.

Still, the overall information distribution remains a long-tail phenomenon: most bars are noise-dominated and uninformative, while only a small subset—those in the "head" of the distribution—are useful for prediction. This justifies the use of Probabilistic Sparse Self-Attention mechanisms in our encoder/decoder architecture to focus on the most informative parts of the sequence.

Understanding the Trading Market
From a market theory perspective, what drives price changes? Why do prices move at all?

Classical price theory posits:

The market reflects all available information.

Prices move in trends.

History tends to repeat itself.

If these assumptions hold, especially points 2 and 3, then price trends over time are predictable to some extent. Price changes are the result of market behavior, and the market, in turn, is influenced by several core forces:

Market participant behavior — decisions made by banks, institutions, and market makers based on their valuation of the asset.

External information flow — such as interest rate announcements, economic outlooks, or unexpected geopolitical events.

Seasonal and macroeconomic cycles — recurring patterns tied to time of year or economic phases.

However, bar sequences alone only reflect the output (price changes)—they don’t capture the underlying drivers of these changes. Crucially, the most important driver—market participant behavior—is not directly observable or quantifiable.

This introduces information asymmetry into the prediction problem: our models must infer future prices without full knowledge of the forces causing those changes.

To improve predictive reliability, we should incorporate external and temporal context (points 2 and 3 above) into both historical and future price modeling. This means enriching each bar with additional time-based metadata such as:

Hour of the day

Day of the week

Day of the month

Month and year

Trading market or region

Related news sentiment or events

This temporal and contextual data can help bridge the gap between observable price changes and the latent forces behind them.
