## 1.227 NLS_NCHAR_CONV_EXCP

`NLS_NCHAR_CONV_EXCP` determines whether an error is reported when there is data loss during an implicit or explicit character type conversion between NCHAR/NVARCHAR2 and CHAR/VARCHAR2.

| Property            | Description                              |
|:--------------------|:-----------------------------------------|
| Parameter type      | String                                   |
| Syntax              | `NLS_NCHAR_CONV_EXCP = { TRUE | FALSE }` |
| Default value       | `FALSE`                                  |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`          |
| Modifiable in a PDB | Yes                                      |
| Basic               | No                                       |

The default value results in no error being reported.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about this parameter
