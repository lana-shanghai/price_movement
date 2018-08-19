# price_movement

A simple model predicting the movement of cryptocurrency prices up or down up to six hours ahead of time.

The file price_movement_top_coins.ipynb
takes the minute price data for 50 coins from the top of the coinmarketcap from cryptocompare to train and then predicts a price for a coin exactly 60 minutes later. 
Some additional factors are calculated, namely, volatility for the past 60 minutes, returns for the past 60 minutes, and the Sharpe ratio, and checks is there is an up trend. 

Then two types of algorithms are applied to the data. First, a random forest classifier, second, a sequential keras model. 

The accuracy for the random forest has shown to be higher (up to 91% on the collected data), so it is used for the prediction of a chosen coin, whereas the neural network has shown up to 73%. It also selects the features that are the most significant in the prediction, in this case, it is the volatility. It is recommended to choose a coin from the top 100, because the behavior of the higher groups and lower groups of coins tend to correlate within the groups. 

For future testing of the models, I would select aggregate trading volumes and their up or down dynamics, longer and shorter price dynamics regarding the returns and volatility, and more internal trends (the rolling mean 30 vs rolling mean 60 is quite a simplified version). 

The performance of both models decreases over time, so the data and the training should be updated immediately before the prediction for a coin.

The file price_movement_random_forest_hours predicts growth in exactly 1, 2, 3 ... 6 hours. 
It has shown a very interesting result, accuracy for:

1 hour - 54%
2 hours - 62%
3 hours - 61,3%
4 hours - 64%
5 hours - 65,7%
6 hours - 71,4%

which shows us that the time intervals between the hour points allow to make a better prediction on a slightly longer time interval.
Also, we see that the prediction using the minute data in the first notebook gives better results than the hourly data. 
