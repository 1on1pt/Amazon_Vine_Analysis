# Amazon_Vine_Analysis
Using Big Data techology to complete a Big Data analysis using Google Colab, AWS RDS, PySpark, PostgreSQL, and pgAdmin.

## Overview of the Analysis
![amazon_vine_image](https://user-images.githubusercontent.com/94148420/162590757-c6b5e1e7-e145-4bfe-ab97-1346d37b4fe1.jpg)

Since the work with Jennifer on the SellBy project was so successful, you’ve been tasked with another, larger project: analyzing Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

In this project, the **Automotive dataset** was selected for analysis. This analysis included using PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. PySpark was used to determine if there is any bias toward favorable reviews from **Vine members (paid)** as compared to **non-Vine Members (unpaid)** in the dataset.

### Resources
#### Code:
* Amazon_Reviews_ETL.ipynb
* Vine_Review_Analysis.ipynb

#### Data:
* https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt
* https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Automotive_v1_00.tsv.gz

#### Software/Data Tools:
* Google Colab
* pgAdmin 4 v6.4
* PostreSQL
* PySpark
* AWS RDS


## Results
### Determine Bias of Vine Reviews

#### The Amazon Data was loaded into a Spark DataFrame.  In this project, the *Automotive* dataset was used.
![load_data_into_spark_df](https://user-images.githubusercontent.com/94148420/162591789-8375000a-e512-47b6-9159-86c5ccf29359.PNG)


#### Clean the data.
![clean_data](https://user-images.githubusercontent.com/94148420/162591828-0d777c48-9cea-4930-a437-33918b3eb691.PNG)


#### Create the vine_table.
![vine_df](https://user-images.githubusercontent.com/94148420/162591863-d4fd598e-4c91-48e6-9bb4-55efce2679a0.PNG)


#### Filter to show total votes are equal to or greater than 20.
![votes_greater_equal_twenty](https://user-images.githubusercontent.com/94148420/162591912-5ac5a152-0f2a-43e3-9e2b-dccce8e7518a.PNG)


#### Filter to create a new DataFrame/Table to retrieve all rows where the number of helpful_votes/total_votes is greater than or equal to 50%.
![helpful_total_greater_equal_fifty](https://user-images.githubusercontent.com/94148420/162591986-5b644e99-9e5a-4315-92c6-90bfaf39f7ba.PNG)


#### Filter to create a new DataFrame that retrieves the *helpful* reviews that were written as part of the Vine program (paid), vine == 'Y'.
![vine_paid](https://user-images.githubusercontent.com/94148420/162592058-2fe70ff2-4ab0-4aab-b930-b58f1147dd4b.PNG)


#### Filter to create a new DataFrame that retrieves *helpful* reviews that were not part of the Vine program(unpaid), vine == 'N'.
![vine_unpaid](https://user-images.githubusercontent.com/94148420/162592105-80792585-7980-4861-99f6-bdc864e3afd6.PNG)


#### Total number of *helpful* reviews (paid + unpaid).
![total_number_reviews](https://user-images.githubusercontent.com/94148420/162592165-2c7c3227-5235-462d-a7a5-e12461e7d465.PNG)


#### Total number of Vine *helpful* reviews (paid).
![total_paid](https://user-images.githubusercontent.com/94148420/162592214-fd38a131-3344-42fa-bbb2-0324b5475676.PNG)


#### Total number of non-Vine *heflpful* reviews (unpaid).
![total_unpaid](https://user-images.githubusercontent.com/94148420/162592249-bc504f8d-bad2-4f61-a266-935d52b81b2c.PNG)


#### Total number of 5-star *helpful* reviews (paid + unpaid).
![total_number_five_star_reviews](https://user-images.githubusercontent.com/94148420/162592644-7d05460c-5fc1-41c8-a97c-e733eb4fa448.PNG)


#### Total 5-star Vine *helpful* reviews (paid).
![total_five_star_paid](https://user-images.githubusercontent.com/94148420/162592304-a27c5614-ef09-4d13-ac0c-2ed330ecee48.PNG)


#### Total 5-star non-Vine *helpful* reviews (unpaid).
![total_five_star_unpaid](https://user-images.githubusercontent.com/94148420/162592357-74203d5a-6ea7-4cc9-a587-1397ed970a26.PNG)


#### Percentage of Vine *helpful* reviews (paid) that are 5-star.
![percent_five_star_paid](https://user-images.githubusercontent.com/94148420/162592390-1dd1d142-0b3a-49c4-94dc-40128a6ab44f.PNG)


#### Percentage of non-Vine *helpful* reviews (unpaid) that are 5-star.
![percent_five_star_unpaid](https://user-images.githubusercontent.com/94148420/162592413-00e855d0-1928-4afe-ac15-c8c78083f320.PNG)


## Summary
The results indicate that the Vine members (paid) **did not show any positivity bias** towards their reviews when rating the Automotive products.  The evidence is that  39.3% of Vine members (paid) rated the Automotive products as being 5-star, whereas non-Vine members (unpaid) rated the Automotive products as 5-star 48.4% of the time.  The Vine members appear to be more critical of these products than the non-Vine members.

Had the numbers been reversed, i.e. Vine members rating 5-star 48.4% of the time and non-Vine members rating 5-star 39.3%, one could argue that there is Vine member bias with giving 5-star written reviews.

Additional analyses that could be performed would include:
* Include not only *helpful votes*, but all votes even if they were not considered *helpful*.  The reviewer may not consider *helpfulness* in their rating.
* Include only the data where the purchase is **verified**.
* 
