# Analysis of Amazon Reviews.
## Background
The purpose of this project was to determine if the reviews from Amazon's Vine program (Vine; V) were biased or not. To conduct this analysis, Amazon's reviews on baby category were analyzed, by breaking them into paid reviews(V) and un-paid reviews(!V/NV).The data was cleaned and transformed using PySpark (see ETL script)and loaded into PostgreSQL database. The analysis was done through both SQL queries and in a Google colaboratory using Pyspark (check SQL-Queries and Analysis-Challenge).

## Analysis
The raw data composed of 1,752,932 number of reviews(row count), with the oldest recorded review date of 1999-07-13, and the latest recorded review date of 2015-08-31. The data was checked for null and duplicate values for the 'product_id', 'customer_id' and 'review_id' columns. Only duplication found was in the product_id column which was filtered out before loading it into the product table in RDS. 

It was noted that when data was filtered for verified purchases only, the number of V reviews; dropped from 12100 to 19, and !V reviews; dropped from 1740832 to 1392109. However when you check the average star rating across V reviews and !V reviews, for both verified purchase and otherwise, it comes out to be ~4 for all, This suggests that there is little evidence of bias based on these metrics.

### V Review Summary Table:
![](https://github.com/Muzznah/Amazon-Reviews-ETL/blob/master/Images/V-Describe.png)
### NV Review Summary Table:
![](https://github.com/Muzznah/Amazon-Reviews-ETL/blob/master/Images/!V-Describe.png)
### Star Rating Table:
![](https://github.com/Muzznah/Amazon-Reviews-ETL/blob/master/Images/V-!V-starcount.png)

The above three tables highlight that:
   1- Average star-rating break up between V and !V showed only slight difference, with both coming out to be approximately 4.
   2- Average helpful-vote break up between V and !V showed a significant difference, with V getting an average of ~3 compared to ~1 average for !V review.
   3- V reviewers tend to be more conservative while giving a negative rating with only ~5% who gave a low rating of 2-star and none that gave below that.
   4- Majority of V reviewers(~79%) gave a high rating of 4-5 star however it matched up with !V reviewers(~79%) rating of 4-5 stars.
   5- Looking at only the 5-star rating, you see that only ~42% of V reviewers choose it as opposed to ~63% of !V reviewer
   6- Vine reviews are a 0.7% of total reviews and majority of the reviews (~99%) are from regular customers.
## Conclusion
- It seems that most of the vine reviews, are written by people who got the product for free ( as only 19 of them link to a verified purchase) which may have led them to be a little conservative in terms of choosing extreme ratings. However, when you check the average star rating across V reviews and !V reviews, for both verified purchase and otherwise, it comes out to be ~4 for all, This suggests that there is little evidence of bias based on the above metrics.
- Also since they have a higher perecentage of helpful vote, it seems they offer more detail for products merits and demerits.

## Resources
### Data
- https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt
- https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Baby_v1_00.tsv.gz
- 
### Software
- Amazon RDS, Google Colaboratory, spark 3.0.0, Python 3.7.7, PostgreSQL 11.8, pgAdmin4.14
