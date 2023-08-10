# FINAL ASSIGNMENT-1202
Viewing both fact and dimension table
```sql
select * from summer_product.product_list;
select * from summer_product.dimension;
```

Altering column name- fact and dimension table 
```sql
 ALTER TABLE summer_product.dimension
RENAME COLUMN ï»¿product_id TO product_id;

 ALTER TABLE summer_product.dimension
RENAME COLUMN ï»¿product_id TO product_id;
```

Displaying the altered columns
```sql
select product_id from summer_product.product_list;
select product_id from summer_product.dimension;
```

Creating a view that joins the columns from both the fact and dimensions tables with 'product_id' column as primary key
```sql
CREATE VIEW combined_table1 AS
SELECT fact.product_id, fact.price, fact.units_sold,dimension.countries_shipped_to, dimension.product_color
FROM summer_product.product_list fact
INNER JOIN summer_product.dimension dimension ON fact.product_id = dimension.product_id;
```
Viewing the combined table
```sql
SELECT * FROM combined_table1;
```

Displaying the average units sold for each product color 
```sql
SELECT product_color, AVG(units_sold) AS average_units_sold
FROM combined_table1
GROUP BY product_color;
```
