This method queries for the parameters of a stored procedure or function, represented by a specified `OracleCommand`, and populates the `OracleParameterCollection` of the command with the return values.

### Declaration

    // C#
    public static void DeriveParameters(OracleCommand command);

### Parameters

- `command`

  The command that represents the stored procedure or function for which parameters are to be derived.

### Exceptions

`InvalidOperationException` - The `CommandText` is not a valid stored procedure or function name, the `CommandType` is not `CommandType.StoredProcedure`, or the `Connection.State` is not `ConnectionState.Open`.

### Remarks

When `DeriveParameters` is used to populate the `Parameter` collection of an `OracleCommand` Object that represents a stored function, the return value of the function is bound as the first parameter (at position `0` of the `OracleParameterCollection`).

`DeriveParameters` can only be used for stored procedures or functions, not for anonymous PL/SQL blocks.

`DeriveParameters` incurs a database round-trip to retrieve parameter metadata prior to executing the stored procedure/function. It should only be used during design time. To avoid unnecessary database round-trips in a production environment, the `DeriveParameters` method itself should be replaced with the explicit parameter settings that were returned by the `DeriveParameters` method at design time.

`DeriveParameters` can only preserve the case of the stored procedure or function name if it is encapsulated by double-quotes. For example, if the stored procedure in the database is named `GetEmployees` with mixed-case, the `CommandText` property on the `OracleCommand` object must be set appropriately as in the following example:

    cmd.CommandText = "\"GetEmployees\"";

Stored procedures and functions in a package must be provided in the following format:

    <package name>.<procedure or function name>

For example, to obtain parameters for a stored procedure named `GetEmployees` (mixed-case) in a package named `EmpProcedures` (mixed-case), the name provided to the `OracleCommand` is:

    "\"EmpProcedures\".\"GetEmployees\""

`DeriveParameters` cannot be used for object type methods.

The derived parameters contain all the metadata information that is needed for the stored procedure to execute properly. The application must provide the value of the parameters before execution, if required. The application may also modify the metadata information of the parameters before execution. For example, the `Size` property of the `OracleParameter` may be modified for PL/SQL character and string types to optimize the execution of the stored procedure.

The output values of derived parameters return as .NET Types by default. To obtain output parameters as provider types, the `OracleDbType` property of the parameter must be set explicitly by the application to override this default behavior. One quick way to do this is to set the `OracleDbType` to itself for all output parameters that should be returned as provider types.

The `BindByName` property of the supplied `OracleCommand` is left as is, but the application can change its value.

If the specified stored procedure or function is overloaded, the first overload is used to populate the parameters collection.

    // Database Setup
    /*
    connect scott/tiger@oracle
    CREATE OR REPLACE PROCEDURE MyOracleStoredProc (arg_in IN VARCHAR2,
      arg_out OUT VARCHAR2) IS
    BEGIN
      arg_out := arg_in;
    END;
    /
    */

    // C#
    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class DeriveParametersSample
    {
      static void Main()
      {
        // Create the PL/SQL Stored Procedure MyOracleStoredProc as indicated in
        // the preceding Database Setup

        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Create an OracleCommand
        OracleCommand cmd = new OracleCommand("MyOracleStoredProc", con);
        cmd.CommandType = CommandType.StoredProcedure;

        // Derive Parameters
        OracleCommandBuilder.DeriveParameters(cmd);
        Console.WriteLine("Parameters Derived");

        // Prints "Number of Parameters for MyOracleStoredProc = 2"
        Console.WriteLine("Number of Parameters for MyOracleStoredProc = {0}",
          cmd.Parameters.Count);

        // The PL/SQL stored procedure MyOracleStoredProc has one IN and
        // one OUT parameter.  Set the Value for the IN parameter.
        cmd.Parameters[0].Value = "MyText";

        // The application may modify the other OracleParameter properties also
        // This sample uses the default Size for the IN parameter and modifies
        // the Size for the OUT parameter

        // The default size for OUT VARCHAR2 is 4000
        // Prints "cmd.Parameters[1].Size  = 4000"
        Console.WriteLine("cmd.Parameters[1].Size  = " + cmd.Parameters[1].Size);

        // Set the Size for the OUT parameter
        cmd.Parameters[1].Size = 6;

        // Execute the command
        cmd.ExecuteNonQuery();

        // Prints "cmd.Parameters[1].Value = MyText"
        Console.WriteLine("cmd.Parameters[1].Value = " + cmd.Parameters[1].Value);

        con.Close();
        con.Dispose();
      }
    }

### Example

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)

- [OracleCommand Class](OracleCommandClass.md)

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [`http://msdn.microsoft.com/library`](http://msdn.microsoft.com/library) for detailed information about this Microsoft .NET Framework feature
