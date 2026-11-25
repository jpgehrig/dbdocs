The `REF` `CURSOR` is a data type in the Oracle PL/SQL language. It represents a cursor or a result set in Oracle Database. The `OracleRefCursor` object is a corresponding ODP.NET type for the `REF` `CURSOR` type.

This section discusses the following aspects of using the `REF` `CURSOR` data type and `OracleRefCursor` objects:

- Obtaining an OracleRefCursor Object

- Obtaining a REF CURSOR Data Type

- Populating an OracleDataReader from a REF CURSOR

- Populating the DataSet from a REF CURSOR

- Populating an OracleRefCursor from a REF CURSOR

- Updating a DataSet Obtained from a REF CURSOR

- Behavior of ExecuteScalar Method for REF CURSOR

- Passing a REF CURSOR to a Stored Procedure

### Obtaining an OracleRefCursor Object

There are no constructors for `OracleRefCursor` objects. They can be acquired only as parameter values from PL/SQL stored procedures, stored functions, or anonymous blocks.

An `OracleRefCursor` object is a connected object. The connection used to execute the command returning an `OracleRefCursor` object is required for its lifetime. Once the connection associated with an `OracleRefCursor object `is closed, the `OracleRefCursor` object cannot be used.

### Obtaining a REF CURSOR Data Type

A `REF` `CURSOR` data type can be obtained as an `OracleDataReader`, `DataSet`, or `OracleRefCursor` object. If the `REF` `CURSOR` data type is obtained as an `OracleRefCursor` object, it can be used to create an `OracleDataReader` object or populate a `DataSet` from it. When accessing a `REF` `CURSOR` data type, always bind it as an `OracleDbType.RefCursor` parameter.

### Populating an OracleDataReader from a REF CURSOR

A `REF` `CURSOR` data type can be obtained as an `OracleDataReader` object by calling the `ExecuteReader` method of the `OracleCommand` object. The output parameter with the `OracleDbType` property set is bound to `OracleDbType.RefCursor`. None of the output parameters of type `OracleDbType.RefCursor` is populated after the `ExecuteReader` method is invoked.

If there are multiple output `REF` `CURSOR` parameters, use the `NextResult` method of the `OracleDataReader` object to access the next `REF` `CURSOR` data type. The `OracleDataReader` `NextResult` method provides sequential access to the `REF` `CURSOR` data types; only one `REF` `CURSOR` data type can be accessed at a given time.

The order in which `OracleDataReader` objects are created for the corresponding `REF` `CURSOR` data types depends on the order in which the parameters are bound. If a PL/SQL stored function returns a `REF` `CURSOR` data type, then it becomes the first `OracleDataReader` object and all the output `REF` `CURSOR` data types follow the order in which the parameters are bound.

### Populating the DataSet from a REF CURSOR

For the `Fill` method to populate the `DataSet` properly, the `SelectCommand` property of the `OracleDataAdapter` class must be bound with an output parameter of type `OracleDbType.RefCursor`. If the `Fill` method is successful, the `DataSet` is populated with a `DataTable` that represents a `REF` `CURSOR` data type.

If the command execution returns multiple `REF` `CURSOR` data types, the `DataSet` is populated with multiple `DataTable` objects.

With Oracle Data Provider for .NET release 11.1.0.6.20, the extended property, `REFCursorName`, has been introduced on the `DataTable`, to identify the `REF` `CURSOR` that populates the `DataTable`.

This property is particularly useful when a `DataSet` is being populated with more than one `REF` `CURSOR`, one or more of which is `NULL`. For example, if a `DataSet` is populated by executing a stored procedure that returns three `REF` `CURSOR`s and the second `REF` `CURSOR` is `NULL`, the `REFCursorName` property value for the first `DataTable` is `REFCursor` and for the second `DataTable`, `REFCursor2` . No `DataTable` is populated for the `NULL` `REF` `CURSOR`.

### Populating an OracleRefCursor from a REF CURSOR

When the `ExecuteNonQuery` method is invoked on a command that returns one or more `REF` `CURSOR` data types, each of the `OracleCommand` parameters that are bound as an `OracleDbType.RefCursor` gets a reference to an `OracleRefCursor` object.

To create an `OracleDataReader` object from an `OracleRefCursor` object, invoke the `GetDataReader` method from the `OracleRefCursor` object. Subsequent calls to the `GetDataReader` method return a reference to the same `OracleDataReader` object.

