# capstone1

Google Data Analytics - Cyclistic Bike share

CAPSTONE PROJECT:

The project aims at using various data analytics in a Marketing Analyst team for a Fictional Bike share company called Cyclistic. In cyclistic, there are two different type of users a.Casual rider and b.Members. 
Members  have annual subcriptions where the casual riders don't. Also,Lily Morelo-Marketing executive team suggests that the company's future success depends on maximizing the number of annual membershiip

1. The Business Task:
a. To identify how the casual riders and members use the ride share service differently
b. Marketing strategy to convert the casual riders to members.
Insights lead to the understanding of how the casual riders and the annual members use the cyclistic bikes differently, this can in turn be used to develop marketing strategies to convert the casual riders to annual members.

2. A description of the data source used:
Data Location: https://divvy-tripdata.s3.amazonaws.com/index.html

Public dataset. The data has been made available by Motivate International Inc. under the license: https://ride.divvybikes.com/data-license-agreement

Due to privacy reasons, one cannot determine the location in which the casual riders live, whether it is near the service area or somewhere else. Cannot determine if they have purchased the pass multiple times.

ROCCC – Reliable, Original, Comprehensive, Current, Cited

Data is credible, as it is accurate, data can be used to arrive to informed data driven decision making aimed at solving the business problem defined above.

3. Cleaning and manipulation of data in excel:
i. Dowloaded the last 12 months of data from the link mentioned above in data source section and extracted them into a folder.
ii. For each excel, added the column 'day_of_the_week' - which says in which day the ride has been started. used the function '=weekday(column)' in excel.
iii. For each excel, added a column 'month' to determine whether the data belongs to the month as each excel belongs to one month. used the function '=month(started_at)' in excel. Here there is a strong assumption, although the ride started in one month and prolonged to the next month,only the start time is considered.
iv. For each excel, added the column 'date-difference' to determine if there is some error in the data. used the formula '=ended_at-started_at'. For instance, the started_at is 12/03/2021 and the ended_at is 10/02/2021. Therefore, this column allowed us to see if there is any negative value potraying such flaws in data. Fortunately, there was not any. 
v. Exported the excel folders to google cloud storage, as the file size was huge to be imported from local computer while using bigquery(sql).

4. Analysis and Insight generation in bigquery(sql):
i. Created a new project called 'cyclistic-chicago-data'.
ii. Created a new dataset under the above project with the name 'cyclistic_data'.
iii. Imported all the twelve months table from the google cloud storage, stored them under the 'cyclistic-data' dataset.
iv. After importing all the tables, combined all the tables vertically under the same column name without any duplicate data using the function 'UNION DISTINCT'

The query:
select *
from `cyclistic-chicago-data.cyclistic_data.january_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.february_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.march_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.april_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.may_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.june_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.july_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.august_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.september_month`
union distinct 
select *
from `cyclistic-chicago-data.cyclistic_data.october_month`
union distinct
select *
from `cyclistic-chicago-data.cyclistic_data.november_month`
union distinct
select *
from `cyclistic-chicago-data.cyclistic_data.december_month`

all the tables are combined using the above query, and the resulting table is stored using the 








Dashboard
![Dashboard](https://user-images.githubusercontent.com/101074709/157043796-eeca7552-39f6-41e1-821a-c5687dbfe468.jpg)
