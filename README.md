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

![customer_colab](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/Customer_ID.png)

products_table:

![product_colab](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/Product_table.png)

review_id_table:

![review_colab](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/review_id.png)

vine_table:

![vine_colab](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/vine_table.png)

Each dataframe was loaded to PostgreSQL and the RDS. Due to the size of each dataframe, it took some time to load. To verify the data loaded correctly, I ran a sql statement on each table.

customer_table:

![customer_sql](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/custom_sql.png)

products_table:

![product_sql](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/products_sql.png)

review_id_table:

![review_sql](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/review_sql.png)

vine_table:

![vine_sql](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/vine_sql.png)

### Deliverable 2: Determine Bias of Vine Reviews

Using PySpark, analysis the vine_table dataset to determine if there is any bias towards reviews that were written as part of the Vine program. 

After dropping the nulls the dataset was around 1.7 million reviews. 

Filtering for only reviews with 20 or more votes dropped the dataset down to 65K. 

![twenty or more votes](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/20votes.png)

Next the dataset was filtered for helpful votes at least 50% which brought the total dataset to 40,565.

![50 helpful](https://github.com/CorinneBean/Amazon_Vine_Analysis/blob/fb099672080def18c8e03578447ebf067a0a9c33/Images/50votes.png)



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


 
