created:: 2024-04-14 09:59
status:: #zettel/fleeting
tags:: #database #performance 
### Partitioning
**Partition Tables:** Partitioning involves dividing large tables into smaller, more manageable pieces. This can significantly improve query performance by allowing the database engine to work on smaller subsets of data, leading to faster query execution.

```sql
CREATE TABLE sales (  
	sale_id INT PRIMARY KEY,  
	sale_date DATE,  
	amount DECIMAL(10, 2)  
) PARTITION BY RANGE (YEAR(sale_date)) (  
	PARTITION p0 VALUES LESS THAN (1990),  
	PARTITION p1 VALUES LESS THAN (2000),  
	PARTITION p2 VALUES LESS THAN (2010),  
	PARTITION p3 VALUES LESS THAN (2020),  
	PARTITION p4 VALUES LESS THAN (MAXVALUE)  
);
```

**Partition Pruning:** Ensure that the query planner prunes unnecessary partitions during query execution. This prevents scanning the entire dataset and improves performance.

```sql
SELECT * FROM sales WHERE sale_date >= '2022-01-01' AND sale_date < '2023-01-01';
```

### Caching
Implement caching that store query results frequently requested can be improve the performance. We can use a NOSQL database to do it, that as: *redis or memcached*

### Indexing
We can create index in a column for improve a query performance. It a great way to improve a query without hard work.

```sql
CREATE INDEX idx_username ON users(username);
```

### Database Design
Make efficient schema table is a great way to has more performance in your database. Always use column with a maximum value is a good practice.

```sql
CREATE TABLE products (  
	product_id INT PRIMARY KEY,  
	product_name VARCHAR(255),  
	price DECIMAL(10, 2)
);
```