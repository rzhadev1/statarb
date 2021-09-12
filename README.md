# statarb 
An implementation of a statistical arbitrage model, done on jupyter notebook. Based on Avendella, Lee 2008. 

### Notes
- *Only SP500 Stocks are used (with stocks that have less than 1 year of data exluded), although a larger stock universe should be used*
- *ETF returns are used as market factors, but could be easily replaced by another multi-factor model such as PCA*
- *Different signal parameters are used than described in Avendella, in order to lean more towards long positions than short positions* 
- *1 year of backtest data is used (August 3rd, 2020 - August 3rd, 2021)*
- *Backtests start at day 60 in the data, as the estimation window is 60 days to account for 2 earnings cycles*
- *The model is given $300,000 to simulate in backtest. This is to emulate a 130/30 fund with $1,000,000 in a market-wide index ETF such as SPY. The actual returns for this model would be the SP500 return + model returns, but the jupyter notebook focuses on the model return.* 
- *The code is... not very good.*
- *Using -1.25 and -0.5 entry/exit signals for long positions, 2.0 and 1.25 for short entry/exit signals.*


### An Overview of Statistical Arbitrage
<ol>
<li>Regress stock returns onto corresponding ETF returns</li>
<li>Find the cointegrated residual between the SPDR sector ETF and the stock</li>
<li>Estimate the OU process and generate trading signals </li>
<li>Use trading signals to construct a market-neutral portfolio of stocks</li>
<li>Allocate equal amounts of capital to each position </li>
<li>Calculate returns based on holdings </li>
</ol>

### Results and Findings 
- Two of the worst performing stocks, DISCK and DISCA, had unforeseen volatility due to the collapse of Archegos Capital Management in March 2021. Strangley, VIAC, which was also part of Archegos's portfolio, had positive returns in our model. 
- Total Return: $25,359.38
- Percentage Return: 8.45%
- Sharpe Ratio: 1.5125

![PnL](cumulativepnl.png)

- Best and worst performers out of all 501 Stocks

![best](topperformers.png)

![worst](worstperformers.png)

- Mean reversion strength distribution, where 1/k gives mean reversion time

![kappadist](kappadistribution.png)

- Signal Evolution for DISCA

![DISCAsig](DISCAsignal.png)
![DISCAgraph](DISCAgraph.png)

- Signal Evolution for ENPH

![ENPHsig](ENPHsignal.png)
![ENPHgraph](ENPHgraph.png)

### TODO
- Add portfolio weighting optimization, such that faster mean reverting stocks are chosen over slower reverting stocks. 
- Possibly connect to IBKR to test on live data
- Fix bugs relating to negative stock beta, which shouldn't be possible 
- Bug relating to K values where mean reversion time is calculated to be less than half a day 
- Track trades with detailed information. The current backtest code block makes this not really possible. 















 


