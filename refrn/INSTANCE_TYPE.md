## 1.162 INSTANCE_TYPE

`INSTANCE_TYPE` specifies whether the instance is a database instance, an Oracle Automatic Storage Management (Oracle ASM) instance, or an Oracle ASM Proxy instance.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | String                                       |
| Syntax              | `INSTANCE_TYPE = { RDBMS | ASM | ASMPROXY }` |
| Default value       | `RDBMS`                                      |
| Modifiable          | No                                           |
| Modifiable in a PDB | No                                           |
| Basic               | No                                           |
| Oracle RAC          | Multiple instances must have the same value. |

### Values

- `RDBMS`

  The instance is a database instance.

- `ASM`

  The instance is an Oracle ASM instance.

- `ASMPROXY`

  The instance is an Oracle ASM proxy instance.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-flex-asm.md) for information about managing Oracle Flex ASM
