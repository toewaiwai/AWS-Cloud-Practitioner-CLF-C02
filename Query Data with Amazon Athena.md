<img width="449" height="201" alt="image" src="https://github.com/user-attachments/assets/706b9313-5f83-4e86-9e17-e6560426219f" />

Task 1: Set up and configure Amazon Athena
<img width="1617" height="670" alt="image" src="https://github.com/user-attachments/assets/322b7d94-f699-42cf-93b0-28c61f6a145e" />
Task 2: Upload sales data to S3
<img width="1918" height="499" alt="image" src="https://github.com/user-attachments/assets/fb607f62-536e-4772-9682-8689457b1018" />
Task 3: Create and configure an AWS Glue crawler
<img width="1918" height="690" alt="image" src="https://github.com/user-attachments/assets/370de2fe-a9e5-4738-a7b1-c28de395edbb" />
<img width="1918" height="817" alt="image" src="https://github.com/user-attachments/assets/d34d3770-2616-4abf-a8ab-2fcb4f8c7028" />
<img width="1918" height="700" alt="image" src="https://github.com/user-attachments/assets/ab4bce92-d7d7-41a8-aca3-73b2d2a37f70" />
<img width="1918" height="777" alt="image" src="https://github.com/user-attachments/assets/4dd4551f-4141-41fa-b692-a66616d06425" />
<img width="1918" height="726" alt="image" src="https://github.com/user-attachments/assets/d1d28a36-e67b-418c-81e4-64f7a1b1b6ab" />
Task 4: Create database tables using Athena and Glue Crawler
<img width="1915" height="808" alt="image" src="https://github.com/user-attachments/assets/fec543fe-179c-4180-b15d-6adc210b2c22" />
```cmd
CREATE EXTERNAL TABLE customers (
    card_id bigint,
    customer_id bigint,
    lastname string,
    firstname string,
    email string,
    address string,
    birthday string,
    country string
)
ROW FORMAT SERDE 
  'org.apache.hadoop.hive.serde2.lazy.LazySimpleSerDe'
WITH SERDEPROPERTIES (
  'field.delim'=',',
  'serialization.format'=','
)
STORED AS INPUTFORMAT 
  'org.apache.hadoop.mapred.TextInputFormat' 
OUTPUTFORMAT 
  'org.apache.hadoop.hive.ql.io.HiveIgnoreKeyTextOutputFormat'
LOCATION
  's3://data-bucket-642804619/customers/'
TBLPROPERTIES (
  'has_encrypted_data'='false',
  'skip.header.line.count'='1'
);
```
<img width="1896" height="784" alt="image" src="https://github.com/user-attachments/assets/70d8fcb6-4a02-416e-9947-4ab2f0d4cbcd" />
<img width="1915" height="822" alt="image" src="https://github.com/user-attachments/assets/6e2200e1-87ef-4942-96e0-57c5e3fbc8d3" />
```cmd
CREATE EXTERNAL TABLE sales (
    card_id bigint,
    customer_id bigint,
    price decimal(10,2),
    product_id string,
    timestamp timestamp
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
LOCATION 's3://data-bucket-642804619/sales/'
TBLPROPERTIES (
    'skip.header.line.count'='1'
);
```
<img width="1915" height="820" alt="image" src="https://github.com/user-attachments/assets/60c75411-9862-4549-a93e-d1c40028b2ce" />
<img width="1912" height="823" alt="image" src="https://github.com/user-attachments/assets/53110303-0974-425b-b019-86b3e2df341d" />
Use AWS Glue crawler to automatically create table schemas
<img width="1893" height="813" alt="image" src="https://github.com/user-attachments/assets/9b84dde5-3a55-45aa-87db-1e2766c4fffc" />
<img width="1918" height="813" alt="image" src="https://github.com/user-attachments/assets/e251815b-9a5b-432b-8943-c8b07d04a010" />
```cmd
DESCRIBE customers
```
<img width="1897" height="820" alt="image" src="https://github.com/user-attachments/assets/59c155f1-d490-4f08-a7d5-35e21ef127ce" />
<img width="1893" height="775" alt="image" src="https://github.com/user-attachments/assets/efa01038-88f9-4ced-b1ad-88f52bc1ac0a" />
Task 5: Perform basic aggregations and filtering
<img width="1896" height="808" alt="image" src="https://github.com/user-attachments/assets/d8e6ae6a-7399-4262-ba50-77123c0e0148" />
```cmd
SELECT 
    c.country,
    COUNT(DISTINCT c.customer_id) as total_customers,
    COUNT(*) as total_transactions,
    SUM(cast(s.price as decimal(10,2))) as total_sales
FROM customers c
JOIN sales s ON c.customer_id = s.customer_id
GROUP BY c.country
ORDER BY total_sales DESC;
```
<img width="1890" height="807" alt="image" src="https://github.com/user-attachments/assets/0c082a1f-b1d3-4e0f-9288-5ef66f2bae00" />
Join multiple tables
```cmd
SELECT 
    c.country,
    c.firstname,
    c.lastname,
    s.product_id,
    cast(s.price as decimal(10,2)) as price,
    s.timestamp
FROM customers c
JOIN sales s ON c.customer_id = s.customer_id
ORDER BY cast(s.price as decimal(10,2)) DESC
LIMIT 10;
```
<img width="1894" height="817" alt="image" src="https://github.com/user-attachments/assets/8c2861d9-9606-459c-8628-8ed5477d2fae" />
```cmd
SELECT 
    c.firstname,
    c.lastname,
    c.country,
    COUNT(*) as purchase_count,
    SUM(cast(s.price as decimal(10,2))) as total_spent
FROM customers c
JOIN sales s ON c.customer_id = s.customer_id
GROUP BY c.firstname, c.lastname, c.country
HAVING COUNT(*) > 1
ORDER BY total_spent DESC
LIMIT 10;
```
<img width="1894" height="819" alt="image" src="https://github.com/user-attachments/assets/0879f8a9-3ec4-4b54-8e66-e1b07f1a373c" />
Task 6: Explore query editor Features
```cmd
EXPLAIN
SELECT 
    c.country,
    COUNT(DISTINCT c.customer_id) as total_customers,
    SUM(cast(s.price as decimal(10,2))) as total_sales
FROM customers c
JOIN sales s ON c.customer_id = s.customer_id
GROUP BY c.country
ORDER BY total_sales DESC;
```
<img width="1903" height="810" alt="image" src="https://github.com/user-attachments/assets/cdb18c92-ee21-44d5-a51b-00cacbcb927d" />
Review logical plan explanation
```cmd
SELECT 
    c.firstname,
    c.lastname,
    c.country,
    COUNT(*) as purchase_count,
    SUM(cast(s.price as decimal(10,2))) as total_spent
FROM customers c
JOIN sales s ON c.customer_id = s.customer_id
GROUP BY c.firstname, c.lastname, c.country
HAVING COUNT(*) > 1
ORDER BY total_spent DESC;
```
<img width="1896" height="814" alt="image" src="https://github.com/user-attachments/assets/bef2ff61-bb9a-49e1-a21f-39d2ae60428a" />
Save queries for future use
<img width="1815" height="741" alt="image" src="https://github.com/user-attachments/assets/3bb1a87f-3c3a-4732-b4ef-d168b078744c" />
