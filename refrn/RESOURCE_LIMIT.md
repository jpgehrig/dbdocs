## 1.310 RESOURCE_LIMIT

`RESOURCE_LIMIT` determines whether resource limits are enforced in database profiles.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `true`         |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | Yes            |
| Range of values     | `true | false` |
| Basic               | No             |

### Values

- `TRUE`

  Enables the enforcement of resource limits

- `FALSE`

  Disables the enforcement of resource limits

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md) and [Oracle Database SQL Language Reference](../sqlrf/CREATE-PROFILE.md) for more information on setting resource limits for profiles
