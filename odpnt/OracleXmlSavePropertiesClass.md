An `OracleXmlSaveProperties` object represents the XML properties used by the `OracleCommand` class when the `XmlCommandType` property is `Insert`, `Update`, or `Delete`.

### Class Inheritance

`System.Object`

`  System.OracleXmlSaveProperties`

### Declaration

    public sealed class OracleXmlSaveProperties : ICloneable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

`OracleXmlSaveProperties` can be accessed and modified using the `XmlSaveProperties` property of the `OracleCommand` class. Each `OracleCommand` object has its own instance of the `OracleXmlSaveProperties` class in the `XmlSaveProperties` property.

Use the default constructor to get a new instance of `OracleXmlSaveProperties`. Use the `OracleXmlSaveProperties``.Clone()` method to get a copy of an `OracleXmlSaveProperties` instance.

### Example

This sample demonstrates how to do inserts, updates, and deletes to a relational table or view using an XML document.

    // C#
    /* -- If HR account is being locked, you need to log on as a DBA
       -- to unlock the account first. Unlock a locked users account:

       ALTER USER hr ACCOUNT UNLOCK;
    */

    using System;
    using Oracle.DataAccess.Client;

    class OracleXmlSavePropertiesSample
    {
      static void Main()
      {
        string[] KeyColumnsList = null;
        string[] UpdateColumnsList = null;
        int rows = 0;

        // Create the connection.
        string constr = "User Id=hr;Password=hr;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Create the command.
        OracleCommand cmd = new OracleCommand("", con);

        // Set the XML command type to insert.
        cmd.XmlCommandType = OracleXmlCommandType.Insert;

        // Set the XML document.
        cmd.CommandText = "<?xml version=\"1.0\"?>\n" +
          "<ROWSET>\n" +
          " <MYROW num = \"1\">\n" +
          " <EMPLOYEE_ID>1234</EMPLOYEE_ID>\n" +
          " <LAST_NAME>Smith</LAST_NAME>\n" +
          " <EMAIL>Smith@Oracle.com</EMAIL>\n" +
          " <HIRE_DATE>1982-01-23T00:00:00.000</HIRE_DATE>\n" +
          " <JOB_ID>IT_PROG</JOB_ID>\n" +
          " </MYROW>\n" +
          " <MYROW num = \"2\">\n" +
          " <EMPLOYEE_ID>1235</EMPLOYEE_ID>\n" +
          " <LAST_NAME>Barney</LAST_NAME>\n" +
          " <EMAIL>Barney@Oracle.com</EMAIL>\n" +
          " <HIRE_DATE>1982-01-23T00:00:00.000</HIRE_DATE>\n" +
          " <JOB_ID>IT_PROG</JOB_ID>\n" +
          " </MYROW>\n" +
          "</ROWSET>\n";

        // Set the XML save properties.
        KeyColumnsList = new string[1];
        KeyColumnsList[0] = "EMPLOYEE_ID";
        UpdateColumnsList = new string[5];
        UpdateColumnsList[0] = "EMPLOYEE_ID";
        UpdateColumnsList[1] = "LAST_NAME";
        UpdateColumnsList[2] = "EMAIL";
        UpdateColumnsList[3] = "HIRE_DATE";
        UpdateColumnsList[4] = "JOB_ID";
        cmd.XmlSaveProperties.KeyColumnsList = KeyColumnsList;
        cmd.XmlSaveProperties.RowTag = "MYROW";
        cmd.XmlSaveProperties.Table = "employees";
        cmd.XmlSaveProperties.UpdateColumnsList = UpdateColumnsList;
        cmd.XmlSaveProperties.Xslt = null;
        cmd.XmlSaveProperties.XsltParams = null;

        // Do the inserts.
        rows = cmd.ExecuteNonQuery();
        Console.WriteLine("rows: " + rows);

        // Set the XML command type to update.
        cmd.XmlCommandType = OracleXmlCommandType.Update;

        // Set the XML document.
        cmd.CommandText = "<?xml version=\"1.0\"?>\n" +
          "<ROWSET>\n" +
          " <MYROW num = \"1\">\n" +
          " <EMPLOYEE_ID>1234</EMPLOYEE_ID>\n" +
          " <LAST_NAME>Adams</LAST_NAME>\n" +
          " </MYROW>\n" +
          "</ROWSET>\n";

        // Set the XML save properties.
        KeyColumnsList = new string[1];
        KeyColumnsList[0] = "EMPLOYEE_ID";
        UpdateColumnsList = new string[1];
        UpdateColumnsList[0] = "LAST_NAME";
        cmd.XmlSaveProperties.KeyColumnsList = KeyColumnsList;
        cmd.XmlSaveProperties.UpdateColumnsList = UpdateColumnsList;
        rows = cmd.ExecuteNonQuery();
        Console.WriteLine("rows: " + rows);

        // Set the XML command type to delete.
        cmd.XmlCommandType = OracleXmlCommandType.Delete;

        // Set the XML document.
        cmd.CommandText = "<?xml version=\"1.0\"?>\n" +
          "<ROWSET>\n" +
          " <MYROW num = \"1\">\n" +
          " <EMPLOYEE_ID>1234</EMPLOYEE_ID>\n" +
          " </MYROW>\n" +
          " <MYROW num = \"2\">\n" +
          " <EMPLOYEE_ID>1235</EMPLOYEE_ID>\n" +
          " </MYROW>\n" +
          "</ROWSET>\n";

        // Set the XML save properties.
        KeyColumnsList = new string[1];
        KeyColumnsList[0] = "EMPLOYEE_ID";
        cmd.XmlSaveProperties.KeyColumnsList = KeyColumnsList;
        cmd.XmlSaveProperties.UpdateColumnsList = null;

        // Do the deletes.
        rows = cmd.ExecuteNonQuery();
        Console.WriteLine("rows: " + rows);

        // Clean up.
        cmd.Dispose();
        con.Close();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleXmlSaveProperties Members](XmlSavePropertiesMembers.md)

- [OracleXmlSaveProperties Constructor](XmlSavePropertiesCtors.md)

- [OracleXmlSaveProperties Properties](XmlSavePropertiesProperties.md)

- [OracleXmlSaveProperties Public Methods](XmlSavePropertiesPublicMethods.md)
