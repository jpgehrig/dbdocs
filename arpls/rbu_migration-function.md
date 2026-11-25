## 188.1.2 RBU_MIGRATION Function

This function estimates the undo tablespace needed for migration from manual to automatic undo management.

### Syntax

If you are currently using manual undo management (rollback segments) to manage undo space, then Oracle recommends migrating to automatic undo management. You must first create an undo tablespace, before opening a newly upgraded database. The required size of undo tablespace depends on the system workload and Flashback requirements.

**Note:**

The `RBU_MIGRATION` function should be called only when `undo_management` = manual.

Viewing the output using the historical information in memory:

    DBMS_UNDO_ADV.RBU_MIGRATION()
    RETURN NUMBER;

Viewing the output using the Start Time and End Time:

    DBMS_UNDO_ADV.RBU_MIGRATION(
        START_TIME IN DATE,
        END_TIME   IN DATE)
    RETURN NUMBER;

### Parameters

Table 188-3 RBU_MIGRATION Function Parameters

| Parameter    | Description                     |
|:-------------|:--------------------------------|
| `START_TIME` | Start time of the given period. |
| `END_TIME`   | End time of the given period.   |
