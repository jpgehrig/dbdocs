## 12.7 Updating Large Tables in Parallel

The `DBMS_PARALLEL_EXECUTE` package lets you incrementally update the data in a large table in parallel, in two high-level steps:

1.  Group sets of rows in the table into smaller chunks.
2.  Apply the desired `UPDATE` statement to the chunks in parallel, committing each time you have finished processing a chunk.

This technique is recommended whenever you are updating a lot of data. Its advantages are:

- You lock only one set of rows at a time, for a relatively short time, instead of locking the entire table.

- You do not lose work that has been done if something fails before the entire operation finishes.

- You reduce rollback space consumption.

- You improve performance.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PARALLEL_EXECUTE.md) for more information about the `DBMS_PARALLEL_EXECUTE` package
