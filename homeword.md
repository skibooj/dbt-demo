## Week 4 Homework 
[Form](https://forms.gle/B5CXshja3MRbscVG8) 

We will use all the knowledge learned in this week. Please answer your questions via form above.  
* You can submit your homework multiple times. In this case, only the last submission will be used. 


### Question 1: 
**What is the count of records in the model fact_trips after running all models with the test run variable disabled and filtering for 2019 and 2020 data only (pickup datetime)**  
You'll need to have completed the "Build the first dbt models" video and have been able to run the models via the CLI. 
You should find the views and models for querying in your DWH.
>Code:
```sql
SELECT COUNT(*) from `electric-goods-340611.production.fact_trips`  
WHERE pickup_datetime BETWEEN '2019-01-01' AND '2020-12-31'
```
**result:** 61587856

**closest answer:** 61635151
### Question 2: 
**What is the distribution between service type filtering by years 2019 and 2020 data as done in the videos**

You will need to complete "Visualising the data" videos, either using data studio or metabase. 

[distribution](https://user-images.githubusercontent.com/22966749/155297326-c90d6edf-a29e-4728-be30-c1e2b3d62d95.png)

### Question 3: 
**What is the count of records in the model stg_fhv_tripdata after running all models with the test run variable disabled (:false)**  

Create a staging model for the fhv data for 2019 and do not add a deduplication step. Run it via the CLI without limits (is_test_run: false).
Filter records with pickup time in year 2019.

>Code:
```sql
SELECT count(*) FROM `electric-goods-340611.production.stg_fhv_tripdata`;
where extract(year from pickup_datetime) in (2019)
```
**answer:** 42084899

### Question 4: 
**What is the count of records in the model fact_fhv_trips after running all dependencies with the test run variable disabled (:false)**  

Create a core model for the stg_fhv_tripdata joining with dim_zones.
Similar to what we've done in fact_trips, keep only records with known pickup and dropoff locations entries for pickup and dropoff locations. 
Run it via the CLI without limits (is_test_run: false) and filter records with pickup time in year 2019.

>Code:
```sql
SELECT count(*) FROM `electric-goods-340611.production.fact_fhv_trips`
where extract(year from pickup_datetime) in (2019)
```

**answer:** 22676253


### Question 5: 
**What is the month with the biggest amount of rides after building a tile for the fact_fhv_trips table**
Create a dashboard with some tiles that you find interesting to explore the data. One tile should show the amount of trips per month, as done in the videos for fact_trips, based on the fact_fhv_trips table.


[link to raport](https://datastudio.google.com/reporting/03ac886b-d68d-4740-b867-0a8af4404b74/page/0DXmC)
