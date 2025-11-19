
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

## Joins
- Natural join
- Inner join
- Self join
- Left join
- Right join
- Full outer join
- Cross join

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