## 1.128 FAST_START_MTTR_TARGET

`FAST_START_MTTR_TARGET` enables you to specify the number of seconds the database takes to perform crash recovery of a single instance.

| Property            | Description                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                  |
| Default value       | `0`                                                                                      |
| Modifiable          | `ALTER SYSTEM`                                                                           |
| Modifiable in a PDB | No                                                                                       |
| Range of values     | 0 to 3600 seconds                                                                        |
| Basic               | No                                                                                       |
| Oracle RAC          | Multiple instances can have different values, and you can change the values at run time. |

When specified, `FAST_START_MTTR_TARGET` is overridden by `LOG_CHECKPOINT_INTERVAL`.

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/instance-tuning-using-performance-views.md) for an example of setting the lower bound for this parameter

- [Oracle Database Performance Tuning Guide](../tgdba/instance-tuning-using-performance-views.md) for an example of setting the upper bound for this parameter

- [Oracle Database Performance Tuning Guide](../tgdba/instance-tuning-using-performance-views.md) for an example of selecting a preliminary value for this parameter
