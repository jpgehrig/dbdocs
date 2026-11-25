## 1.291 PLSQL_WARNINGS

`PLSQL_WARNINGS` enables or disables the reporting of warning messages by the PL/SQL compiler, and specifies which warning messages to show as errors.

| Property            | Description                                                                                                                                                                                                                                  |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                                                                                                                                                       |
| Syntax              | `PLSQL_WARNINGS = '``value_clause``' [, '``value_clause``' ] ...`                                                                                                                                                                            |
| Syntax              | `value_clause::=`<br>` { ENABLE | DISABLE | ERROR }:`<br>` { ALL`<br>` | SEVERE`<br>` | INFORMATIONAL`<br>` | PERFORMANCE`<br>` | { ``integer `<br>` | (``integer`` [, ``integer`` ] ...)`<br>` }`<br>` }`                                   |
| Default value       | `'DISABLE:ALL'`                                                                                                                                                                                                                              |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                                                                                                                                                                                              |
| Modifiable in a PDB | Yes                                                                                                                                                                                                                                          |
| Basic               | No                                                                                                                                                                                                                                           |
| Examples            | `PLSQL_WARNINGS = 'ENABLE:SEVERE', 'DISABLE:INFORMATIONAL';`<br>`PLSQL_WARNINGS = 'DISABLE:ALL';`<br>`PLSQL_WARNINGS = 'DISABLE:5000', 'ENABLE:5001', 'ERROR:5002';`<br>`PLSQL_WARNINGS = 'ENABLE:(5000,5001,5002)', 'DISABLE:(6000,6001)';` |

### `value_clause`

Multiple value clauses may be specified, enclosed in quotes and separated by commas. Each value clause is composed of a qualifier, a colon (`:`), and a modifier.

Qualifier values:

- `ENABLE`

  Enable a specific warning or a set of warnings

- `DISABLE`

  Disable a specific warning or a set of warnings

- `ERROR`

  Treat a specific warning or a set of warnings as errors

Modifier values:

- `ALL`

  Apply the qualifier to all warning messages

- `SEVERE`

  Apply the qualifier to only those warning messages in the `SEVERE` category

- `INFORMATIONAL`

  Apply the qualifier to only those warning messages in the `INFORMATIONAL` category

- `PERFORMANCE`

  Apply the qualifier to only those warning messages in the `PERFORMANCE` category

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/architecture-pl-sql.md) for more information about this parameter
