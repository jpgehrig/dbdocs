The `OracleXmlCommandType` enumeration specifies the values that are allowed for the `XmlCommandType` property of the `OracleCommand` class. It is used to specify the type of XML operation.

Table 7-1 lists all the `OracleXmlCommandType` enumeration values with a description of each enumerated value.

Table 7-1 OracleXmlCommandType Members

| Member Name | Description                                                                                                                  |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------|
| `None`      | No XML operation is desired                                                                                                  |
| `Query`     | The command text is a SQL query and the result of the query is an XML document. The SQL query needs to be a select statement |
| `Insert`    | The command text is an XML document containing rows to insert.                                                               |
| `Update`    | The command text is an XML document containing rows to update.                                                               |
| `Delete`    | The command text is an XML document containing rows to delete.                                                               |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

"[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"
