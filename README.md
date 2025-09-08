# IDS706_week2-3-assignment

This assignment is the first part of a two-week project. Choose a beginner-friendly dataset from sources like Kaggle or public APIs. Perform basic data analysis using Pandas (and Polars for advanced students). This includes importing data, inspecting it, applying filters and groupings, and optionally visualizing it. You’ll also begin exploring a machine learning algorithm of your choice.

## Import the Dataset
"amazon_products_sales_data_uncleaned.csv"- 38.6MB


## Inspect the Data

### Coding Part
##### Pandas and Polars respectively
 1. Display the first 5 rows using .head() to get a quick overview.
 2. Use .info() and .describe() to understand data types and summary statistics.
 3. Check for missing values and duplicates

### Analysis part: Data overview 
there are 42657 rows and 16 columns. All of the entires are string. The headers(the first row) are title, rating, number_of_reviews, bought_in_last_month, current/discounted_price, price_on_variant, listed_price, is_best_seller, is_sponsored, is_couponed, buy_box_availability, delivery_details, sustainability_badges, image_url, product_url, collected_at.

1. Title: name of the product; 0 null value 
2. Rating: Amazon ratings in the format of "X.X out of 5 stars"; 1024 null values 
3. Number_of_reviews: strings with "," as character separator; 1024 null values corresponidng to rating
4. Bought_in_last_month：in the format of "XX+ bought in past month"; 3217 null values + some unmeaningful strings such as "Typical:", "List Price, " etc.
5. Current/discounted_price: contain "," as separator; in the format of "XX.XX"; 12941 null values 
6. Price_on_variant: in the format of "basic variant price: $XX.XX / XX Count(Pack of X) / XX GHz / nan / ..." ; 0 null values
7. Listed_price: contain "," as separator; in the format of "$XX.XX" or "No Discount" (listed_price = current/discounted_price in this case); 0 null values 
8. Is_best_seller: Binary variable: "No Badge" or "Best Seller"; 0 null value
9. Is_sponsored: Binary variable: "Sponsored" or "Organic"; 0 null value
10. Is_couponed: "Save XX% with coupon" or "No Coupon"l 0 null value
11. buy_box_availability: null means unavailabile; "Add to cart"; 14653 null values 
12. delivery_details: estimated delivery date as of the day collected the data; format example "Delivery Mon, Sep 1"; 11720 null values
13. sustainability_badges: several categories, need further inspection; 39267 null values 
14. image_url: format example "https://m.media-amazon.com/images/I/71pAqiVEs3L._AC_UL320_.jpg"; 0 null value
15. product_url:  2069 null values 
16. collected_at: format example "2025-08-21 11:14:29"; 0 null value 



## Clean the data 
### Coding Part
1. Clean "rating": 
    remove " out of 5 stars" in rating with str.replace(), and change the string data type into float using pd.to_numeric()
2. Clean "number_of_review":
    remove "," separator in number_of_reviews with str.replace()
3. Clean "current/discounted_price":
    fill the null current/discounted_price with price_on_variant
    1. replace cells without "$" to NA, and remove "basic variant price: $" part in price_on_variant
    2. apply cleaned price_on_variant to missing current_discounted_price
    3. remove all "," separator in current/discounted_price and convert to numeric
    4. check again the missing value in current/discounted_price after cleaning
4. Clean "listed_price":
    remove"$" in listed_price and replace "No Discount" with current/discounted_price

### Analysis Part
I chose four main columns to clean, mainly dealing with converting data type for future manipulation, and clean null values. There are still 2062 missing values in current/discounted_price and listed_price, which are aligned with each other after cleaning.


## Basic Filtering and Grouping
 1. keep only title, rating, number_of_reviews, current/discounted_price, listed_price columnsApply filters to extract meaningful subsets of the data.
 2. Use groupby() to group the rating and get the corresponding average number_of_review, current/discounted_price and listed_price.



## Explore a Machine Learning Algorithm
 I chose to generate a Random Forest model and a XGBoost model to compare with each other in terms of their RSME and R^2
 




## Visualization
 


## Documentation
 Explain your steps and findings in this README.md file.



