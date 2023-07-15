# Cohort-Analysis
This project involves conducting a Cohort Analysis using a real world dataset. The aim is to measure the retention rate of the created groups.
## What is  Cohort Analysis
 Cohort analysis is a type of behavioral analytics in which you take a group of users, and analyze their usage patterns based on their shared traits to better track and understand their actions. A cohort is simply a group of people with shared characteristics.

## Dataset 
The dataset is about an E-commerce shop from England, containing half a million transactions that occurred between 2010 and 2011.



![right](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/50fea3d9-bc23-4d23-9467-eb2f70ee20f3)



## Data Cleaning
After examining our dataset, it appears that there are 135,080 rows with an empty customerid column. In order to conduct a cohort analysis, it is necessary to have the "customerid" information. Therefore, we have decided to remove these rows, resulting in a decrease in our dataset size from 541,909 rows to 406,829 rows.



![missing](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/421ed29e-9b42-4457-a377-6e4f6d61e9e9)



After creating a Common Table Expression (CTE) and continuing to explore our dataset, we have discovered that the quantity column contains negative values. This occurrence may be attributed to damaged or returned items.


![negative](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/248eded1-0a5c-493e-8783-a6a2195a5453)


After removing these values, we ultimately create a new table called cleaned_table, which contains 399,994 rows. Now we're ready to start our analysis

## Conducting cohort analysis

### First stage
First, we identify the initial purchase month for each customer by finding the minimum invoice date. Then, we calculate the duration in months since that month for each record in our dataset.
![ke](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/45ebe194-962f-47f6-b3c1-58a941bf31c2)






