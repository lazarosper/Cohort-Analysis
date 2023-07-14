# Cohort-Analysis
This project involves conducting a Cohort Analysis using a real world dataset. The aim is to measure the retention rate of the created groups.
## What is  Cohort Analysis
 Cohort analysis is a type of behavioral analytics in which you take a group of users, and analyze their usage patterns based on their shared traits to better track and understand their actions. A cohort is simply a group of people with shared characteristics.

## Dataset 
The dataset is about an E-commerce shop from England, containing half a million transactions that occurred between 2010 and 2011.



![right](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/50fea3d9-bc23-4d23-9467-eb2f70ee20f3)



## Data Cleaning
Starting with our dataset it seems that there are 135,080 rows where the customerid column in empty,as to conduct a cohort analysis we need to have the customerid
we choose to remove this rows,decreasing our dataset from  541,909 rows to  406,829



![missing](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/421ed29e-9b42-4457-a377-6e4f6d61e9e9)



Afterward i create a CTE  and continue exploring our dataset,we found that  the quantity columns include negative values this may be because the items were damaged or returned 



![negative](https://github.com/lazarosper/Cohort-Analysis/assets/119593480/248eded1-0a5c-493e-8783-a6a2195a5453)


Nevertheless we excludes this values, finally we create a new table called cleaned_table that has 399,994 rows and we are ready to begin our Analysis
