## 6.502 USER_IM_EXPRESSIONS

`USER_IM_EXPRESSIONS` provides information about the list of expressions (SYS_IME virtual columns) that are currently enabled for in-memory storage in schemas owned by the current user. Its columns (except for `OWNER`) are the same as those in `DBA_IM_EXPRESSIONS`.

Typically, you can query this view after invoking the `DBMS_INMEMORY_ADMIN.IME_CAPTURE_EXPRESSIONS` PL/SQL procedure to see the list of hot expressions added to tables owned by you across the database.

Based on this view, you can:

- Populate expressions on a particular table immediately

- Drop certain expressions that are marked for in-memory but not desired by you

**See Also:**

"[DBA_IM_EXPRESSIONS](DBA_IM_EXPRESSIONS.md)"
