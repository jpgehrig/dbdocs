## 1.198 MAX_DISPATCHERS

`MAX_DISPATCHERS` specifies the maximum number of dispatcher processes allowed to be running simultaneously.

| Property            | Description                                                                                                                                                                                                                    |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                                                                                                                                                        |
| Default value       | There is no default value.                                                                                                                                                                                                     |
| Modifiable          | `ALTER SYSTEM`                                                                                                                                                                                                                 |
| Modifiable in a PDB | No                                                                                                                                                                                                                             |
| Range of values     | If `MAX_DISPATCHERS` is specified, then it should be greater than or equal to the number of dispatchers specified by the `DISPATCHERS` parameter and less than the number of processes specified by the `PROCESSES` parameter. |
| Basic               | No                                                                                                                                                                                                                             |

This parameter can be overridden by the `DISPATCHERS` parameter and is maintained for backward compatibility with older releases.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-processes.md) for more information about this parameter

- Your operating system-specific Oracle documentation for the default value and range of values
