
**Warmup period:** Used for generating signals / rules only, not trading decisions

General Backtesting
- Start & End date are pre-defined (e.g. Jan 2015 - Jan 2025)
	- Get results (metrics like Sharpe ratio, return, etc.) overall
	- Essentially same as 1 sample per year of data, calculate all metrics
		- Aggregate these metrics


Sample Rule
- If Short-Term Moving Avg. (STMA) > Long-Term MA (LTMA) --> Go Long
	- Else (STMA < LTMA) --> Short
- Can use 50 & 60 day MA (STMA) and 200 & 300 day MA (LTMA)
	- 4 possible combinations of STMA & LTMA (assuming 1 of each)
	- As params / number of STMA / LTMA increase, number of combinations increase exponentially
		- Try to start with smaller variety of params to avoid computational over-head & decision paralysis

Vectorised Backtesting
- Focuses on the close price & is computationally more efficient
- Add columns in an empty dataframe for close price + all params (e.g. STMA, LTMA, etc.)
- Set a "Position" value based on params
	- E.g. if the STMA > LTMA --> Position = 1 so STMA < LTMA = -1
	- When Position value changes we take that as a "Signal"
		- STMA has crossed from BELOW LTMA to ABOVE LTMA (Pos. = -1 --> Pos. = 1)
		- Get Signal based on Position (e.g. Difference of Position < 0 --> Long)
- Plot signals on the graph of Price, STMA & LTMA
	- See if Signals correctly reflect actual price movement in coming days
	- Calculate Log returns for Stock & the Strategy (assuming we follow signals)
		- Sum all of Log returns
		- Convert to regular returns (for easier calculation & conversion to metrics)
	- Metrics of the strategy & stock --> see if strategy is *perfoming better* than buy & hold stock
		- Consider if the strategy matches expected return and acceptable risk appetite


Drawdowns:
- When / How often does the strategies' live/moving total returns (cumsum) falls below to its maximum cummulation of returns 
	- e.g. After 50 days, cummulative return was 40% <-- current maximum
		- By day 60 it has dropped to 35% (drawdown period since current cummulative return is less than the maximum we achieved till now, 40%)
		- See how many days it takes to cross 40% cumsum returns, and how far below 40% it goes (lowest value) before it goes upward and crosses 40%
	- The MAXIMUM drop (drawdown) between cumsum & actual return is the "actual" / "final" drawdown
		- Decide if the drawdown is acceptable or not (does it last too long, and is it too far below the maximum return?)
		- Good to figure out when to change to a new strategy (old edge is gone/paused temporarily)
		- Continue live backtesting until we expect the edge to come back and re-enable the strategy if it every comes back (don't get rid of the strategy?) --> for longer term algo trading



Event Based Backtesting:
- More realistic simulation of the trading strategy (employs all the High, Low, Close, Open values????)
	- More computationally heavy
- Can decide whether your limit orders will actually be executed or not