## 6.697 USER_TAB_COLUMNS

`USER_TAB_COLUMNS` describes the columns of the tables, views, and clusters owned by the current user.

Its columns (except for `OWNER`) are the same as those in `ALL_TAB_COLUMNS`.

To gather statistics for this view, use the `DBMS_STATS` package.

This view filters out system-generated hidden columns. The `USER_TAB_COLS` view does not filter out system-generated hidden columns.

**See Also:**

- "[ALL_TAB_COLUMNS](ALL_TAB_COLUMNS.md)"

- "[USER_TAB_COLS](USER_TAB_COLS.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for more information about the `DBMS_STATS` package
