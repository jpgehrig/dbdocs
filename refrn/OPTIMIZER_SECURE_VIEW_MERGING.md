## 1.257 OPTIMIZER_SECURE_VIEW_MERGING

`OPTIMIZER_SECURE_VIEW_MERGING` enables the optimizer to use view merging to improve query performance without performing the checks that would otherwise be performed to ensure that view merging does not violate any security intentions of the view creator.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | Boolean                                      |
| Default value       | `true`                                       |
| Modifiable          | `ALTER SYSTEM`                               |
| Modifiable in a PDB | Yes                                          |
| Range of values     | `true | false`                               |
| Basic               | No                                           |
| Oracle RAC          | Multiple instances can have different values |

### Values

- `false`

  Oracle Database does not perform security checks that may prevent view merging and predicate move-around.

- `true`

  Oracle Database performs checks to ensure that view merging and predicate move-around do not violate any security intentions of the view creator.

To enable the optimizer to use view merging for any query issued by a user, you must grant the `MERGE ANY VIEW` privilege to the user. Grant the `MERGE VIEW` privilege to a user on specific views to enable the optimizer to use view merging for queries on these views. These privileges are required only under specific conditions, such as when a view is not merged because the security checks fail.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/query-transformations.md) for more information about view merging
