## 6.566 USER_MVREF_RUN_STATS

`USER_MVREF_RUN_STATS` has information about each refresh run for the materialized views accessible for the current database user, with each run being identified by the `REFRESH_ID`. The information includes timing statistics related to the run and the parameters specified in that run.

Its columns (except for `RUN_OWNER`) are the same as those in `DBA_MVREF_RUN_STATS`.

**See Also:**

"[DBA_MVREF_RUN_STATS](DBA_MVREF_RUN_STATS.md)"
