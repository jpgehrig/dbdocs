An `OracleCommandBuilder` object provides automatic SQL generation for the `OracleDataAdapter` when updates are made to the database.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.ComponentModel.Component`

`      System.Data.Common.DbCommandBuilder`

`        OracleDataAccess.Client.OracleCommandBuilder`

### Declaration

    // C#
    public sealed class OracleCommandBuilder : DbCommandBuilder

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

`OracleCommandBuilder` automatically generates SQL statements for single-table updates when the `SelectCommand` property of the `OracleDataAdapter` is set. An exception is thrown if the `DataSet` contains multiple tables. The `OracleCommandBuilder` registers itself as a listener for `RowUpdating` events whenever its `DataAdapter` property is set. Only one `OracleDataAdapter` object and one `OracleCommandBuilder` object can be associated with each other at one time.

To generate `INSERT`, `UPDATE`, or `DELETE` statements, the `OracleCommandBuilder` uses `ExtendedProperties` within the `DataSet` to retrieve a required set of metadata. If the `SelectCommand` is changed after the metadata is retrieved (for example, after the first update), the `RefreshSchema` method should be called to update the metadata.

`OracleCommandBuilder` first looks for the metadata from the `ExtendedProperties` of the `DataSet`; if the metadata is not available, `OracleCommandBuilder` uses the `SelectCommand` property of the `OracleDataAdapter` to retrieve the metadata.

### Example

The following example performs an update on the `EMP` table. It uses the `OracleCommandBuilder` object to create the `UpdateCommand` for the `OracleDataAdapter` object when `OracleDataAdapter.Update()` is called.

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleCommandBuilderSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        string cmdstr = "SELECT empno, sal from emp";

        // Create the adapter with the selectCommand txt and the
        // connection string
        OracleDataAdapter adapter = new OracleDataAdapter(cmdstr, constr);

        // Create the builder for the adapter to automatically generate
        // the Command when needed
        OracleCommandBuilder builder = new OracleCommandBuilder(adapter);

        // Create and fill the DataSet using the EMP
        DataSet dataset = new DataSet();
        adapter.Fill(dataset, "EMP");

        // Get the EMP table from the dataset
        DataTable table = dataset.Tables["EMP"];

        // Indicate DataColumn EMPNO is unique
        // This is required by the OracleCommandBuilder to update the EMP table
        table.Columns["EMPNO"].Unique = true;

        // Get the first row from the EMP table
        DataRow row = table.Rows[0];

        // Update the salary
        double sal = double.Parse(row["SAL"].ToString());
        row["SAL"] = sal + .01;

        // Now update the EMP using the adapter
        // The OracleCommandBuilder will create the UpdateCommand for the
        // adapter to update the EMP table
        adapter.Update(dataset, "EMP");

        Console.WriteLine("Row updated successfully");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Members](CommandBuilderMembers.md)

- [OracleCommandBuilder Constructors](CommandBuilderCtors.md)

- [OracleCommandBuilder Static Methods](CommandBuilderStaticMethods.md)

- [OracleCommandBuilder Properties](CommandBuilderProperties.md)

- [OracleCommandBuilder Public Methods](CommandBuilderPublicMethods.md)

- [OracleCommandBuilder Events](CommandBuilderEvents.md)
