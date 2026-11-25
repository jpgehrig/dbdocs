## 1.282 PERMIT_92_WRAP_FORMAT

`PERMIT_92_WRAP_FORMAT` allows Oracle Database release 9.2 wrapped versions of PL/SQL source text to be used in Oracle Database releases 10.2 and later when this parameter is set to `true`.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | Boolean                                      |
| Default value       | `true`                                       |
| Modifiable          | No                                           |
| Modifiable in a PDB | No                                           |
| Range of values     | `true | false`                               |
| Basic               | No                                           |
| Oracle RAC          | Multiple instances should use the same value |

Oracle recommends that wrapped files be created using the PL/SQL Wrapper utility from Oracle Database release 10 or later.

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/plsql-source-text-wrapping.md) for more information about PL/SQL source text wrapping
