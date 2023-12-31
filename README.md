# INTRODUCTION
This project involves conducting a Cohort Analysis using a real world dataset. The aim is to measure the retention rate of the created groups.
the tools iam  using are: SQL(T-SQl),Power query and PowerBI 
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
Previously we used the count of the unique customerids to make our cohorts and measure the retention rate,but what if we wished to use a different measure? It is definitely possible. Here, I will utilize revenue as the metric to evaluate the retention of each group. The overall process remains quite similar but with  some minor differences

1)We need to calculate the revenue column by multiplying the quantity and unit price columns to determine the total revenue

2)Instead of using the 'count' function, we will switch to the 'sum' function.


![bonusstage](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/73ce073f-eda2-4e0f-859e-63769134d4ef)


## Visualzation
I am using  powerBI to visualize the finding,i created two views in the database to present the results of cohort analysis for each metric: one for the count of customers and the other for the sum of revenue.I then integrated these views into PowerBI to visualize them. 

![cohort](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/7313af48-fa36-4fc6-8648-46dedb978e17)


The Y-axis represents the months in which the customers were acquired.

The X-axis represents the number of months after their first purchase.

Every square on the chart indicates the percentage of customers who returned in a particular month.


As we know PowerBI dashboards are interactive, enabling us to selectively view the chart for a particular group, such as the March 2011 cohort, as illustrated below.
![cohortmarch](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/6af93f3f-4cc1-4ad0-a462-d40f50f1968e)

We can examine how that group performed based on both of our metrics during that timeframe.

## Conclusion


As we would expect,the retention rate for each group naturally decreases over time. However, what's intriguing is the observed increase in the retention rate during the last months of the year, particularly in November. This suggests that some customers from that group, who had previously stopped making purchases, have chosen to return. One possible explanation for this phenomenon could be the surge in demand during the holiday season, which includes events like Black Friday and Cyber Monday. As an E-shop these holiday promotions likely attract customers back to the store, leading to the observed rise in retention during this period.

Overall Cohort analysis enables businesses to uncover customer behavior patterns that may not be obvious at first glance.Its a powerfull tool that can help many business.These insights help optimize marketing strategies, improve customer experiences and ultimately driving business success.



