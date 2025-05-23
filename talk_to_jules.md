we should consider the reasoning model? so the training should like this.

llm based on the timing, price and indicator signals to create and execute the trading plan
the plan should include, open price, profit-taken, stop-loss, trading duration etc, predict success rate...)
then we provide next 5 mins bar just like market does, we also provide calculated indicators value to llm. based on those new input. llm provide altered trading plan (adjust PT and SL and trading duration) or decide to close the trading to make max profit and min loss.
if the trading still going on, repeat the step 3.
if trading closed or no trading, monitor the market change and prepare for the next trading.

