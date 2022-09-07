# Amazon_Vine_Analysis


## Project Overview

Selecting Amazon Pet Product reviews from a given dataset, the project will utilize PySpark to perform the ETL process to extract the dataset, transform the data, connect to a AWS RDS instance, and load the transformed data into pgAdmin. PySpark will be used to determine if there is any bias toward favorable reviews from Vine members in the dataset.

## Resources
- Data Source: [Amazon Pet Product Review Dataset](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Pet_Products_v1_00.tsv.gz)
- Technology Used: AWS and RDS, PostgreSQL, Google Colab Notebook


## Challenge Overview

### Deliverable 1: Perform ETL on Amazon Product Reviews

Extract the Pet Products Review dataset from an AWS S3 using PySpark in order to tranform the data into datasets that matched the schema of the PostgreSQL tables. The dataset was broken into 4 smaller dataframes:

customer_table:

![customer_colab]()

products_table:

![product_colab]()

review_id_table:

![review_colab]()

vine_table:

![vine_colab]()

Each dataframe was loaded to PostgreSQL and the RDS. Due to the size of each dataframe, it took some time to load. To verify the data loaded correctly, I ran a sql statement on each table.

customer_table:

![customer_sql]()

products_table:

![product_sql]()

review_id_table:

![review_sql]()

vine_table:

![vine_sql]()

### Deliverable 2: Determine Bias of Vine Reviews

Using PySpark, analysis the vine_table dataset to determine if there is any bias towards reviews that were written as part of the Vine program. 

After dropping the nulls the dataset was around 1.7 million reviews. 

Filtering for only reviews with 20 or more votes dropped the dataset down to 65K. 

![twenty or more votes](https://user-images.githubusercontent.com/87085239/183271734-891c9347-4251-40aa-9425-43b1d55e91ea.png)

Next the dataset was filtered for helpful votes at least 50% which brought the total dataset to 40,565.

![50 helpful](https://user-images.githubusercontent.com/87085239/183271817-70e3ee77-78c7-46c0-b171-a929eb93adc1.png)



## Results

- Total Reviews: 38,010

- Paid Vine Reviews
    - Total Reviews:170
    - 5 Star Reviews:65
    - 38.23% of vine reviews were 5-Star

- Non-Vine Reviews
    - Total Reviews:37,840
    - 5 Star Reviews:20,612
    - 54.47% of non-vine reviews were 5-Star


## Summary

It doesn't appear that the vine program is useful for the Pet Products category. Although Vine reviews yield around 31.23% of 5-Star reviews, they only make up around 0.44% of the total reviews. Non-paid 5-Star views is over 37.8K as opposed to 170 paid reviews.

### Additional Analysis

The average paid review is 3.9 and non-paid average around 3.7. 

I would recommend doing further anaylsis on paid reviews and their distribution of ratings and helpful_votes to detemine the quality of reviews being paid for.


 
