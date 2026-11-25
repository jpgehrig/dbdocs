## 1.37 CIRCUITS

`CIRCUITS` specifies the total number of virtual circuits that are available for inbound and outbound network sessions.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Integer        |
| Default value       | `4294967295`   |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | No             |
| Basic               | No             |

It is one of several parameters that contribute to the total SGA requirements of an instance.

You should not specify a value for this parameter unless you want to limit the number of virtual circuits.

**See Also:**

- [Oracle Database Concepts](../cncpt/memory-architecture.md) for more information on memory structures

- [Oracle Database Concepts](../cncpt/process-architecture.md) for more information on processes
