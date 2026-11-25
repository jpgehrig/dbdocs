## 6.498 USER_ILMOBJECTS

`USER_ILMOBJECTS` displays all the Automatic Data Optimization policies and objects for a user.

Many objects inherit policies via their parent objects or because they were created in a particular tablespace. This view provides a mapping between the policies and objects and indicates whether a policy is inherited by an object or is directly specified on it. Its columns are the same as those in `DBA_ILMOBJECTS`.

**Note:**

Automatic Data Optimization is supported in Oracle Database 12c Release 2 multitenant environments.

**See Also:**

"[DBA_ILMOBJECTS](DBA_ILMOBJECTS.md)"
