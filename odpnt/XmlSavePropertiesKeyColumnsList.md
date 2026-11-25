This property specifies the list of columns used as a key to locate existing rows for update or delete using an XML document.

### Declaration

    // C#
    public string[] KeyColumnsList {get; set;}

### Property Value

The list of columns.

### Remarks

Default value is null.

The first null value (if any) terminates the list.

`KeyColumnsList` usage with `XMLCommandType` property values:

- `Insert` - `KeyColumnsList` is ignored and can be null.

- `Update` - `KeyColumnsList` must be specified; it identifies the columns to use to find the rows to be updated.

- `Delete` - If `KeyColumnsList` is null, all the column values in each row element in the XML document are used to locate the rows to delete. Otherwise, `KeyColumnsList` specifies the columns used to identify the rows to delete.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleXmlSaveProperties Class](OracleXmlSavePropertiesClass.md)

- [OracleXmlSaveProperties Members](XmlSavePropertiesMembers.md)
