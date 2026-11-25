## 6.427 USER_DB_LINKS

`USER_DB_LINKS` describes the database links owned by the current user. Its columns are the same as those in `ALL_DB_LINKS` except that it does not have the `OWNER` column.

It also displays an additional column, `PASSWORD`, which is no longer used and for which nothing is returned. The `PASSWORD` column is maintained for backward compatibility only.

**See Also:**

"[ALL_DB_LINKS](ALL_DB_LINKS.md)"
