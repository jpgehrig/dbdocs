## 6.510 USER_INDEXES

`USER_INDEXES` describes indexes owned by the current user. To gather statistics for this view, use the `DBMS_STATS` package. This view supports parallel partitioned index scans. Its columns (except for `OWNER`) are the same as those in `ALL_INDEXES`.

**See Also:**

"[ALL_INDEXES](ALL_INDEXES.md)"
