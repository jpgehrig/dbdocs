This method executes a SQL statement or a command using the `XmlCommandType` and `CommandText` properties and returns the number of rows affected.

### Declaration

    // C#
    public override int ExecuteNonQuery();

### Return Value

The number of rows affected.

### Implements

`IDbCommand`

### Exceptions

`InvalidOperationException` - The command cannot be executed.

### Remarks

`ExecuteNonQuery` returns the number of rows affected, for the following:

- If the command is `UPDATE`, `INSERT`, or `DELETE` and the `XmlCommandType` property is set to `OracleXmlCommandType.None`.

- If the `XmlCommandType` property is set to `OracleXmlCommandType.Insert`, `OracleXmlCommandType.Update`, `OracleXmlCommandType.Delete`.

For all other types of statements, the return value is `-1`.

`ExecuteNonQuery` is used for either of the following:

- Catalog operations (for example, querying the structure of a database or creating database objects such as tables).

- Changing the data in a database without using a `DataSet`, by executing `UPDATE`, `INSERT`, or `DELETE` statements.

- Changing the data in a database using an XML document.

Although `ExecuteNonQuery` does not return any rows, it populates any output parameters or return values mapped to parameters with data.

If the `XmlCommandType` property is set to `OracleXmlCommandType.Query` then `ExecuteNonQuery` executes the select statement in the `CommandText` property, and if successful, returns `-1`. The XML document that is generated is discarded. This is useful for determining if the operation completes successfully without getting the XML document back as a result.

If the `XmlCommandType` property is set to `OracleXmlCommandType.Insert`, `OracleXmlCommandType.Update`, or `OracleXmlCommandType.Delete`, then the value of the `CommandText` property is an XML document. `ExecuteNonQuery` saves the changes in that XML document to the table or view that is specified in the `XmlSaveProperties` property. The return value is the number of rows that are processed in the XML document. Also, each row in the XML document could affect multiple rows in the database, but the return value is still the number of rows in the XML document.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class ExecuteNonQuerySample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleCommand cmd = new OracleCommand(
          "select sal from emp where empno=7934", con);

        object sal = cmd.ExecuteScalar();
        Console.WriteLine("Employee sal before update: " + sal);

        cmd.CommandText = "update emp set sal = sal + .01 where empno=7934";

        // Auto-commit changes
        int rowsUpdated = cmd.ExecuteNonQuery();

        if (rowsUpdated > 0)
        {
          cmd.CommandText = "select sal from emp where empno=7934";
          sal = cmd.ExecuteScalar();
          Console.WriteLine("Employee sal after update: " + sal);
        }

        // Clean up
        cmd.Dispose();
        con.Dispose();
      }
    }

### Requirements

For XML support, this method requires Oracle9i XML Developer's Kits (Oracle XDK) or later, to be installed in the database. Oracle XDK can be downloaded from Oracle Technology Network (OTN).

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- [`http://www.oracle.com/technetwork/index.html`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=otn_index)
