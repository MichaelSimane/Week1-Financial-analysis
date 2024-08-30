## Task 2: Studying Historical Stock Data

### Objective

In Task 2, I analyze historical data for Apple Inc.'s (AAPL) stock to identify trends and patterns that might help in predicting future stock prices. I also explore various technical indicators and optimization techniques for portfolio management.

### How I Did It

1. **Loading the Stock Data:**
   - I used `yfinance` to fetch historical stock data for Apple Inc. and imported it for analysis.
   
   ```
   import yfinance as yf
   df = yf.download('AAPL', start='2000-01-01', end='2024-01-01')
   df.head()
   ```
   This code retrieves Apple’s historical stock data and displays the first few rows, including metrics such as date, opening price, closing price, and volume.

2. **Analyzing Technical Indicators:**
   - I applied various technical analysis indicators using the `talib` library with a time period of 50 days to understand stock price movements.
   
   ```
   import talib as ta
   
   df['SMA'] = ta.SMA(df['Close'], timeperiod=50)  # Simple Moving Average
   df['RSI'] = ta.RSI(df['Close'], timeperiod=50)  # Relative Strength Index
   ```

3. **Visualizing the Data:**
   - I used `plotly` and `matplotlib` to visualize stock data and technical indicators, helping to identify trends and patterns.
   
   ```
   import plotly.express as px
   import matplotlib.pyplot as plt
   
   fig = px.line(df, x=df.index, y='Close', title='AAPL Stock Price')
   fig.show()

   df[['Close', 'SMA']].plot(figsize=(10, 6))
   plt.title('AAPL Stock Price and Moving Average')
   plt.show()
   ```

4. **Optimizing Portfolios:**
   - I used `pypfopt` to perform portfolio optimization, assessing the risk and return profiles of different stock allocations.
   
   ```
   from pypfopt.efficient_frontier import EfficientFrontier
   from pypfopt import risk_models, expected_returns
   
   mu = expected_returns.mean_historical_return(df['Close'])
   S = risk_models.sample_cov(df['Close'])
   ef = EfficientFrontier(mu, S)
   weights = ef.max_sharpe()  # Maximize the Sharpe ratio
   cleaned_weights = ef.clean_weights()
   ```

### What I Found

My analysis revealed several key insights:

- **Seasonal Patterns:** Apple’s stock prices exhibit consistent seasonal patterns, with specific periods showing better performance. This may be linked to product launches or other significant events.
- **Technical Indicators:** Indicators like the Simple Moving Average (SMA) and Relative Strength Index (RSI), calculated over a 50-day period, provided useful insights into stock trends and potential buy/sell signals.
- **Portfolio Optimization:** Optimization techniques suggested effective stock allocation strategies to maximize returns while managing risk.
