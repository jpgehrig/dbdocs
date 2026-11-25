## 1.253 OPTIMIZER_INDEX_COST_ADJ

`OPTIMIZER_INDEX_COST_ADJ` lets you tune optimizer behavior for access path selection to be more or less index friendly—that is, to make the optimizer more or less prone to selecting an index access path over a full table scan.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Integer                         |
| Default value       | `100`                           |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | 1 to 10000                      |
| Basic               | No                              |

The default for this parameter is 100 percent, at which the optimizer evaluates index access paths at the regular cost. Any other value makes the optimizer evaluate the access path at that percentage of the regular cost. For example, a setting of 50 makes the index access path look half as expensive as normal.

**Note:**

The adjustment does not apply to user-defined cost functions for domain indexes.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Comments.md) for additional information about this initialization parameter
