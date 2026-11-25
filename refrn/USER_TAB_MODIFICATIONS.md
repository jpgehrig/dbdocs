## 6.702 USER_TAB_MODIFICATIONS

`USER_TAB_MODIFICATIONS` describes modifications to all tables owned by the current user that have been modified since the last time statistics were gathered on the tables. Its columns are the same as those in `ALL_TAB_MODIFICATIONS`.

**Note:**

For performance reasons, Oracle Database does not populate this view immediately when the actual modifications occur.

**See Also:**

"[ALL_TAB_MODIFICATIONS](ALL_TAB_MODIFICATIONS.md)"
