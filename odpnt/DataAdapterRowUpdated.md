This event is raised when row(s) have been updated by the `Update()` method.

### Declaration

    // C#
    public event OracleRowUpdatedEventHandler RowUpdated;

### Event Data

The event handler receives an `OracleRowUpdatedEventArgs` object which exposes the following properties containing information about the event.

- `Command`

  The `OracleCommand` executed during the `Update`.

- `Errors` (inherited from `RowUpdatedEventArgs`)

  The exception, if any, is generated during the `Update`.

- `RecordsAffected` (inherited from `RowUpdatedEventArgs`)

  The number of rows modified, inserted, or deleted by the execution of the `Command`.

- `Row` (inherited from `RowUpdatedEventArgs`)

  The `DataRow` sent for `Update`.

- `StatementType` (inherited from `RowUpdatedEventArgs`)

  The type of SQL statement executed.

- `Status` (inherited from `RowUpdatedEventArgs`)

  The `UpdateStatus` of the `Command`.

- `TableMapping` (inherited from `RowUpdatedEventArgs`)

  The `DataTableMapping` used during the `Update`.

### Example

The following example shows how to use the `RowUpdating` and `RowUpdated` events.

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class RowUpdatedSample
    {
      // Event handler for RowUpdating event
      protected static void OnRowUpdating(object sender,
                                          OracleRowUpdatingEventArgs e)
      {
        Console.WriteLine("Row updating.....");
        Console.WriteLine("Event arguments:");
        Console.WriteLine("Command Text: " + e.Command.CommandText);
        Console.WriteLine("Command Type: " + e.StatementType);
        Console.WriteLine("Status: " + e.Status);
      }

      // Event handler for RowUpdated event
      protected static void OnRowUpdated(object sender,
                                         OracleRowUpdatedEventArgs e)
      {
        Console.WriteLine("Row updated.....");
        Console.WriteLine("Event arguments:");
        Console.WriteLine("Command Text: " + e.Command.CommandText);
        Console.WriteLine("Command Type: " + e.StatementType);
        Console.WriteLine("Status: " + e.Status);
      }

      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        string cmdstr = "SELECT EMPNO, ENAME, SAL FROM EMP";

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

        // Set the event handlers for the RowUpdated and the RowUpdating event
        // the OnRowUpdating() method will be triggered before the update, and
        // the OnRowUpdated() method will be triggered after the update
        adapter.RowUpdating += new OracleRowUpdatingEventHandler(OnRowUpdating);
        adapter.RowUpdated += new OracleRowUpdatedEventHandler(OnRowUpdated);

        // Now update the EMP using the adapter
        // The OracleCommandBuilder will create the UpdateCommand for the
        // adapter to update the EMP table
        // The OnRowUpdating() and the OnRowUpdated() methods will be triggered
        adapter.Update(dataset, "EMP");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[OracleRowUpdatedEventHandler Delegate](OracleRowUpdatedEventHandlerDelegate.md)"
