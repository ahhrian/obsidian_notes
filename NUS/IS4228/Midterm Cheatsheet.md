### Key Formulae (Manual)
**Time Value of Money**
- PV of a Lump Sum: $PV=\frac{C}{(1+r)^{n}}$ 
- PV of Ordinary Annuity: $PV=C[\frac{1-(1+r)^{-n}}{r}]$
- PV of Growing Annuity: $PV=C_{1}[\frac{1-(\frac{1+g}{1+r})^{n}}{r-g}]$ 
- PV of a Perpetuity: $PV=\frac{C}{r}$
- PV of Growing Perpetuity: $PV=\frac{C_{1}}{r-g}$
- Future Value (FV): $FV=PV(1+r)^{n}$
- Net Present Value (NPV): $NPV=\sum_{i=0}^{n}\frac{C_{i}}{(1+r)^{i}}$
- Effective Annual Rate (EAR): $EAR=(1+APR/k)^{k}-1$
- Internal Rate of Return (IRR): $\text{Return \% needed for NPV} = 0$
		** _Use Excel formula: RATE(Periods, CFs, PV, FV)_

**Bond Valuation and Risk**
- Zero-Coupon YTM: $YTM=(\frac{FV}{P})^{1/n}-1$
- Coupon Payment: $CPN = \frac{\text{Coupon Rate} \times FV}{\text{Payments per Year}}$
- Coupon Bond Price: $P=\frac{CPN}{y}(1-\frac{1}{(1+y)^{N}})+\frac{FV}{(1+y)^{N}}$
- Credit Spread: $\text{Credit Spread} = YTM_{corp} - YTM_{Treasury}$
- Estimated Price Change: $\Delta P \approx (-Duration)(\Delta y)(P_0)$
		** _y refers to change in yield_

**Stock Valuation**
- Perpetual Dividend Growth: $P_{0}=\frac{Div_{1}}{r-SGR}$
- Sustainable Growth Rate: $SGR=(\text{Retention}) \times (\text{Return on New Investment})$
- Total Payout Equity Value: $\text{Equity Value} = PV(\text{Future Dividends} + \text{Repurchases})$
- Total Payout Per-Share Value: $\text{Per-share value} = \frac{\text{Equity Value}}{\text{Outstanding Shares}}$
- Free Cash Flow: $FCF = EBIT \times (1-Tax \ Rate) - \text{Net Investment} - \Delta NWC$
- Discounted FCF Enterprise Value (EV): $EV = PV(\text{Future FCFs})$
- Equity-Enterprise Value Equation: $\text{Equity} = EV - \text{Debt} + \text{Cash}$
- Terminal Value (Discounted FCF): $TV_{N}=\frac{FCF_{N+1}}{WACC-g}$ <- Perpetually growing FCF
- Fundamental Equation of Stock Return: $P_{0}=\frac{Div_{1}+P_{1}}{1+r_{E}}$
	- Total Return: $r_{E}=\frac{Div_{1}+P_{1}}{P_{0}}-1=\frac{Div_{1}}{P_{0}}+\frac{P_{1}-P_{0}}{P_{0}}$
- Equity Cost of Capital: $ECC = \text{Risk Free Rate} + \text{Risk Premium}$
- General Dividend-Discount Model: $P_{0}=\sum_{n=1}^{\infty}\frac{Div_{n}}{(1+r_{E})^{n}}$ <- PV of all future Dividends
- Weighted Average Cost of Capital: $WACC=\frac{Equity}{Equity+Debt}*ECC+\frac{Debt}{Equity+Debt}r_{D}(1-Tax \ Rate)$
	** _Using Market Values of Equity (Market Cap.) & Debt

