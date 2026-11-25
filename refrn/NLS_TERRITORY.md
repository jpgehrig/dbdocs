## 1.230 NLS_TERRITORY

`NLS_TERRITORY` specifies the name of the territory whose conventions are to be followed for day and week numbering.

| Property            | Description                   |
|:--------------------|:------------------------------|
| Parameter type      | String                        |
| Syntax              | `NLS_TERRITORY = ``territory` |
| Default value       | Operating system-dependent    |
| Modifiable          | `ALTER SESSION`               |
| Modifiable in a PDB | Yes                           |
| Range of values     | Any valid territory name      |
| Basic               | Yes                           |

This parameter also establishes the default date format, the default decimal character and group separator, and the default ISO and local currency symbols.

For information on these settings, see "[NLS_DATE_FORMAT](NLS_DATE_FORMAT.md)", "[NLS_NUMERIC_CHARACTERS](NLS_NUMERIC_CHARACTERS.md)", "[NLS_CURRENCY](NLS_CURRENCY.md)", and "[NLS_ISO_CURRENCY](NLS_ISO_CURRENCY.md)".

**Note:**

The value of this initialization parameter `NLS_TERRITORY` is used to initialize the session value of this parameter, which is the actual value referenced by the SQL query processing. This initial value is overridden by a client-side value if the client uses the Oracle JDBC driver or if the client is OCI-based and the `NLS_LANG` client setting (environment variable) is defined. The initialization parameter value is, therefore, usually ignored.

### Examples

For an example of overriding the default value for the `NLS_TERRITORY` parameter, see [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md).

**See Also:**

- [Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md) for a complete list of territories

- Your operating system-specific Oracle documentation for the territory-dependent default values for these parameters
