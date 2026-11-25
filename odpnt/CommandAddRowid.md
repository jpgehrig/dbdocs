This property adds the `ROWID` as part of the select list.

### Declaration

    // C#
    public bool AddRowid {get; set;}

### Property Value

`bool`

### Remarks

Default is `false`.

This `ROWID` column is hidden and is not accessible by the application. To gain access to the `ROWID`s of a table, the `ROWID` must explicitly be added to the select list without the use of this property.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[LOB Support](featLOBsupp.md)" for further information on how this property used with LOBs
