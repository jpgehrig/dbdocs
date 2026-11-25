## 6.696 USER_TAB_COLS

`USER_TAB_COLS` describes the columns of the tables, views, and clusters owned by the current user.

Its columns (except for `OWNER`) are the same as those in `ALL_TAB_COLS`.

To gather statistics for this view, use the `DBMS_STATS` package.

This view differs from `USER_TAB_COLUMNS` in that system-generated hidden columns are not filtered out.

**See Also:**

- "[ALL_TAB_COLS](ALL_TAB_COLS.md)"

- "[USER_TAB_COLUMNS](USER_TAB_COLUMNS.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for more information about the `DBMS_STATS` package
