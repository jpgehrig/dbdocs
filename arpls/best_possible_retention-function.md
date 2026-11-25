## 188.1.1 BEST_POSSIBLE_RETENTION Function

This function returns the best possible value for the `undo_retention` parameter that the current undo tablespace can satisfy in order to maximize the usage for the current undo tablespace based on the historical information of a given period.

### Syntax

Viewing the output using the historical information in memory:

    DBMS_UNDO_ADV.BEST_POSSIBLE_RETENTION()
    RETURN NUMBER;

Viewing the output using start time and end time:

    DBMS_UNDO_ADV.BEST_POSSIBLE_RETENTION(
        start_time IN DATE,
        end_time   IN DATE)
    RETURN NUMBER;

Viewing the output using begin and end AWR snapshot ID:

    DBMS_UNDO_ADV.BEST_POSSIBLE_RETENTION(
        begin_snap IN NUMBER,
        end_snap   IN NUMBER)
    RETURN NUMBER;

### Parameters

Table 188-2 BEST_POSSIBLE_RETENTION Function Parameters

| Parameter    | Description                                                                                               |
|:-------------|:----------------------------------------------------------------------------------------------------------|
| `start_time` | Start time of the given period.                                                                           |
| `end_time`   | End time of the given period.                                                                             |
| `begin_snap` | Begin snapshot identifier. It is based on historical information in AWR from the `begin_snap` identifier. |
| `end_snap`   | End snapshot identifier. It is based on historical information in AWR until the `end_snap` identifier.    |
