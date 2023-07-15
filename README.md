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


First, we identify the initial purchase month for each customer by finding the minimum invoice date, which we then name it as 'first_purchase'. Subsequently, we calculate the number of months that have passed since the customer's first purchase and name it as 'indexx' column. We store the results of this query in a Common Table Expression (CTE) as we will utilize them in subsequent stages.



![ke](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/45ebe194-962f-47f6-b3c1-58a941bf31c2)


### Second stage
Here, we group the data by 'first_purchase' and 'indexx', counting the unique customer IDs within each group.

![stage2](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/6907b133-b4a0-4356-8c30-e762987003e5)

### Third stage
Finally, we calculate the retention rate for each group by utilizing the 'first_value' window function to identify the initial cohort size. We then divide the count of each cohort by this initial cohort size to determine the retention rate.
![stage3](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/82ec8ffc-b600-465e-b4c1-0c170ef015ad)


### Bonus Stage!
Previously we used the count of the uniques customerid to make our cohorts and measure the retention rate,but what if we wished to use a different measure? It is definitely possible. Here, I will utilize revenue as the metric to evaluate the retention of each group. The overall process remains quite similar but with  some minor differences

1)We need to calculate the revenue column by multiplying the quantity and unit price columns to determine the total revenue
2)Instead of using the 'count' function, we will switch to the 'sum' function.

![bonusstage](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/73ce073f-eda2-4e0f-859e-63769134d4ef)


