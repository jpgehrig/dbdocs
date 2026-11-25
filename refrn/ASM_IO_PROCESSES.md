## 1.20 ASM_IO_PROCESSES

`ASM_IO_PROCESSES` specifies the number of I/O worker processes to be started in an Oracle IOServer instance.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Integer                                       |
| Default value       | `20`                                          |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | No                                            |
| Range of values     | `1` – `32`                                    |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |

This parameter is applicable only in an Oracle IOServer instance, which runs out of an Oracle Grid Infrastructure home.

The default value should work in most cases. However, under heavy I/O load, there may be some delays associated with posting processes out of I/O waits. In this case, a slightly higher value than the default may be appropriate.