To populate a `DataSet` with an `OracleRefCursor` object, the application can invoke a `Fill` method of the `OracleDataAdapter` class that takes an `OracleRefCursor` object. Similar to the `OracleDataReader` object, an `OracleRefCursor` object is forward-only. Therefore, once a row is read from an `OracleRefCursor` object, that same row cannot be obtained again from it unless it is populated again from a query.

When multiple `REF` `CURSOR` data types are returned from a command execution as `OracleRefCursor` objects, the application can choose to create an `OracleDataReader` object or populate a `DataSet` with a particular `OracleRefCursor` object. All the `OracleDataReader` objects or `DataSet` objects created from the `OracleRefCursor` objects are active at the same time, and can be accessed in any order.

### Updating a DataSet Obtained from a REF CURSOR

`REF` `CURSOR` types cannot be updated. However, data that is retrieved into a `DataSet` can be updated. Therefore, the `OracleDataAdapter` class requires a custom SQL statement to flush any `REF` `CURSOR` data updates to the database.

The `OracleCommandBuilder` object cannot be used to generate SQL statements for `REF` `CURSOR` updates.

### Behavior of ExecuteScalar Method for REF CURSOR

The `ExecuteScalar` method returns the value of the first column of the first row of the `REF` `CURSOR` if it is one of the following:

- A return value of a stored function execution

- The first bind parameter of a stored procedure execution

**See Also:**

[Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md)for more information

### Passing a REF CURSOR to a Stored Procedure

An application can retrieve a `REF` `CURSOR` type from a PL/SQL stored procedure or function and pass it to another stored procedure or function. This feature is useful in scenarios where a stored procedure or a function returns a `REF` `CURSOR` type to the .NET application, and based on the application logic, the application passes this `REF` `CURSOR` to another stored procedure for processing. Note that if you retrieve the data from a `REF` `CURSOR` type in the .NET application, you cannot pass it back to another stored procedure.

The following example demonstrate passing a `REF` `CURSOR`:

    /*
    connect scott/tiger@oracle
    create table test (col1 number);
    insert into test(col1) values (1);
    commit;

    create or replace package testPkg as type empCur is REF Cursor;
    end testPkg;
    /

    create or replace procedure testSP(param1 IN testPkg.empCur, param2 OUT NUMBER)
    as
    begin
    FETCH param1 into param2;
    end;
    /
    */

    // C#


    using System;
    using Oracle.DataAccess.Client;
    using System.Data;

    class InRefCursorParameterSample
    {
      static void Main()
      {
        OracleConnection conn = new OracleConnection
          ("User Id=scott; Password=tiger; Data Source=oracle");

        conn.Open(); // Open the connection to the database

        // Command text for getting the REF Cursor as OUT parameter
        String cmdTxt1 = "begin open :1 for select col1 from test; end;";

        // Command text to pass the REF Cursor as IN parameter
        String cmdTxt2 = "begin testSP (:1, :2); end;";

        // Create the command object for executing cmdTxt1 and cmdTxt2
        OracleCommand cmd = new OracleCommand(cmdTxt1, conn);

        // Bind the Ref cursor to the PL/SQL stored procedure
        OracleParameter outRefPrm = cmd.Parameters.Add("outRefPrm",
          OracleDbType.RefCursor, DBNull.Value, ParameterDirection.Output);

        cmd.ExecuteNonQuery(); // Execute the anonymous PL/SQL block

        // Reset the command object to execute another anonymous PL/SQL block
        cmd.Parameters.Clear();
        cmd.CommandText = cmdTxt2;

        // REF Cursor obtained from previous execution is passed to this
        // procedure as IN parameter
        OracleParameter inRefPrm = cmd.Parameters.Add("inRefPrm",
          OracleDbType.RefCursor, outRefPrm.Value, ParameterDirection.Input);

        // Bind another Number parameter to get the REF Cursor column value
        OracleParameter outNumPrm = cmd.Parameters.Add("outNumPrm",
          OracleDbType.Int32, DBNull.Value, ParameterDirection.Output);

        cmd.ExecuteNonQuery(); //Execute the stored procedure

        // Display the out parameter value
        Console.WriteLine("out parameter is: " + outNumPrm.Value.ToString());
      }
    }
