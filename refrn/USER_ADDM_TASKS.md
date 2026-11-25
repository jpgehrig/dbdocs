## 6.267 USER_ADDM_TASKS

`USER_ADDM_TASKS` displays information about the ADDM tasks owned by the current user.

The view contains one row for each row in the related `USER_ADVISOR_TASKS` view that has `ADVISOR_NAME=ADDM` and `STATUS=COMPLETED`. Its columns (except for `OWNER`) are the same as those in `DBA_ADDM_TASKS`.

**See Also:**

"[DBA_ADDM_TASKS](DBA_ADDM_TASKS.md)"
