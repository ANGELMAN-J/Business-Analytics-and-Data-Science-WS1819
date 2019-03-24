# Business Analytics and Data Science WS1819
For my course Business Analytics and Data Science, all students had to participate in an [in-class Kaggle competition](https://www.kaggle.com/c/bads1718). The goal was to predict product returns using real world data of an online fashion retailer (binary classification with artificially balanced classes). 
The Kaggle competition was scored in terms of AUC and I ranked 2nd out of 118 students.

Grading, however, is in terms of error costs. The idea is that the e-tailer could intervene before an order is made (i.e. by offering fewer payment options, claiming the item is out of stock, etc.) to deter an order that is likely to be returned. To mirror this, we were given a cost matrix with highly asymmetric error costs (false positives are much more costly than false negatives). This turned the challenge from a predictive classification to a prescriptive task.

To account for that, I:
- calculate the optimal decision threshold τ per order and make a profit-maximising decision
- use models calibrated with Platt's Scaling and assessed by a reliability/calibration curve
- build a "zoo" of heterogenous base models
- implemented an Ensemble Selection algorithm to build a selective averaging ensemble from my model zoo, optimising for AUC
- and a version of it optimising for profit.

My final, profit-concious ensemble reduces costs by 30% (compared to never intervening) and 6% compared to a well-tuned Logistic Regression.

In this repository, you can find:
- My term paper which describes the project in more detail.
- My code for the final Ensemble Selection - both the Profit-Agnostic version and the Profit-Conscious version.
- The transformed data to go with this code.
- A notebook with basic EDA on the original data.

I've decided to only share the transformed data and Ensembling code since I do not have permission to share the original data. As with most data science projects, about 80-90% of my effort went into data cleaning, EDA and feature engineering.

These were the columns we got initially: 

'order_date', 'delivery_date', 'item_id', 'item_size', 'item_color','brand_id', 'item_price', 'user_id', 'user_title', 'user_dob','user_state', 'user_reg_date', 'return'

From this I made features such as:
- 'user_age', 'account_age', 'delivery_time', etc. but also more complex ones such as 
- 'LTV', 'recency', 'bought_on_discount' (by looking at an item_id's average price and comparing it to the price in the order), number of items/different items/colours of the same item bought in the same order, user's preferred colours/sizes and whether the item differs, and
- conditional expectations (CE) for: user_id (making sure to prevent target leak), item_id, combinations of item_id and colour/size to find malfitting versions of the same item, etc.

The process of EDA, data cleaning, feature engineering was accompanied by testing models, in a loop that repeated many times informed both by the performance of my models as well as relevant literature.

<img src = "https://github.com/ANGELMAN-J/Business-Analytics-and-Data-Science-WS1819/blob/master/Leaderboard.jpg" alt = "Kaggle Leaderboard" title = "Kaggle Leaderboard" align = "center" width = "830" />
