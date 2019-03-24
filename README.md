# Business Analytics and Data Science WS1819
#projectdesc


In this repository, you can find:
- My term paper which describes the project in more detail.
- My code for the final Ensemble Selection - both the Profit-Agnostic version and the Profit-Conscious version.
- The transformed data to go with this code.
- A notebook with basic EDA on the original data.

I've decided to only share the transformed data and Ensembling code since I do not have permission to share the original data. As with most data science projects, about 80-90% of my effort went into data cleaning, EDA and feature engineering.
These were the columns we got initially: 'order_date', 'delivery_date', 'item_id', 'item_size', 'item_color','brand_id', 'item_price', 'user_id', 'user_title', 'user_dob','user_state', 'user_reg_date', 'return'
From this I made features such as 
- 'user_age', 'account_age', 'delivery_time', etc. but also more complex ones such as 
- 'LTV', 'recency', 'bought_on_discount' (by looking at an item_id's average price and comparing it to the price in the order), number of items/different items/colours of the same item bought in the same order, user's preferred colours/sizes and whether the item differs, and
- conditional expectations (CE) for: user_id (making sure to prevent target leak), item_id, combinations of item_id and colour/size to find malfitting versions of the same item, etc.

The process of EDA, data cleaning, feature engineering was accompanied by testing models, in a loop that repeated many times.

<img src = "https://github.com/ANGELMAN-J/Business-Analytics-and-Data-Science-WS1819/blob/master/Leaderboard.jpg" alt = "Kaggle Leaderboard" title = "Kaggle Leaderboard" align = "center" width = "830" />
