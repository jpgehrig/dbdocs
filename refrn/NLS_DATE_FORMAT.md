## 1.221 NLS_DATE_FORMAT

`NLS_DATE_FORMAT` specifies the default datetime format model to use with the `TO_CHAR` and `TO_DATE` functions. The default value of this parameter is determined by `NLS_TERRITORY`.

| Property            | Description                      |
|:--------------------|:---------------------------------|
| Parameter type      | String                           |
| Syntax              | `NLS_DATE_FORMAT = "``format``"` |
| Default value       | Derived from `NLS_TERRITORY`     |
| Modifiable          | `ALTER SESSION`                  |
| Modifiable in a PDB | Yes                              |
| Range of values     | Any valid datetime format model  |
| Basic               | No                               |

The value of this parameter can be any valid datetime format model, and the value must be surrounded by double quotation marks. For example:

    NLS_DATE_FORMAT = "MM/DD/YYYY"

**Note:**

The value of this initialization parameter `NLS_DATE_FORMAT` is used to initialize the session value of this parameter, which is the actual value referenced by the SQL query processing. This initial value is overridden by a client-side value if the client uses the Oracle JDBC driver or if the client is OCI-based and the `NLS_LANG` client setting (environment variable) is defined. The initialization parameter value is, therefore, usually ignored.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md) for more information on datetime format models

- [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about this parameter
