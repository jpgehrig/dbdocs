## 1.222 NLS_DATE_LANGUAGE

`NLS_DATE_LANGUAGE` specifies the language to use for the spelling of day and month names and date abbreviations (a.m., p.m., AD, BC) returned by the `TO_DATE` and `TO_CHAR` functions.

| Property            | Description                      |
|:--------------------|:---------------------------------|
| Parameter type      | String                           |
| Syntax              | `NLS_DATE_LANGUAGE = ``language` |
| Default value       | Derived from `NLS_LANGUAGE`      |
| Modifiable          | `ALTER SESSION`                  |
| Modifiable in a PDB | Yes                              |
| Range of values     | Any valid `NLS_LANGUAGE` value   |
| Basic               | No                               |

**Note:**

The value of this initialization parameter `NLS_DATE_LANGUAGE` is used to initialize the session value of this parameter, which is the actual value referenced by the SQL query processing. This initial value is overridden by a client-side value if the client uses the Oracle JDBC driver or if the client is OCI-based and the `NLS_LANG` client setting (environment variable) is defined. The initialization parameter value is, therefore, usually ignored.

**See Also:**

- [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for more information about this parameter

- [Oracle Database SQL Language Reference](../sqlrf/TO_DATE.md) for information on the `TO_DATE` function.

- [Oracle Database SQL Language Reference](../sqlrf/TO_CHAR-datetime.md) for information on the `TO_CHAR` function.
