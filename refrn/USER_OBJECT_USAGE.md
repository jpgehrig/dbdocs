## 6.578 USER_OBJECT_USAGE

`USER_OBJECT_USAGE` displays statistics about index usage gathered from the database for the indexes owned by the current user.

You can use this view to monitor index usage. All indexes owned by the current user that have been used at least once can be monitored and displayed in this view. Its columns (except for `OWNER`) are the same as those in `DBA_OBJECT_USAGE`.

**See Also:**

"[DBA_OBJECT_USAGE](DBA_OBJECT_USAGE.md)"
