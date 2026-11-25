This method executes a command using the `XmlCommandType` and `CommandText` properties and appends the result as an XML document to the existing `Stream` provided by the application.

### Declaration

    // C#
    public void ExecuteToStream(Stream outputStream);

### Parameters

- `outputStream`

  A `Stream`.

### Remarks

The behavior of `ExecuteToStream` varies depending on the `XmlCommandType` property value:

- `XmlCommandType` = `OracleXmlCommandType.None`

  `ExecuteToStream` throws an `InvalidOperationException`.

- `XmlCommandType` = `OracleXmlCommandType`.`Query`

  `ExecuteToStream` executes the select statement in the `CommandText` property, and if successful, appends the XML document that was generated to the given `Stream`.

  If the SQL query does not return any rows, then nothing is appended to the given `Stream`. The character set of the appended data is Unicode.

- `XmlCommandType` = `OracleXmlCommandType`.`Insert`, `OracleXmlCommandType`.`Update`, or `OracleXmlCommandType`.`Delete`

  The value of the `CommandText` property is an XML document. `ExecuteToStream` saves the changes in that XML document to the table or view that is specified in the `XmlSaveProperties` property. Nothing is appended to the given `Stream`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- [Oracle XML DB Developer’s Guide](../adxdb/XML-DB-and-ODP-for-dot-NET.md)

- [`http://www.oracle.com/technetwork/index.html`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=otn_index)
