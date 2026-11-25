This property specifies whether or not `ROWID` information is part of change notification events fired whenever data changes on the database.

### Declaration

    // C#
    public OracleRowidInfo RowidInfo {get; set;};


### Property Value

An `OracleRowidInfo` enumeration type that determines the inclusion of `ROWID` in the change notification event.

### Remarks

There are three `OracleRowidInfo` enumeration types that are valid for this property:

- `Default` includes `ROWID` information in the change notification event only if `OracleCommand.AddRowid` property is set to true or if `ROWID` is in the select list of the query that is registered for change notification.

- `Include` includes `ROWID` information regardless of whether or not `ROWID` is in the select-list for the query.

- `Exclude` excludes `ROWID` information regardless of whether or not `ROWID` is in the select-list.

For change notification registrations that involve stored procedure executions, change notification events related to the `REF` `CURSOR` contain `ROWID` information only if `RowidInfo` property is set to `OracleRowidInfo.Include`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)

- "[OracleRowidInfo Enumeration](OracleRowidInfoEnumeration.md)"