**Risk, Return & Portfolio Theory**
- Expected Return: $E[R]=\sum(p_{R}\cdot R)$
- Expected Yield: $Expected \ Yield = (\frac{Expected \ Return}{Bond \ Price})^{1 \div n} - 1$
- Variance: $Var(R)=\sum P_{R}(R-\mathbb{E}[R])^{2}$ <- $P_R$ = Probability of return, R
- Realized Return: $R_{t+1}=\frac{Div_{t+1}+P_{t+1}}{P_{t}}-1$
- Realized Annual Returns: $1+R_{annual}=(1+R_{1})(1+R_{2})...(1+R_{n})$ <- N periods per year
- $Real \ Return = Nominal \ Return - Inflation \ Rate$
- Portfolio Weights: $x_{i}=\frac{\text{Value of investment } i}{\text{Total value of portfolio}}$
- Portfolio Return: $R_{p}=\sum x_{i}R_{i}$
- Covariance: $Cov(R_{i},R_{j})=\frac{1}{T-1}\sum_{t}(R_{i,t}-\overline{R_{i}})(R_{j,t}-\overline{R_{j}})$
- Correlation: $Corr(R_{i},R_{j})=\frac{Cov(R_{i},R_{j})}{SD(R_{i})SD(R_{j})}$
- Portfolio Variance: $Var(R_{p})=\sum_{i}\sum_{j}x_{i}x_{j}Cov(R_{i},R_{j})$

**CAPM & Pricing Models**
- Beta: $\beta_{p}=\frac{Cov(r_{p},r_{b})}{Var(r_{b})}$
- Alpha: $\alpha = R_p - \beta_p(R_M - R_f)$
- CAPM Expected Return: $E[r_{i}]=r_{f}+\beta_{i}\times(E[r_{Market}]-r_{f})$
- Expected Return with Alpha: $r_{i}=r_{f}+\beta_{i}\times(E[r_{Market}]-r_{f})+\alpha_{i}$
- Sharpe Ratio: $\text{Sharpe Ratio}=\frac{E[R_{P}]-r_{f}}{SD(R_{P})}$
- Required Return for $i$ relative to portfolio $P$: $r_{i}=(E[R_{P}]-r_{f})\beta_{i}^{P}+r_{f}$
- Regression Approach: $R_{i}-r_{f}=\alpha_{i}+\beta_{i}(R_{M}-r_{f})+\epsilon_{i}$

### Excel Formulae
- RATE(Periods, CF, PV, FV)
	- Set PV & FV to be opposite signs (PV generally is initial cost of Investment)
	- USAGE: Finding IRR, given fixed Coupons (if any), PV (initial cost) and FV
### Concepts & Common Mistakes
**Bonds & Risk**
- Selling safe bonds (e.g. T-Bills) before maturity is **NOT** risk-free (still subject to fluctuations in I.R.) which causes price change --> Only risk-free if held to maturity
- If YTM @ point of sale = Original YTM (i.e. coupon rate), IRR = YTM
	- if YTM @ Sale Increases, IRR Decreases
	- $\text{IRR (Zero-Coupon Bonds)} = (\frac{Value \ @ \ sale}{PV_0})^{(1 \div N)} - 1$
- If Int. Rate (or YTM) < Coupon Rate, Bond Value > Par
- Longer maturity bonds MORE sensitive to YTM changes
	- More periods to compound the higher/lower discount rate
- Lower Coupon bonds MORE/LESS ? (TBC)

**Sovereign Bonds Vs Corporate Bonds**
> 1. Governments can print money to make up unpayable amount (corporate cannot)
> 	- This causes "soft" default since value of money FALLS due to inflation
> 	- Reduced purchasing power, effectively means the $1000 face value isn't going to give them the same purchasing power as it should (i.e. effectively getting less money)
> 2. Gvt can default strategically (for political reasons), corp. only default when insolvent (cannot pay)
> 3. Creditors cannot seize government assets as easily and quickly as corporate assets during defaults

**Benefits of Tokenisation**
1. T+0/T+1 settlement of payments (compared to T+2), i.e. much faster
2. 24/7 trading, not limited to banking hours
3. Automated compliance & regulation - smart contracts embed KYC/AML rules
4. Fractional ownership of tokens, lowers minimum investment threshold (increase accessibility)