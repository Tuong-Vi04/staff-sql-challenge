# 👯retail_sale-sql-challenge

## 📚 Table of Contents
- [Business task](#business-task)
- [Question and Solution](#question-and-solution)
Please note that all the information regarding the case study has been sourced from the following link: [here](https://github.com/najirh/Retail-Sales-Analysis-SQL-Project--P1). 

***

## Business Task
Solve the questions to find the pattern of sale of the retail sale dataset.

***

## Data cleaning
````sql
SELECT *
FROM retail_sales
WHERE transactions_id IS NULL
  OR sale_date IS NULL
  OR sale_time IS NULL
  OR gender IS NULL
  OR category IS NULL
  OR quantity IS NULL
  OR cogs IS NULL
  OR total_sale IS NULL;
````
#### Results:
| transactions_id |	sale_date  | sale_time |	customer_id |	gender | age | category |	quantity | price_per_unit | cogs | total_sale |
|-----------------|------------|-----------|--------------|--------|-----|----------|----------|----------------|------|------------|
| 679	            | 2022-08-26 | 08:59:00  |	64         	| Female |	18 | Beauty   |		NULL   |      NULL      | NULL |    NULL    |
| 746	            | 2022-07-05 | 11:33:00  |	42        	| Female |	33 | Clothing |		NULL   |      NULL      | NULL |    NULL    |
| 1225	          | 2022-02-02 | 09:51:00  |	137	        | Female |	57 | Beauty   |		NULL   |      NULL      | NULL |    NULL    |

````sql
DELETE
FROM retail_sales
WHERE transactions_id IS NULL
  OR sale_date IS NULL
  OR sale_time IS NULL
  OR gender IS NULL
  OR category IS NULL
  OR quantity IS NULL
  OR cogs IS NULL
  OR total_sale IS NULL;
````
*** 

### Data exploration
**How many sales do we have?**
````sql
SELECT
COUNT(*) as total_sale 
FROM retail_sales
````
#### Results:
| total_sale |
| ---------- |
| 1997       | 

**How many unique customer do we have?**

````sql
SELECT
COUNT(DISTINCT customer_id) as total_sale
FROM retail_sales
````

#### Results:
| total_sale |
| ---------- |
| 155        | 

**How many categories do we have?**
````sql
SELECT
DISTINCT category
FROM retail_sales
````
#### Results:
| category    |
| ----------- |
| Electronics | 
| Clothing    | 
| Beauty      | 

*** 

## Question and Solution

If you have any distributions or questions on my work, reach out to me on [LinkedIn](https://www.linkedin.com/in/nguyenthituongvi/).


**Q.1 Write a SQL query to retrieve all columns for sales made on "2022-11-05"**

````sql
SELECT *
FROM retail_sales
WHERE sale_date ='2022-11-05';
````
#### Results:
| transactions_id |	sale_date  | sale_time |	customer_id |	gender | age | category      | quantity | price_per_unit | cogs | total_sale |
|-----------------|------------|-----------|--------------|--------|-----|---------------|----------|----------------|------|------------|
| 180	            | 2022-11-05 | 10:47:00  |	117        	| Male   |	41 | Clothing      |		3     |      300       | 129  |    900     |
| 240	            | 2022-11-05 | 11:49:00  |	95        	| Female |	23 | Beauty        |		1     |      300       | 123  |    300     |
| 1256	          | 2022-11-05 | 09:58:00  |	29	        | Male   |	23 | Clothing      |		2     |      500       | 190  |    1000    |
| 1587	          | 2022-11-05 | 20:06:00  |	140        	| Female |	40 | Beauty        |		4     |      300       | 105  |    1200    |
| 1819	          | 2022-11-05 | 20:44:00  |	83        	| Female |	35 | Beauty        |		2     |      50        | 13.5 |    100     |
| 943	            | 2022-11-05 | 19:29:00  |	90         	| Female |	57 | Clothing      |		4     |      300       | 318  |    1200    |
| 1896	          | 2022-11-05 | 20:19:00  |	87        	| Female |	30 | Electronics   |		2     |      25        | 25   |    50      |
| 1137	          | 2022-11-05 | 22:34:00  |	104	        |  Male  |	46 | Beauty        |		2     |      500       | 145  |    1000    |
| 856	            | 2022-11-05 | 17:43:00  |	102        	| Male   |	54 | Electronics   |		4     |      30        | 9.3  |    120     |
| 214	            | 2022-11-05 | 16:31:00  |	53        	| Male   |	20 | Beauty        |		2     |      30        | 8.1  |    60      |
| 1265	          | 2022-11-05 | 14:35:00  |	86	        | Male   |	55 | Clothing      |		3     |      300       | 111  |    900     |

- There are 11 sales on 2022-11-05

***

**Q.2 Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 10 in the month of Nov-2022**

````sql
SELECT *
FROM retail_sales
WHERE category = 'Clothing' 
	AND quantity >= 4 	
	AND TO_CHAR(sale_date,'YYYY-MM') = '2022-11'

````
#### Results:
| transactions_id |	sale_date  | sale_time |	customer_id |	gender | age | category      | quantity | price_per_unit | cogs | total_sale |
|-----------------|------------|-----------|--------------|--------|-----|---------------|----------|----------------|------|------------|
| 1484	          | 2022-11-23 | 09:29:00  |	22        	| Female |	19 | Clothing      |		4     |      300       | 147  |    1200    |
| 64	            | 2022-11-15 | 06:34:00  |	7         	| Male   |	49 | Clothing      |		4     |      25        | 8.5  |    100     |
| 284	            | 2022-11-12 | 09:17:00  |	129	        | Male   |	43 | Clothing      |		4     |      50        | 20.5 |    200     |
| 1885	          | 2022-11-09 | 07:32:00  |	148        	| Female |	52 | Clothing      |		4     |      30        | 10.8 |    120     |
| 547	            | 2022-11-14 | 07:36:00  |	3         	| Male   |	63 | Clothing      |		4     |      500       | 250  |    2000    |
| 159	            | 2022-11-10 | 21:30:00  |	42         	| Male   |	26 | Clothing      |		4     |      50        | 23.5 |    200     |
| 699	            | 2022-11-21 | 22:21:00  |	129       	| Female |	37 | Clothing      |		4     |      30        | 16.2 |    120     |
| 1259	          | 2022-11-03 | 17:31:00  |	105	        | Female |	45 | Clothing      |		4     |      50        | 21   |    200     |
| 146	            | 2022-11-10 | 22:01:00  |	74        	| Male   |	38 | Clothing      |		4     |      50        | 49   |    200     |
| 1476	          | 2022-11-11 | 22:27:00  |	130        	| Female |	27 | Clothing      |		4     |      500       | 555  |    2000    |
| 1296	          | 2022-11-26 | 20:42:00  |	45          | Female |	22 | Clothing      |		4     |      300       | 342  |    1200    |
| 1696	          | 2022-11-21 | 17:59:00  |	24        	| Female |	50 | Clothing      |		4     |      50        | 55   |    200     |
| 1497	          | 2022-11-19 | 21:44:00  |	109       	| Male   |	41 | Clothing      |		4     |      30        | 32.4 |    120     |
| 735	            | 2022-11-26 | 21:38:00  |	153         | Female |	64 | Clothing      |		4     |      500       | 515  |    2000    |
| 943	            | 2022-11-05 | 19:29:00  |	90        	| Female |	57 | Clothing      |		4     |      300       | 318  |    1200    |
| 965	            | 2022-11-27 | 21:45:00  |	84        	| Male   |	22 | Clothing      |		4     |      50        | 13   |    200     |
| 1615	          | 2022-11-17 | 13:43:00  |	82        	| Female |	61 | Clothing      |		4     |      25        | 13.5 |    100     |


- When we look at the highest amount of sale, it is only 4 products, so we change the questions into quantity = 4

***

**Q.3 Write a SQL query to calculate the total sales (total_sale) for each category**

````sql
SELECT category,
	SUM(total_sale) net_sale,
	COUNT(*) total_orders
FROM retail_sales
GROUP BY 1;
````
#### Results:
| category    |	net_sale | total_orders |
|-------------|----------|--------------|
| Electronics | 313810   | 684          |	
| Clothing    | 311070   | 701          |	
| Beauty      | 286840   | 612          |	

***

**Q.4 Write a SQL query to find the average age of customers who purchased items from the 'beauty' catecory**

````sql
SELECT ROUND(AVG(age),2) as Beauty_avg_age
FROM retail_sales
WHERE category = 'Beauty';
````
#### Results:
| Beauty_avg_age |
| -------------- |
| 40.2           | 

***

**Q.5 Write a SQL query to find the total number of transactions (transactions_id) made by each gender in each category**

````sql
SELECT gender, category,
	COUNT(transactions_id) Total_transactions
FROM retail_sales
GROUP BY 1,2
ORDER BY 1;
````
#### Results:
| Gender |	Category   | total_transactions |
|--------|-------------|--------------------|
| Female | Beauty      | 330                |	
| Female | Clothing    | 347                |	
| Female | Electronics | 340                |	
| Male   | Beauty      | 282                |	
| Male   | Clothing    | 354                |	
| Male   | Electronics | 344                |	

***

**Q.6 Write a SQL query to calculate the average sale for each month. Find out best selling month in each category**

````sql
SELECT year, 
	month, 
	avg_sale
FROM
(
	SELECT 
		EXTRACT(YEAR FROM sale_date) as year,
		EXTRACT(MONTH FROM sale_date) as month,
		AVG(total_sale) as avg_sale,
		RANK() OVER (PARTITION BY EXTRACT (YEAR FROM sale_date) ORDER BY AVG(total_sale) DESC) as rank
	FROM retail_sales
	GROUP BY 1,2
) as t1
WHERE rank=1;
````
#### Results:
| year | month | avg_sale          |
|------|-------|-------------------|
| 2022 | 7     | 541.3414634146342 |	
| 2023 | 2     | 535.531914893617  |	

***

**Q.7 Write a SQL query to find the top 5 customers based on the highest total sales**

````sql
SELECT customer_id, 
		SUM(total_sale)
FROM retail_sales
GROUP BY 1
ORDER BY 2 DESC
LIMIT 5;
````
#### Results:
| customer_id | sum   | 
|-------------|-------|
| 3           | 38440 | 	
| 1           | 30750 | 	
| 5           | 30405 | 	
| 2           | 25295 | 	
| 4           | 23580 | 	

***

**Q.8 Write a SQL query to find the number of unique customers who purchased items from each category**

````sql
SELECT COUNT(DISTINCT(customer_id)) as cnt_unique_cs, category
FROM retail_sales
GROUP BY 2;
````
#### Results:
| cnt_unique_cs | category    | 
|---------------|-------------|
| 141           | Beauty      | 	
| 149           | Clothing    | 	
| 144           | Electronics | 

***

**Q.9 Write a SQL query to create each shift and number of orders (Example Morning <=12, Afternoon Between 12 & 17, Evening >17)**

````sql
WITH hourly_sale
AS
(
	SELECT
		CASE
			WHEN EXTRACT(HOUR FROM sale_time)<12 THEN 'Morning'
			WHEN EXTRACT(HOUR FROM sale_time)BETWEEN 12 AND 17 THEN 'Afternoon'
			ELSE 'Evening'
		END as shift
	FROM retail_sales
)
SELECT shift,
	COUNT(*) as total_orders
FROM hourly_sale
GROUP BY shift
ORDER BY total_orders DESC;
````
#### Results:
| shift     | total_orders | 
|-----------|--------------|
| Evening   | 1062         | 	
| Morning   | 558          | 	
| Afternoon | 377          | 

***
