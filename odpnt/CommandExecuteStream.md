This method executes a command using the `XmlCommandType` and `CommandText` properties and returns the result as an XML document in a new `Stream` object.

### Declaration

    // C#
    public Stream ExecuteStream();

### Return Value

A `Stream`.

### Remarks

The behavior of `ExecuteStream` varies depending on the `XmlCommandType` property value:

- `XmlCommandType` = `OracleXmlCommandType.None`

  `ExecuteStream` throws an `InvalidOperationException`.

- `XmlCommandType` = `OracleXmlCommandType`.`Query`

  `ExecuteStream` executes the select statement in the `CommandText` property, and if successful, returns an `OracleClob` object containing the XML document that was generated. `OracleClob` contains Unicode characters.

  If the SQL query does not return any rows, then `ExcecuteStream` returns an `OracleClob` object containing an empty XML document.

- `XmlCommandType` = `OracleXmlCommandType`.`Insert`, `OracleXmlCommandType`.`Update`, or `OracleXmlCommandType`.`Delete`.

  The value of the `CommandText` property is an XML document. `ExecuteStream` saves the data in that XML document to the table or view that is specified in the `XmlSaveProperties` property and an empty `OracleClob` is returned.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-and-ODP-for-dot-NET.md)

- [`http://www.oracle.com/technetwork/index.html`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=otn_index)
