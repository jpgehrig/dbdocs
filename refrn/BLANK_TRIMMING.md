## 1.35 BLANK_TRIMMING

`BLANK_TRIMMING` specifies the data assignment semantics of character datatypes.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `false`        |
| Modifiable          | No             |
| Modifiable in a PDB | Yes            |
| Range of values     | `true | false` |
| Basic               | No             |

### Values

- `TRUE`

  Allows the data assignment of a source character string or variable to a destination character column or variable even though the source length is longer than the destination length. In this case, however, the additional length over the destination length must be all blanks, else an exception condition is raised. This value complies with the semantics of SQL-92 Transitional Level and above.

- `FALSE`

  Disallows the data assignment if the source length is longer than the destination length and reverts to SQL92 Entry Level semantics.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/character-set-migration.md) for more information on how using this parameter can help prevent data truncation issues during character set migration
