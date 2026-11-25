To tune query performance you can index JSON fields in several ways, store their values in the In-Memory Column Store (IM column store), or expose them as non-JSON data using materialized views.

- [Overview of Performance Tuning for JSON](overview-of-performance-improvement-for-json.md)
  Which performance-tuning approaches you take depend on the needs of your application. Some use cases and recommended solutions are outlined here.
- [Indexes for JSON Data](indexes-for-json-data.md)
  You can index JSON data as you would any data of the type you use to store it. In addition, you can define a JSON search index, which is useful for both ad hoc structural queries and full-text queries.
- [In-Memory JSON Data](in-memory-json-data.md)
  A column of JSON data can be stored in the In-Memory Column Store (IM column store) to improve query performance.
- [JSON Query Rewrite To Use a Materialized View Over JSON_TABLE](json-query-rewrite-use-materialized-view-json_table.md)
  You can enhance the performance of queries that access particular JSON fields by creating, and indexing, a materialized view over such data that's defined using SQL/JSON function `json_table`.
