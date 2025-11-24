
Data page size -- 8KB

The tables are logically connected pages that hold row data.

The visual order of table is maintained through
- IAM (Index Allocation Map) -- tells the pages that belong to the table
- PFS (Page Free Space) -- tells which page has free space (( when a row is deleted in a page then there is a free space))
- B-tree navigation  -- Connects pages for tables with clustered indexes.
- Page pointers (nextpagepointer, prevpagepointer)

## Views
- It is a virtual table where the corresponding query is saved, and dynamically executed when the view is called upon.
- The data itself is not stored.
- It produces up-to-date data.
- It can be queried just like any normal table.


## Materialized view
- Similar to view but stores the data corresponding to the view, so it does not need to run each time
- It will be updated when explicitly refreshed.

## Joins
- Natural join
- Inner join
- Self join
- Left join
- Right join
- Full outer join
- Cross join


## Aggregate functions

- SUM
- AVG
- MIN
- MAX
- COUNT

## Common Table Expression(CTE)
- Creates a temporary view of a table specific to a query
- It helps avoid the complex readability in subquery
- There is two type of queries present in this
	- anchor query (first query )
	- Recursive query ( all the queries that follow after union or union all)
- The recursive queries are repeated until it does not return any rows to the table 
- A recursive CTE accepts wither ==UNION== or ==UNION ALL== 
- Using cte reference directly in recursive query can lead to infinite loop;
- **UNION** 
	- Allows only the unique value to exits all the duplicate values are removed
- **UNOIN ALL**
	- Allows all the values without any restriction ( duplicates are allowed).




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




## Truncate working
- It takes O(1) 
- The query straight away marks the pages as empty logically and add the pages to free space
- Does not delete the values physically
- The data will be physically present until a record suitable for the page is inserted and overwrites the existing old data.


## Delete 
- Similar to truncate it flags the particular row as deleted and added to page free space.
- Can be overwritten when a suitable record is inserted.


## Drop 
- Similar to truncate but deallocates all the pages
- Physically remove the structure of the table from db
- Remove the table from all the 



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
- Use limit or pagination 
- Avoid using wildcards at the start (for searching)
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


