# Moving Averages Crossover Strategy
This simple strategy uses fast and slow simple moving averages. Fast SMA is an average of the window of 40 till 60 days, for slow the values from 180 to 220 window of the days was used. 
The logic is when fast MA goes higher than slow MA when put buy order as it's assumed that prices will go up, when such happens it's called golden cross. In the opposite when fast MA goes lower than
slow MA we put sell signal indicating that prices may go down, it's called death cross.

## Data collection
For the stocks we used top 10 companies by the market cap and gathered data for the last 10 years using yfinance.
- Tickers: `["AAPL", "MSFT", "NVDA", "AMZN", "GOOG", "2222.SR", "META", "BRK-B", "TSLA", "TSM"]`

## Strategy implementation
Gridsearch technique was used to find best parameters in given range.
```python
parameter_grid = {
    "shortterm_window": list(range(40, 61, 5)),
    "longterm_window": list(range(180, 221, 10)),
    "lag": list(range(0, 6))
}
```
## Results
For the evaluation we compared strategy to simple buy and hold, and results shown that MAC strategy was more profitable than B&H only in one stock. It's Nvidia, as for last several years it had huge upward trend.
In the notebook provided you can see the plot of returns of MAC and B&H strategies. Additionally plots for the buy and sell orders according to the MAC.
``` table
           shortterm_window  longterm_window  lag  total_return_%  sharpe_ratio  
AAPL                   60              180    3          256.30          0.60   
MSFT                   40              220    0         1008.15          1.07   
NVDA                   50              180    2        48167.90          1.52   
AMZN                   40              220    0          471.82          0.72   
GOOG                   60              220    1          274.14          0.62   
2222.SR                40              220    5           20.54          0.33   
META                   40              200    1          268.41          0.54   
BRK-B                  45              180    2           72.32          0.38   
TSLA                   60              180    1          116.77          0.42   
TSM                    40              200    1          491.24          0.72
```
