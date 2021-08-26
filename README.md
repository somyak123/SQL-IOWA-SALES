# SQL-IOWA-SALES
## Total Sales By cities
```sql
SELECT sum(ILS.sale_dollars) as Total_sales,ILS.city FROM `bigquery-public-data.iowa_liquor_sales.sales` ILS
group by ILS.city
order by sum(ILS.sale_dollars) desc 
```
![image](https://user-images.githubusercontent.com/87647923/130980572-bfe6d2d8-0d23-415a-9f82-5a9cc20af63f.png)
## Which liquor brand in a city has maximum sales
```sql
SELECT max(ILS.sale_dollars) as Max_sales,ILS.city,ILS.category_name FROM `bigquery-public-data.iowa_liquor_sales.sales` ILS
group by ILS.city,ILS.category_name
order by ILS.city desc , max(ILS.sale_dollars) desc 
```
![image](https://user-images.githubusercontent.com/87647923/130990471-3eaa0c25-1aa4-4b8f-b908-95312ff661d1.png)
## What is the minimum bottles cost for each category in all countys
```sql
SELECT min(ILS.state_bottle_cost) as Min_cost,ILS.county,ILS.category_name FROM `bigquery-public-data.iowa_liquor_sales.sales` ILS
group by ILS.category_name,ILS.county
order by ILS.category_name desc , max(ILS.sale_dollars) desc 
```
![image](https://user-images.githubusercontent.com/87647923/130992238-dc9d6ac4-6d9a-4dc7-96d4-aca357d39ede.png)
