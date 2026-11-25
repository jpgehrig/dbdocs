You can optimize the performance of distributed queries.

You can improve the performance of distributed queries by using the following strategies:

- Choose the best SQL statement.

  In many cases, there are several SQL statements that can achieve the same result. If all tables are on the same database, then the difference in performance between these SQL statements may be minimal. If the tables are located on different databases, then the difference in performance may be more significant. Also, note that the best SQL statement may change from one release to the next.

- Use the query optimizer.

  The query optimizer uses indexes on remote tables, considers more execution plans than the rule-based optimizer, and generally gives better results. With the query optimizer, performance of distributed queries is generally satisfactory. Only on rare occasions is it necessary to change SQL statements, create views, or use procedural code.

- Use views.

  In some situations, views can be used to improve performance of distributed queries. For example:

  - Joining several remote tables on the remote database

  - Sending a different table through the network

  - Retrieve data from the remote table in parallel

- Use procedural code.

  On rare occasions, it can be more efficient to replace a distributed query by procedural code, such as a PL/SQL procedure or a precompiler program.

**Parent topic:** [Performance Recommendations](performance-recommendations.md)
