# VIVENDO-BRAZILLIAN-FAST-FOOD-COMPENSATION-CLAIMS
![sm_f7b6c861bd80a6dfd15d04c4919ff73e](https://github.com/Olauryn/VIVENDO-BRAZILLIAN-FAST-FOOD-COMPENSATION-CLAIMS/assets/118401566/9e1e4942-d6e5-4485-88f7-9d649652ee86)

Vivendo Brazilian is a fast food chain in Brazil with over 200 outlets. (Not a real fast food outlet)


## **INTRODUCTION**
**Vivendo** is a fast food chain in Brazil with over 200 outlets.
Customers often **claim compensation** from the company for food poisoning.
The legal team processes these claims. The legal team has offices in four locations.
The legal team wants to improve how long it takes to reply to customers and close claims.
The head of the legal department wants a report on how each location differs in the time it
takes to close claims.

## **TOOL USED FOR THE ANALYSIS**
Power BI and Excel

## **PROBLEM STATEMENT**
The legal team wants to **improve how long it takes to reply to customers and close claims** and 
the head of the legal department wants **a report on how each location differs in the time it
takes to close claims**

## **DATASET DESCRIPTION**
**The dataset contains **2000** rows and **8** fields with the following description;

**claim_id:** Nominal. The unique identifier of the claim. Missing values are not possible due to the database structure.

**time_to_close:** Discrete. The number of days to close the claim. Any positive value. Replace missing values with the overall median time to close.

**claim_amount:** Continuous. The initial claim requested in the currency of Brazil, rounded to 2 decimal places. Replace missing values with the overall median claim amount.

**amount_paid:** Continuous. Final amount paid. In the currency of Brazil. Rounded to 2 decimal places.Replace missing values with the overall median amount paid.

**location:** Nominal. Location of the claim, one of “RECIFE”, “SAO LUIS”, “FORTALEZA”, or “NATAL”. Remove missing values.

**individuals_on_claim:** Discrete. Number of individuals on this claim. Minimum 1 person. Replace missing value with 0.

**linked_cases:** Nominal. Whether this claim is linked to other cases. Either TRUE orFALSE. Replace missing values with FALSE.

**cause:** Nominal. Cause of the food poisoning. One of “vegetable”, “meat” or “unknown”. Replace missing values with ‘unknown’

## **DATA VALIDATION**

The dataset received contained **8 fields**, a total count of **2000 rows**. First thing I did was to observe the data sets and define the rules for the dataset by checking each of the fields data type and adjusting them to the appropriate data type. I also checked for consistency, accuracy, duplicates, tested for outliers and randomly conducted a sample check to ensure the data meets the defined rules and standards. 
From my observation I noticed the following from each of the fields in the dataset. 

**Claim_id:** There were **2000 unique and distinct values** in this field, no missing values and duplicates. This is due to the database structure and it matches with the description of the dataset given. 

**time_to_close:** This is the number of days to close the claim. There were no missing values and there were **256 distinct and 55 unique values** and also the records in this field contained only positive values ranging from **76–518**. This field matches with the description of the dataset given.

**claim_amount:** there are **2000 unique and distinct values in this field**, and the datatype was a text data type, but to ensure easy manipulation of the records in this field, I had to separate the currency sign **(R$)** from the number values in this field, converted the data type to the appropriate data type and renamed the column **“claim_amount (R$)”** to indicate that the values in this field is in currency form and rounded up the values to 2 decimal point. 


**amount_paid:** This field had some errors, that is it contained some records **“NA”** which isn’t correct as this field is supposed to contains number values. This NA makes it difficult to get the correct datatype, hence I replaced all the values that contained **NA** with the overall **“median amount_paid”** which was **“20105.70”** and rounded the values in this field to 2 decimal places. The number of records containing NA in this field was **“36”**. This field contained 1964 distinct values and 1962 unique values. 


**Location:**  This field had **4** unique records **“REECIFE”**, **“SAO LUIS”**, **“FORTALEZA”** and **“NATAL”** which matches the description of the dataset provided and there were no missing values. 

**individuals_on_claim:** There was no missing values in this record and it contained **15** distinct values with a minimum of **“1”** person and ranges from **1 to 15** which matches the description of the dataset given. 

**linked_cases:** In this field, I discovered that we had **3** distinct values, **“TRUE”**, **“FALSE”** and **“NA”**, in the dataset, but this field is to either contain **“TRUE” or “FALSE”** hence I replaced all **“26”** records containing “NA” with the value “FALSE”.

**Cause:** This field is to contain **three** values **“vegetable”, “meat” and “unknown”**, but I observed that this field contained two same values in the field that has same spellings but in different capitalization format **(“VEGETABLES” and “vegetable”)**. Since other records in this field were in lower case and also the expected format, I transformed all **“16”** records with **“VEGETABLES” to “vegetable”** and also transformed the **“14”** record containing **“Meat” with a leading white space in this field to “meat”** for uniformity and also to match the description of the dataset given. 

## **STATING THE NUMBER OF MISSING AND ERROR VALUES**

**amount_paid:** The total number of missing values is **36** which were replaced with the overall median value of the column **“20105.70”**

**linked_cases:** The total number of misssing values is **26** which were replaced with the value **"FALSE"**

**cause:** This total number of error values is **16 and 14** which were replaced by the appropraite value **"vegetables" and "meat"** respectively. 


## DATA VISUALIZATION AND INSIGHTS 

## What is the number of claims in each location and which location has the highest claims**

The dataset comprises of four unique locations, **RECIFE (7101)**, **SAO LUIS (4161)**, **FORTALEZA (2508)**, and **NATAL (2329)** among which **RECIIFE** had the highest count of individual claims which was 7101, while **NATAL** had the lowest count of individual claims which was 2329. 

<img width="604" alt="Screenshot 2023-04-23 163412" src="https://github.com/Olauryn/VIVENDO-BRAZILLIAN-FAST-FOOD-COMPENSATION-CLAIMS/assets/118401566/ae3ebcab-4f46-4cda-bd22-4d5d1cb1c180">


### Explain whether the observations are balanced across categories of the variable location.

Upon examining the sum of claims in each location, it is evident that the observations are not balanced across categories of the variable location. **RECIFE** has the highest sum of claims with **7101**, while **NATAL** has the lowest with **2339**. The substantial differences in the sum of claims between RECIFE and the other locations suggest a significant imbalance in the dataset.
To also assess the extent of the imbalance, we computed the **relative frequencies** of claims in each location, by dividing the sum of claims in each location by the total sum of claims and then multiplying it by 100, thereby giving us the percentage of claims in each location. The relative frequency of claims in RECIFE is **44.10%**, SAO LUIS is **25.85**%, FORTALEZA is **15.58%** and NATAL is **14.47%** and then we determine if the proportions or percentage of observations in each category are roughly equal, that is within 5-10% of each other. 

Based on these findings, it is clear that the observations are not balanced across categories of the variable location when considering the sum claims. Therefore, we should exercise caution when drawing conclusions or making generalizations about the claim’s distribution based solely on these four locations. 

**RELATIVE FREQUENCIES CALCULATIONS**


_RECIFE (7101/16,099) *100 = **44.10%**_


_SAO LUIS (4161/16,099) *100 = **25.85%**_


_FORTALEZA (2508/16,099) *100 = **15.58%**_


_NATAL (2329/16,099) *100 = **14.47%**_



**PERCENTAGE OF OBSERVATION IN EACH CATEGORY CALCULATIONS**

To determine if the percentages are within 5-10% of each other, I calculated the range of the percentages.

Then find the highest and lowest percentages:

**Highest percentage: RECIFE = 44.10%
Lowest percentage: NATAL = 14.47%**

Next, we calculate the range by subtracting the lowest percentage from the highest percentage:

**Range = 44.10% - 14.47% = 29.63%**

To determine if the percentages are within 5-10% of each other, I calculated the maximum allowable difference between any two percentages. This can be done using the following formula:

**Maximum allowable difference = (range * 0.1) = 2.963%**

Now we can compare the percentage differences between each pair of locations to see if they are within the maximum allowable difference:

_RECIFE vs. SAO LUIS: 44.10% - 25.85% = 18.25%_


_RECIFE vs. FORTALEZA: 44.10% - 15.58% = 28.52%_


_RECIFE vs. NATAL: 44.10% - 14.47% = 29.63%_


_SAO LUIS vs. FORTALEZA: 25.85% - 15.58% = 10.27%_


_SAO LUIS vs. NATAL: 25.85% - 14.47% = 11.38%_


_FORTALEZA vs. NATAL: 15.58% - 14.47% = 1.11%_

From these calculations, we can see that the percentage differences between RECIFE and FORTALEZA, and RECIFE and NATAL are both greater than the maximum allowable difference of **2.963%.** Therefore, we can conclude that the observations are not balanced across categories of the variable location.

## Describe the distribution of time to close for all claims. 

<img width="579" alt="Screenshot 2023-04-23 202216" src="https://github.com/Olauryn/VIVENDO-BRAZILLIAN-FAST-FOOD-COMPENSATION-CLAIMS/assets/118401566/e7f416a7-6403-44f3-a08e-8da6b6d6242d">

The distribution of time to close for all claims can be described based on the number of claims made within each time range.

To further understand the distribution of time to close for all claims, we can calculate the relative frequencies of claims in each time range. We do this by dividing the count of claims in each time range by the total count of claims and multiplying by 100.

_Relative frequency of claims for 100-199 days: (1428 / 2000) * 100 = 71.40%_ 

_Relative frequency of claims for 200-299 days: (489 / 2000) * 100 = 24.45%_ 

_Relative frequency of claims for 300-399 days: (53 / 2000) * 100 = 2.65%_

_Relative frequency of claims for 70-99 days: (24 / 2000) * 100 = 1.20%_ 

_Relative frequency of claims for 400 days and above: (6 / 2000) * 100 = 0.30%_

From these calculations, we can see that the majority of claims **(about 71%)** were closed within the time range of **100-199 days**. The number of claims decreases as the time range increases, with only **0.30%** of claims taking 400 days or more to close. This suggests that the distribution of time to close for all claims is heavily skewed to the left, with the majority of claims closing within the first 200 days. The legal team has more claims between **100 and 199 days** compared to all other days distributions, making this period of time the time period with the highest number of individual food poisoning claims.

## Describe the relationship between time to close and location. 

<img width="535" alt="Screenshot 2023-04-23 204648" src="https://github.com/Olauryn/VIVENDO-BRAZILLIAN-FAST-FOOD-COMPENSATION-CLAIMS/assets/118401566/b50ad7fc-adfb-42a8-bccf-669b223c1adf">

**RECIFE** has the highest sum of claims with **7101**, and also the highest time to close claims with **885**. This suggests that the location with the highest sum of claims also had the longest time to close claims on average.

**SAO LUIS** has the second-highest sum of claims with **4161**, and also the second-highest time to close claims with **517**. This suggests that the location with the second-highest sum of claims also had the second-longest time to close claims on average.

**FORTALEZA** has the third-highest sum of claims with **2508**, and also the third-highest time to close claims with **311**. This suggests that the location with the third-highest sum of claims also had the third-longest time to close claims on average.

**NATAL** has the lowest sum of claims with **2339**, and also the shortest time to close claims with **287**. This suggests that the location with the lowest sum of claims also had the shortest time to close claims on average.

Therefore, we can observe a **negative relationship** between time to close and location, where locations with a higher sum of claims tends to have a higher average time to close the claims. This could indicate that there are differences in the efficiency of claims processing across locations, and that locations with a higher workload may have a longer processing time.







