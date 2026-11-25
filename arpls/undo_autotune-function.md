## 188.1.7 UNDO_AUTOTUNE Function

This function finds out whether the auto-tuning of undo retention is enabled for the current undo tablespace.

### Syntax

    DBMS_UNDO_ADV.UNDO_AUTOTUNE(
         chk OUT BOOLEAN)
    RETURN BOOLEAN;

### Parameters

Table 188-8 UNDO_AUTOTUNE Function Parameters

| Parameter | Description                                                            |
|:----------|:-----------------------------------------------------------------------|
| `chk`     | `TRUE` if auto-tuning of undo retention is enabled, `FALSE` otherwise. |
