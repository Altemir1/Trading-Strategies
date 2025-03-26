# Mean Reversion Trading Strategy

## Overview
The *Mean Reversion Strategy* is based on the assumption that stock price is tend to return to its mean, when it goes from the mean price significantly up or down. Sources states that this strategy is only useful during sideways market, as it's not volatile and don't create huge spikes where startegy is losing money. For the testing of the strategy I use stock of the company called KEGOC. This company works in energy sector and one of the biggest in Kazakhstan. The reason behind selecting this stock, is that prices fluctatues in the same range over last 2 years. Perfect fit fro the strategy at first glance. 

## Data collection
- Downloaded data from MarketWatch site. Link: https://www.marketwatch.com/investing/stock/kegc/download-data?startDate=3/13/2022&endDate=3/14/2023&countryCode=kz
- Ticker: `KEGC` (KEGOC)
- Date range: `14-03-2022` to `13-03-2025`

## Strategy 
For implementation of mean reversion strategy higher and lower bollinger bands were used to identify significant level of deviation from the mean. Simply, as the close price was going over higher band the sell order was made and for the lower band the buy order was made. In this example we only considered KEGOC stock and compared it with basic buy and hold strategy returns. To find best parameters for the window and standard devation value for the bollinger bands, delay of the order the grid search was used. 

Best final values for each parameter:
- `window` = 45
- `std` = 1.0
- `delay` = 1

## Results
![mean-reversion-kegoc](https://github.com/user-attachments/assets/1c62ff39-bdb4-4505-99bc-5e3d7b01d9da)

From 10000 dollars that was used in simualtion, strategy made 990 dollars of profit, which is equivalent of 9,9% of return, while buy and hold strategy made -12% of profit. As a conclusion, one can say that this strategy is better than just buy and hold, but it only have been tested on one stock. In further investigation it will be clearer if this strategy is good of use.
