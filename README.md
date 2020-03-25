**Setup**

*Download SQLite*
1. [Download Sqlite](https://www.sqlite.org/download.html)

*Add Path*

2. System Properties > Environment Variables > System Variables > Path > C:\sqlite;

---
**Sqlite Commands**

```
sqlite3 <database>
```

```
.schema <table>
```

* Return Schema in SQL 
```
PRAGMA table_info(<table>);
```

* get a high level query plan 

```
EXPLAIN QUERY PLAN SELECT * FROM <table>;
```

---

**Data Dictionary**

|column|description|
|---|---|
|name|name of the country.|
|area|the total land and sea area of the country.|
|population|the population of the country.|
|birth_rate| the birth rate of the country.|
|created_at|the date the record was created.|
|updated_at|the date the record was updated.|

---

**SQL Indexing**

 Before SQL returning the results to you. First, it tokenizes and parses your query to look for any syntax errors. If there are any syntax errors, the query execution process halts and the error message is returned to you. If the parser was able to successfully parse the query, then SQLite moves on to the query planning and optimization phase.

 When working with a database that's stored on disk as a file, it's crucial to minimize the amount of disk reads necessary to avoid long running times. The query optimizer generates cost estimates for the various ways to access the underlying data, factoring in the schema of the tables and the operations the query requires. The heuristics and algorithms that are involved in query optimization is complex

 The optimizer quickly assesses the various ways to access the data and generates a best guess for the fastest query plan. This high level query plan is then converted into highly efficient, lower-level C code to interact with the database file on disk.

 ```
CREATE INDEX index_name ON table_name(column_name);
 ```

 ```
 CREATE INDEX IF NOT EXISTS area_idx ON facts(area);

SELECT * FROM facts WHERE area = 10000;
SELECT * FROM facts WHERE area > 10000;
SELECT * FROM facts WHERE area < 10000;
 ```

 > create indexes for speeding up queries that filter on multiple columns.