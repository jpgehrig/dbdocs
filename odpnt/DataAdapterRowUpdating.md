This event is raised when row data are about to be updated to the database.

### Declaration

    // C#
    public event OracleRowUpdatingEventHandler RowUpdating;

### Event Data

The event handler receives an `OracleRowUpdatingEventArgs` object which exposes the following properties containing information about the event.

- `Command`

  The `OracleCommand` executed during the `Update`.

- `Errors` (inherited from `RowUpdatingEventArgs`)

  The exception, if any, is generated during the `Update`.

- `Row` (inherited from `RowUpdatingEventArgs`)

  The `DataRow` sent for `Update`.

- `StatementType` (inherited from `RowUpdatingEventArgs`)

  The type of SQL statement executed.

- `Status` (inherited from `RowUpdatingEventArgs`)

  The `UpdateStatus` of the `Command`.

- `TableMapping` (inherited from `RowUpdatingEventArgs`)

  The `DataTableMapping` used during the `Update`.

### Example

The example for the `RowUpdated` event also shows how to use the `RowUpdating` event. See `RowUpdated` event "[Example](DataAdapterRowUpdated.md)".

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[OracleRowUpdatingEventHandler Delegate](OracleRowUpdatingEventHandlerDelegate.md)"
