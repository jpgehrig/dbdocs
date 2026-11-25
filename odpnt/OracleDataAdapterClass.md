An `OracleDataAdapter` object represents a data provider object that populates the `DataSet` and updates changes in the `DataSet` to the Oracle database.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.ComponentModel.Component`

`      System.Data.Common.DataAdapter`

`        System.Data.Common.DbDataAdapter`

`          Oracle.DataAccess.Client.OracleDataAdapter`

### Declaration

    // C#
    public sealed class OracleDataAdapter : DbDataAdapter, IDbDataAdapter

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

The following example uses the `OracleDataAdapter` and the dataset to update the `EMP` table:

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class OracleDataAdapterSample
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

- [OracleDataAdapter Members](DataAdapterMembers.md)

- [OracleDataAdapter Constructors](DataAdapterCtors.md)

- [OracleDataAdapter Static Methods](DataAdapterStaticMethods.md)

- [OracleDataAdapter Properties](DataAdapterProperties.md)

- [OracleDataAdapter Public Methods](DataAdapterPublicMethods.md)

- [OracleDataAdapter Events](DataAdapterEvents.md)
