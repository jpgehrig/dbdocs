## 1.380 WORKAREA_SIZE_POLICY

`WORKAREA_SIZE_POLICY` specifies the policy for sizing work areas. This parameter controls the mode in which working areas are tuned.

| Property            | Description                                |
|:--------------------|:-------------------------------------------|
| Parameter type      | String                                     |
| Syntax              | `WORKAREA_SIZE_POLICY = { AUTO | MANUAL }` |
| Default value       | `AUTO`                                     |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`            |
| Modifiable in a PDB | Yes                                        |
| Basic               | No                                         |

### Values

You can specify the following values for `WORKAREA_SIZE_POLICY`:

- `AUTO`

  When `AUTO` is specified, work areas used by memory-intensive operators are sized automatically, based on the PGA memory used by the system, the target PGA memory set in `PGA_AGGREGATE_TARGET`, and the requirement of each individual operator.

- `MANUAL`

  When `MANUAL` is specified, the sizing of work areas is manual and based on the values of the \*`_AREA_SIZE` parameter corresponding to the operation (for example, a sort uses `SORT_AREA_SIZE`). Specifying `MANUAL` may result in sub-optimal performance and poor PGA memory utilization.

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/instance-tuning-using-performance-views.md) for additional information on setting this parameter
