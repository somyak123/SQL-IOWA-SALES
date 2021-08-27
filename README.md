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
### Finding the average duratiion a bike has been rented from every station situated in given districts using left outter join
```sql
SELECT BS.station_id,BS.council_district, avg(BTR.duration_minutes) as Avg_duration
FROM `bigquery-public-data.austin_bikeshare.bikeshare_stations` BS
left outer join bigquery-public-data.austin_bikeshare.bikeshare_trips BTR on (BS.station_id=BTR.start_station_id)
group by BS.council_district, BS.station_id
order by BS.council_district, BS.station_id
```
![image](https://user-images.githubusercontent.com/87647923/131139447-cf6abb8b-2391-4414-bc0a-be715330752c.png)
### Average duration of rent for bikes with different power types
```sql
SELECT BS.station_id,BS.power_type, avg(BTR.duration_minutes) as Avg_duration
FROM `bigquery-public-data.austin_bikeshare.bikeshare_trips` BTR
left outer join bigquery-public-data.austin_bikeshare.bikeshare_stations BS  on (BS.station_id=BTR.start_station_id)
where BS.power_type is not null 
group by BS.power_type, BS.station_id
order by BS.power_type, BS.station_id
```
![image](https://user-images.githubusercontent.com/87647923/131145302-59135086-7c96-41de-8c39-b09ab4e87fca.png)


