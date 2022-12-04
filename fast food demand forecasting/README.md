# Fast food demand forecasting
 

Demand forecasting is a key component to every growing online business. Without proper demand forecasting processes in place,it can be nearly impossible to have the right amount of stock on hand at any given time. A food delivery service has to dealwith a lot of perishable raw materials which makes it all the more important for such a company to accurately forecast daily and weekly demand.

Too much invertory in the warehouse means more risk of wastage,and not enough could lead to out-of-stocks - and push customers to seek solutions from your competitors. 
Your client is a meal delivery company which operates in multiple cities.They have various fulfillment centers in these cities for dispatching meal orders to their customers. The client wants you to help these centers with demand forecasting for upcoming weeks so that these centers will plan the stock of raw materials accordingly. The replenishment of majority of raw materials is done on weekly basis and since the raw material is perishable,the procurement planning is of utmost importance.Secondly, staffing of the centers is also one area wherein accurate demand forecasts are really helpful.Given the following information,the task is to predict the demand for the next 10 weeks(Weeks: 146-155) for the center-meal combinations in the test set:

Historical data of demand for a product-center combination(Weeks:1 to 145)
Product(Meal) features such as category,sub-category,current price and discount
Information for fulfillment center like center area, city information etc.


Evaluation Metric
Submissions are evaluated on Root Mean Square Error (RMSE) between the predicted probability and the observed target. The evaluation metric for this competition is 100*RMSLE where RMSLE is Root of Mean Squared Logarithmic Error across all entries in the test set.

Data Split
Test data is further randomly divided into Public (30%) and Private (70%) data.


Data transformation
Here number of orders placed (target variable) is highly right skewd so that Log transformation is applied.
Log transformation of base_price, checkout_price, and num_orders.

Feature engineering
For every record difference between base_price and checkout_price.
Differenc of previous week checkout_price and current weeks checkout_price.
Lag features of 10,11, and 12 week lagging features. Here I have used lag of last 10 weeks because we have to predict for 10 weeks in test dataset.
Exponentially weighted mean over last 10, 11, and 12 weeks.

Cross validation
Last 10 weeks (136 - 145) of every center-meal pair data is used as a Validation dataset from train dataset.


Model
Comparison between catboost , XGB boost , decision tree and the model with best accuracy and Rmse is took for prediction.
High regularization so it does not overfit because of new features made using target variable.



