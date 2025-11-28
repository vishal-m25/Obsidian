
Data page size -- 8KB

The tables are logically connected pages that hold row data.

The visual order of table is maintained through
- IAM (Index Allocation Map) -- tells the pages that belong to the table
- PFS (Page Free Space) -- tells which page has free space (( when a row is deleted in a page then there is a free space))
- B-tree navigation  -- Connects pages for tables with clustered indexes.
- Page pointers (nextpagepointer, prevpagepointer)

## Data Types
- Numbers
	- int
	- bigint
	- smallint
	- numeric
	- numeric(precisionm, scale)
	- real
	- double
	- decimal
	- float
	- serial
	- bigserial
- Monetary (money)
	- money
- Characterss
	- char
	- varchar
	- text
- Binary
	- bytea
- Date/time
	- date
	- time
	- timestamp
	- interval
- Boolean
- Enum


## Select 

### keywords & modifiers:
- `DISTINCT`
- `DISTINCT ON (columns)`
- `*`
- `AS`
- Functions:
    - `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
    - Window:
        - `OVER (PARTITION BY ... ORDER BY ... ROWS BETWEEN ...)`
- Filtering:
    - `IN`
    - `NOT IN`
    - `EXISTS`
    - `NOT EXISTS`
    - `BETWEEN`
    - `LIKE`, `ILIKE` (ignore case)
    - `IS NULL`, `IS NOT NULL`
    - `CASE WHEN THEN ELSE END`
- Joins:
- Set operations
    - `UNION`, `UNION ALL`
    - `INTERSECT`
    - `EXCEPT`
- Sorting
    - `NULLS FIRST | LAST`



## Joins
- Natural join
- Inner join
- Self join
- Left join
- Right join
- Full outer join
- Cross join
```sql
select * from employees,user; --creates a cross join of the two tables, can also mention columns to join on
```

## Keywords

### Returning keyword
The `RETURNING` clause allows you to return the modified rows **as part of the DML command itself**, eliminating the need for a separate `SELECT` query. This offers two main benefits:

1. **Atomicity and Consistency:** You get the values generated during the single, atomic operation, avoiding potential race conditions that could occur if you performed the DML and a separate `SELECT`.
2. **Efficiency:** It reduces database round trips, improving application performance.

```sql
insert into users values (7,'asdf') returning id,name;
insert into users values (2,'bob') returning new;
insert into users values (3,'carry') returning old;
insert into users values (6,'anny') returning *;
```

### LATERAL keyword
- Used after join, before subquery to allow the access to columns from outside to inside of the subquery.
- Used after a join and followed by a subquery

### comment
- To give a description for a table
```sql
Comment on table_name is 'this is a user table'
```




## Aggregate functions

- SUM
- AVG
- MIN
- MAX
- COUNT



### Auto increments
- While inserting values need not mention the column or give ==**`DEFAULT`**== as its value.
- Serial 
	- utilizes the previous record id to increment
	- can directly give an id while inserting a row
- Identical 
	- utilizes the previous record value to increment
	- does not allow user to send id while inserting into table
- Sequence
	- a variable is created for the table 
	- uses and updates the variable to calculate the value
```sql
create table table_name( id int serial primary key, name char);

create table table_name(id int generated always as identity primary key);
```

## UPSERT 
- It is a mechanism used to update values, if it does not exist the record is inserted.
- It can be used like try-catch block
```sql
INSERT INTO products (product_id, name, price)
VALUES (101, 'Laptop Pro', 1200.00)
ON CONFLICT (product_id)
DO UPDATE SET
    name = EXCLUDED.name,
    price = EXCLUDED.price;
