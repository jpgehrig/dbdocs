The `OracleIdentityType` enumeration specifies how Oracle identity column values are generated.

Table 6-179 lists all the `OracleIdentityType` enumeration values with a description of each enumerated value.

Table 6-179 OracleIdentityType Members

| Member Name                | Description                                                                                                                                                  |
|:---------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `GeneratedAlways`          | Indicates that unique values are generated for every insertion. No updates or inserts are allowed for this identity column.                                  |
| `GeneratedByDefault`       | Indicates that the values are generated only if no explicit value is provided for the identity column. Null values are not allowed for this identity column. |
| `GeneratedByDefaultOnNull` | Indicates that the values are generated only if no explicit value is provided or a `NULL` is inserted for the identity column.                               |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleDataAdapter Class](OracleDataAdapterClass.md)"

- `OracleDataAdapter` "[IdentityInsert](DataAdapterIdentityInsert.md)"

- `OracleDataAdapter` "[IdentityUpdate](DataAdapterIdentityUpdate.md)"
