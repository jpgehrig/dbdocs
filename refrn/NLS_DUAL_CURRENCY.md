## 1.223 NLS_DUAL_CURRENCY

`NLS_DUAL_CURRENCY` specifies the dual currency symbol (such as "Euro") for the territory. The default is the dual currency symbol defined in the territory of your current language environment.

| Property            | Description                               |
|:--------------------|:------------------------------------------|
| Parameter type      | String                                    |
| Syntax              | `NLS_DUAL_CURRENCY = ``currency_symbol`   |
| Default value       | Derived from `NLS_TERRITORY`              |
| Modifiable          | `ALTER SESSION`                           |
| Modifiable in a PDB | Yes                                       |
| Range of values     | Any valid format name up to 10 characters |
| Basic               | No                                        |

**Note:**

The value of this initialization parameter `NLS_DUAL_CURRENCY` is used to initialize the session value of this parameter, which is the actual value referenced by the SQL query processing. This initial value is overridden by a client-side value if the client uses the Oracle JDBC driver or if the client is OCI-based and the `NLS_LANG` client setting (environment variable) is defined. The initialization parameter value is, therefore, usually ignored.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about this parameter
