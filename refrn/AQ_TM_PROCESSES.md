## 1.16 AQ_TM_PROCESSES

`AQ_TM_PROCESSES` controls time monitoring on queue messages and controls processing of messages with delay and expiration properties specified.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Integer        |
| Default value       | `1`            |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | Yes            |
| Range of values     | `0` to `40`    |
| Basic               | No             |

You do not need to specify a value for this parameter because Oracle Database automatically determines the number of processes and autotunes them, as necessary. Therefore, Oracle highly recommends that you leave the `AQ_TM_PROCESSES` parameter unspecified and let the system autotune.

The default value for `AQ_TM_PROCESSES` is used if the client does not explicitly set a value for the parameter in the `init.ora` file or using the `ALTER` `SYSTEM` statement.

**Note:**

If you want to disable the Queue Monitor Coordinator, then you must set `AQ_TM_PROCESSES` to 0 in your parameter file. Oracle strongly recommends that you do NOT set `AQ_TM_PROCESSES` to 0.

**See Also:**

[Oracle Database Advanced Queuing User's Guide](../adque/aq-basic-components.md) for more information about this parameter