```





## VIEWS
### Views
- It is a virtual table where the corresponding query is saved, and dynamically executed when the view is called upon.
- The data/table itself is not stored.
- It produces up-to-date data.
- It can be queried just like any normal table.


### Materialized view
- Similar to view but stores the data corresponding to the view, so it does not need to run each time
- It will be updated when explicitly refreshed.


## Common Table Expression(CTE)
- It is preferable when the level is unknown, in the same or different table and if the dependency keeps growing hierarchy then this is more suitable.
- Creates a temporary view of a table specific to a query.
- It helps avoid the complex readability in subquery.
- There is two type of queries present in CTE.
	- anchor query (first query )
	- Recursive query ( all the queries that follow after union or union all)
- The recursive queries are repeated until it does not return any rows to the table 
- A recursive CTE accepts either ==UNION== or ==UNION ALL== 
- Using CTE reference directly in recursive query can lead to infinite loop;
- **UNION** 
	- Allows only the unique value to exits all the duplicate values are removed
- **UNOIN ALL**
	- Allows all the values without any restriction ( duplicates are allowed).
	- it is mostly preferred in CTE due to less odds of having duplicate values in hierarchy based table.

```sql
WITH RECURSIVE subordinates AS (
SELECT employee_id, manager_id, full_name, 0 as level
FROM employees
WHERE manager_id IS NULL
UNION ALL
SELECT e.employee_id, e.manager_id, e.full_name, level+1
FROM employees e
INNER JOIN subordinates s ON s.employee_id = e.manager_id
)  
SELECT * FROM subordinates;
```

## Indexing

### Unique index
- Starts with ==**`create unique index`**== 
- Effective on columns that only have unique values






## Query execution order
- Queries are executed in logical order (not in the order they are written), determining how data is retrieved, filtered, grouped, etc.
- It determines how data flows from tables to the final result.

- SQL begins processing a query from ==**`FROM`**== clause
	- identifies the tables involved
	- the data from the table is fetched , subqueries are evaluated in this step.
	- then the join is applied
	- Data preparation :: filters unnecessary data and creates a smaller intermediate dataset.
	- Temporary tables may be create internally to process complex operations.
- ==**`WHERE`**==
	- Filters the rows based in condition provided.
- ==**`GROUP BY`**==
	- the data is grouped after the filtering with where
	- in postgres the columns included in select should either be present in group by or with aggregate function.( to have deterministic solution)
- ==**`HAVING`**==
	- conditions to apply on aggregated results
- ==**`SELECT`**==
- ==**`DISTINCT`**== 
	- removes the duplicate rows
- ==**`ORDER BY`**==
	- sorts
- ==**`LIMIT / OFFSET`**==


## SQL constraints
- NOT NULL
- UNIQUE
- PRIMARY KEY 
- FOREIGN KEY
- CHECK ( )
- DEFAULT
- INDEX  \\  ( CREATE INDEX ind_name ON table(col_x,col_y) )

## Orphan child condition

It occurs when there are two tables parent and child which has reference in the parent, so when an entry/row deleted in parent and simultaneously not in child, then the child now refer to parent row that no longer exists.

This occurs due to;
- Not cascading on creation.
- Soft deleting parent before the child
- Not updating the change in reference from parent to child

## CASCADE delete
- Used in foreign key constraint.
- It help in avoiding orphan child problem
- When the records in the reference table is deleted corresponding records in the referring table as well be deleted.

```sql
create table parent(id int primary key,name varchar(20)) on delete cascade;
```

## Truncate 
- It takes O(1) 
- The query straight away marks the pages as empty logically and add the pages to free space
- Does not delete the values physically
- The data will be physically present until a record suitable for the page is inserted and overwrites the existing old data.


## Delete 
- Similar to truncate it flags the particular row as deleted and added to page free space.
- Can be overwritten when a suitable record is inserted.


## Partition by
- Creates separate table for each distinct value or range of date or time or value in the partitioned column.
- We need to manually create tables and instruct which table should take in which values.
- The cannot be two individual partition in a same table (on two different columns);

```sql
select id,name,department, max(salary) over(partition by (department)) as max from employees order by max desc; -- for select query



```

## Drop 
- Similar to truncate but deallocates all the pages
- Physically remove the structure of the table from DB

## INHERITS
- On using this keyword in a table creation it states that it is child if a table.
- So when a select query is executed on a parent table, unless the ==**`only`**== keyword is used after from, the query will search the entire hierarchy.


## Transactions
- Used to group a set of queries as one atomic query.
- When you need to execute a set of queries sequentially without other queries interrupting then write it inside a Begin.. End .
- Procedures usually store transactions.
- Exception can be used to handle error/exception and handle it internally or rollback the transaction.
```sql
CREATE PROCEDURE safe_insert(p_id INT)
LANGUAGE plpgsql
AS $$
BEGIN
    INSERT INTO table VALUES (p_id);
EXCEPTION 
    WHEN unique_violation THEN
        ROLLBACK --either cancel the entire transaction or handle it internally
END;
$$;
```



## query execution time calculation

- Server side
```sql
EXPLAIN ANALYZE SELECT * FROM my_table WHERE condition;
```
- Shows execution plan , step-by-step execution time



- Client side
```sql
\timing 
-- Now execute your query
SELECT * FROM my_table WHERE condition;
```
- Starts a time on the client side and stops it when the result is returned



## Ways to optimize queries
- Create proper indexes.
- Avoid ==**`select *`**==
- Use ==**`EXISTS`**== instead of ==**`IN`**==
- Avoid functions on indexed columns
- Filter early (push restrictive conditions in subqueries)
- Use limit or pagination(limit + offset)
- Avoid using wildcards at the start (when searching)
- Use joins instead of subquery
- Remove unnecessary order by
- Use proper data types
- Partition large tables
- Denormalize when needed
- Use query caching / materialized views
- Use UNION over OR
- Use temporary tables for multi-joins
- Limit text search columns


## Pagination 
- ### LIMIT N
	- prints the first N records retrieved by the query.
- ### OFFSET N
	- skips the first N records of the retrieved result and prints rest

By combining both, the concept of pagination can be implemented.





## Normalization

### 1NF
- There should not be more than one value in a cell


### 2NF
- There can be composite key, but in a table there should not be a column that partially depend on composite key (it should be broken into different tables).
- There can either be columns dependent only on primary key , or composite key, both are not allowed in the same table.

### 3NF
- Any non prime key should not depend on another non-prime key. The depending key can be a prime key from a candidate key.


### BCNF
- It is also knows as strict 3NF.
- All determinants (left side in a relational representation) should be a super key.
- Removes The depending key the can be a prime key from a candidate key.


### 4NF
- Multi valued dependencies are not allowed in here, there has to be separate table to handle multi value dependencies.


## Date
- Use ==**`::date`**==  after the date when you need to apply interval for date
```sql
select * from sample where join_data>= '4-4-2000'::date + interval '10 year';
```



## RULE
- In can be used on both table and view.
- It is only to guide errors from occurring.
- Can be used on view, when someone try to insert into view, we can create a rule that if it is tried insert into the real table.
```sql
CREATE RULE v_upd AS
ON UPDATE TO view_emp
DO INSTEAD
UPDATE employees
SET name = NEW.name
WHERE id = OLD.id;
```

