# Trading Algorithms
## Description:
Our trading strategy is split into two distinct algorithms. One is the pairs mean reversion algorithm and the other is a foreign exchange strategy based on the RSI and MACD indicators. Only the pairs algorithm is complete at this time as the forex algo is a work in progress. 
## An Overview of the Pairs Algorithm:
This algo is very simple. We must first design a sub algorithm to calculate equities that are cointegrated (think pepsi vs coke). We then take these two equities and measure their moving averages over two distinct time periods (for example 5 days vs 60 days). By calculating these averages we can track the overall predicted changes in the price of each equity. Then we can map the ratio between the two equities, by doing this we can see when one is either outpreforming or underpreforming compared to the expected ratio between them (i.e. if one stock is massivley outpreforming its corrolated partner or underpreforming compared to its partner). We can then manipulate this to be constantly updating during the trading day (in this case we recalculate a moving average every hour). From this information we can calculate the z score of the pair (to check if one is outpreforming/underpreforming) and trade accordingly. Mean reversion comes into play because if one member of the pair is outpreforming the average we can predict, based on the thesis of mean reversion, that it will return to its expected value. As a result we can short the outpreformer and go long on the underpreformer and generate profit on both sides of the pair. 
### Part 1: Calculating Pairs 
The algorithm to calculate pairs is located in the find_pairs_algo.py file. Basically, we take a set of stocks and get its historical data (using the TD ameritrade api, setup for this api is located in the Analysis_TDA.py file), for the close price over the past year. We then use this close data to calculate the moving average over time for this equity. 
After we do this for two equities we can generate our first plot:
