## 6.531 USER_JOINGROUPS

`USER_JOINGROUPS` describes join groups belonging to the user. A join group is a user-created object that consists of two or more columns that can be meaningfully joined. The maximum number of columns that can be included in a join group is 255. The `USER_JOINGROUPS` columns (except for `JOINGROUP_OWNER`) are the same as those in `DBA_JOINGROUPS`.

In certain queries, join groups enable the database to eliminate the performance overhead of decompressing and hashing column values. Join groups require an In-Memory column store (IM column store).

**See Also:**

- "[DBA_JOINGROUPS](DBA_JOINGROUPS.md)"

- [Oracle Database In-Memory Guide](../inmem/optimizing-queries-with-join-groups.md) for an introduction to join groups

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-INMEMORY-JOIN-GROUP.md) for information about creating a join group using the `CREATE INMEMORY JOIN GROUP` statement
