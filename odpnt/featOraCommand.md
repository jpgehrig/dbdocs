The `OracleCommand` object represents SQL statements or stored procedures executed on Oracle Database.

**Note:**

Optimizer hint syntax in the form `--+ ...` is not supported. ODP.NET supports this syntax: `/*+ ... */`.

This section includes the following topics:

- Transactions

- System.Transactions and Promotable Transactions

- Parameter Binding

- Batch Processing

- Statement Caching

- Self-Tuning

### Transactions

Oracle Database starts a transaction only in the context of a connection. Once a transaction starts, all the successive command execution on that connection run in the context of that transaction. Transactions can be started only on an `OracleConnection` object, and the read-only `Transaction` property on the `OracleCommand` object is implicitly set by the `OracleConnection` object. Therefore, the application cannot set the `Transaction` property, nor does it need to.

**Note:**

Transactions are not supported in a .NET stored procedure.

Explicit transactions are required with SQL statements containing `"FOR` `UPDATE"` and `"RETURNING"` clauses. This is not necessary if global transactions are used.

### System.Transactions and Promotable Transactions

ODP.NET supports `System.Transactions`. A local transaction is created for the first connection opened in the `System.Transactions` scope to Oracle Database 11g release 1 (11.1), or higher. When a second connection is opened, this transaction is automatically promoted to a distributed transaction. This functionality provides enhanced performance and scalability.

Connections created within a transaction context, such as `TransactionScope` or `ServicedComponent`, can be established to different versions of Oracle Database. However, in order to enable the local transaction to be promotable, the following must be true:

- The first connection in the transaction context must be established to an Oracle Database 11g release 1(11.1) instance or higher.

- All connections opened within the transaction context must have the `"Promotable Transaction"` setting set to `"promotable"`. If you try to open a subsequent connection in the same transaction context with the `"Promotable Transaction"` setting set to `"local"`, an exception is thrown.

- Promoting local transactions requires Oracle Services for Microsoft Transaction Server 11.1.0.7.20, or higher. If this requirement is not met, then a second connection request in the same transaction context throws an exception.

Transaction promotion will throw an ORA-24797 error when the database transaction is already distributed due to the use of database links.

Setting `"local"` as the value of `"PromotableTransaction"` in the registry, configuration file (machine/Web/application), or the `"Promotable Transaction"` connection string attribute allows only one connection to be opened in the transaction context, which is associated with a local transaction. Such local transactions cannot be promoted. Starting with ODP.NET 12.1.0.2, connections with the `Promotable Transaction` setting set to `local` will begin as and remain a local transaction. If a second connection attempts to join the transaction, an exception will be thrown.

If applications use `System.Transactions`, it is required that the `enlist` connection string attribute is set to either `true` (default) or `dynamic`. However, `enlist=dynamic` cannot be used with `TransactionScope` because auto-enlistment requires `enlist=true`.

ODP.NET supports the following `System.Transactions` programming models for applications using distributed transactions.

- Implicit Transaction Enlistment Using TransactionScope

- Explicit Transaction Enlistment Using CommittableTransaction.

- Local Transaction Support for Older Databases

**See Also:**

- For applications connecting to a pre-Oracle Database 11g release 1 (11.1) instance, refer to "Local Transaction Support for Older Databases". This section describes how ODP.NET behavior can be controlled using the "Promotable Transaction" setting.

- ODP.NET Core does not support distributed transactions

#### Implicit Transaction Enlistment Using TransactionScope

The `TransactionScope` class provides a mechanism to write transactional applications where the applications do not need to explicitly enlist in transactions.To accomplish this, the application uses the `TransactionScope` object to define the transactional code. Connections created within this transactional scope will enlist in a local transaction that can be promoted to a distributed transaction.

**Note:**

If the first connection is opened to a pre-Oracle Database 11g release 1 (11.1) instance, then the connection enlists as a distributed transaction, by default.

You can optionally create the transaction as a local transaction by using the procedure described in "Local Transaction Support for Older Databases". However, these transactions cannot be promoted to distributed transactions.

Note that the application must call the `Complete` method on the `TransactionScope` object to commit the changes. Otherwise, the transaction is aborted by default.

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using System.Data;
    using System.Data.Common;
    using System.Transactions;

    class psfTxnScope
    {
      static void Main()
      {
        int retVal = 0;
        string providerName = "Oracle.DataAccess.Client";
        string constr =
               @"User Id=scott;Password=tiger;Data Source=oracle;enlist=true";

        // Get the provider factory.
        DbProviderFactory factory = DbProviderFactories.GetFactory(providerName);

        try
        {
          // Create a TransactionScope object, (It will start an ambient
          // transaction automatically).
          using (TransactionScope scope = new TransactionScope())
          {
            // Create first connection object.
            using (DbConnection conn1 = factory.CreateConnection())
            {
              // Set connection string and open the connection. this connection
              // will be automatically enlisted in a promotable local transaction.
              conn1.ConnectionString = constr;
              conn1.Open();

              // Create a command to execute the sql statement.
              DbCommand  cmd1 = factory.CreateCommand();
              cmd1.Connection = conn1;
              cmd1.CommandText = @"insert into emp (empno, ename, job) values
                                                         (1234, 'emp1', 'dev1')";

              // Execute the SQL statement to insert one row in DB.
              retVal = cmd1.ExecuteNonQuery();
              Console.WriteLine("Rows to be affected by cmd1: {0}", retVal);

              // Close the connection and dispose the command object.
              conn1.Close();
              conn1.Dispose();
              cmd1.Dispose();
            }

            // The Complete method commits the transaction. If an exception has
            // been thrown or Complete is not called then the transaction is
            // rolled back.
            scope.Complete();
          }
        }
        catch (Exception ex)
        {
          Console.WriteLine(ex.Message);
          Console.WriteLine(ex.StackTrace);
        }
      }
    }

#### Explicit Transaction Enlistment Using CommittableTransaction

The instantiation of the `CommittableTransaction` object and the `EnlistTransaction` method provides an explicit way to create and enlist in a transaction. Note that the application must call `Commit` or `Rollback` on the `CommittableTransaction` object.

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using System.Data;
    using System.Data.Common;
    using System.Transactions;

    class psfEnlistTransaction
    {
      static void Main()
      {
        int retVal = 0;
        string providerName = "Oracle.DataAccess.Client";
        string constr =
               @"User Id=scott;Password=tiger;Data Source=oracle;enlist=dynamic";

        // Get the provider factory.
        DbProviderFactory factory = DbProviderFactories.GetFactory(providerName);

        try
        {
          // Create a committable transaction object.
          CommittableTransaction cmtTx = new CommittableTransaction();

          // Open a connection to the DB.
          DbConnection conn1 = factory.CreateConnection();
          conn1.ConnectionString = constr;
          conn1.Open();

          // enlist the connection with the commitable transaction.
          conn1.EnlistTransaction(cmtTx);

          // Create a command to execute the sql statement.
          DbCommand cmd1 = factory.CreateCommand();
          cmd1.Connection = conn1;
          cmd1.CommandText = @"insert into emp (empno, ename, job) values
                                                         (1234, 'emp1', 'dev1')";

          // Execute the SQL statement to insert one row in DB.
          retVal = cmd1.ExecuteNonQuery();
          Console.WriteLine("Rows to be affected by cmd1: {0}", retVal);

          // commit/rollback the transaction.
          cmtTx.Commit();   // commits the txn.
          //cmtTx.Rollback(); // rolls back the txn.

          // close and dispose the connection
          conn1.Close();
          conn1.Dispose();
          cmd1.Dispose();
        }
        catch (Exception ex)
        {
          Console.WriteLine(ex.Message);
          Console.WriteLine(ex.StackTrace);
        }
      }
    }

**See Also:**

"[EnlistTransaction](ConnectionEnlistTransaction.md)"

#### Local Transaction Support for Older Databases

If the first connection in a `TransactionScope` is opened to a pre-Oracle Database 11g release 1 (11.1) instance, then the connection creates a distributed transaction, by default. You can optionally have the first connection create a local transaction by using the procedure described in this section.

To create local transactions in a `System.Transactions` scope, either the `PromotableTransaction` setting in the registry, machine/Web/application configuration file, or the `"Promotable Transaction"` connection string attribute must be set to `"local"`.

If `"local"` is specified, the first connection opened in the `TransactionScope` uses a local transaction. If any subsequent connections are opened within the same `TransactionScope`, an exception is thrown. If there are connections already opened in the `TransactionScope`, and an `OracleConnection` with `"Promotable Transaction=local"` attempts to open within the same `TransactionScope`, an exception is thrown.

If `"promotable"` is specified, the first and all subsequent connections opened in the same `TransactionScope` enlist in the same distributed transaction.

If both the registry and the connection string attribute are used and set to different values, the connection string attribute overrides the registry entry value. If neither are set, `"promotable"` is used. This is the default value and is equivalent to previous versions of ODP.NET which only supported distributed transactions.

The registry entry for a particular version of ODP.NET applies for all applications using that version of ODP.NET.

### Parameter Binding

When the `DbType` property of an `OracleParameter` object is set, the `OracleDbType` property of the `OracleParameter` object changes accordingly, or vice versa. The parameter set last prevails.An application can bind the data and have ODP.NET infer both the `DbType` and `OracleDbType` properties from the .NET type of the parameter value.ODP.NET allows applications to obtain an output parameter as either a .NET Framework type or an ODP.NET type. The application can specify which type to return for an output parameter by setting the `DbType` property of the output parameter (.NET type) or the `OracleDbType` property (ODP.NET type) of the `OracleParameter` object. For example, if the output parameter is set as a `DbType.String` type by setting the `DbType` property, the output data is returned as a .NET String type. On the other hand, if the parameter is set as an `OracleDbType.Char` type by setting the `OracleDbType` property, the output data is returned as an `OracleString` type. If both `DbType` and `OracleDbType` properties are set before the command execution, the last setting takes affect.

ODP.NET populates `InputOutput`, `Output`, and `ReturnValue` parameters with the Oracle data, through the execution of the following `OracleCommand` methods:

- `ExecuteReader`

- `ExecuteNonQuery`

- `ExecuteScalar`

An application should not bind a value for output parameters; it is the responsibility of ODP.NET to create the value object and populate the `OracleParameter` `Value` property with the object.

When binding by position (default) to a function, ODP.NET expects the return value to be bound first, before any other parameters.

This section describes the following:

- OracleDbType Enumeration Type

- Inference of DbType, OracleDbType, and .NET Types

- PL/SQL Associative Array Binding

- Array Binding

**See Also:**

"[OracleDbType Enumeration](OracleDbTypeEnumerationType.md)"

#### Command Timeouts

The `OracleCommand` `CommandTimeout` property limits how long a command is allowed to execute before terminating with an exception. This setting prevents long running commands from consuming excessive resources or from blocking other necessary operations from occurring.

The database server can be interrupted via either TCP/IP urgent data or normal TCP/IP data, called out of band (OOB) or in band data, respectively. Windows-based database servers only support in band breaks, whereas all other (predominantly UNIX-based) database servers can support OOB or in band breaks.

ODP.NET, Managed Driver uses OOB breaks by default with database servers that support it. For certain network topologies, the routers or firewalls involved in the route to the database may have been configured to drop urgent data or in band the data. If the routers or firewalls can not be changed to handle urgent data appropriately, then the ODP.NET, Managed Driver can be configured to utilize in band breaks by setting the .NET configuration parameter `Disable_Oob` to `on`.

**See Also:**

[settings section](InstallManagedConfig.md) in the [Oracle Data Provider for .NET, Managed Driver Configuration](InstallManagedConfig.md) section for more information.

#### OracleDbType Enumeration Type

`OracleDbType` enumerated values are used to explicitly specify the `OracleDbType` value of an `OracleParameter` object.

Table 3-7 lists all the `OracleDbType` enumeration values with a description of each enumerated value.

Table 3-7 OracleDbType Enumeration Values

| Member Name    | Description                                                                                               |
|:---------------|:----------------------------------------------------------------------------------------------------------|
| `Array`        | Oracle Collection (`VArray` or Nested Table)<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core |
| `BFile`        | Oracle `BFILE` type                                                                                       |
| `BinaryFloat`  | Oracle `BINARY_FLOAT` type                                                                                |
| `BinaryDouble` | Oracle `BINARY_DOUBLE` type                                                                               |
| `Blob`         | Oracle `BLOB` type                                                                                        |
| `Boolean`      | Oracle `BOOLEAN` type                                                                                     |
| `Byte`         | `byte` type                                                                                               |
| `Char`         | Oracle `CHAR` type                                                                                        |
| `Clob`         | Oracle `CLOB` type                                                                                        |
| `Date`         | Oracle `DATE` type                                                                                        |
| `Decimal`      | Oracle `NUMBER` type                                                                                      |
| `Double`       | 8-byte `FLOAT` type                                                                                       |
| `Int16`        | 2-byte `INTEGER` type                                                                                     |
| `Int32`        | 4-byte `INTEGER` type                                                                                     |
| `Int64`        | 8-byte `INTEGER` type                                                                                     |
| `IntervalDS`   | Oracle `INTERVAL` `DAY` `TO` `SECOND` type                                                                |
| `IntervalYM`   | Oracle `INTERVAL` `YEAR` `TO` `MONTH` type                                                                |
| `Long`         | Oracle `LONG` type                                                                                        |
| `LongRaw`      | Oracle `LONG` `RAW` type                                                                                  |
| `NChar`        | Oracle `NCHAR` type                                                                                       |
| `Object`       | Oracle Object type<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                           |
| `NClob`        | Oracle `NCLOB` type                                                                                       |
| `NVarchar2`    | Oracle `NVARCHAR2` type                                                                                   |
| `Raw`          | Oracle `RAW` type                                                                                         |
| `Ref`          | Oracle `REF` type<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                            |
| `RefCursor`    | Oracle `REF` `CURSOR` type                                                                                |
| `Single`       | 4-byte `FLOAT` type                                                                                       |
| `TimeStamp`    | Oracle `TIMESTAMP` type                                                                                   |
| `TimeStampLTZ` | Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` type                                                      |
| `TimeStampTZ`  | Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` type                                                              |
| `Varchar2`     | Oracle `VARCHAR2` type                                                                                    |
| `XmlType`      | Oracle `XMLType` type                                                                                     |

**Note:**

PL/SQL `LONG, LONG RAW, RAW,` and `VARCHAR` data types can be bound with a size up to 32512 bytes.

#### Inference of DbType, OracleDbType, and .NET Types

This section explains the inference from the `System.Data.DbType`, `OracleDbType`, and `Value` properties in the `OracleParameter` class.

In the `OracleParameter` class, `DbType`, `OracleDbType`, and `Value` properties are linked. Specifying the value of any of these properties infers the value of one or more of the other properties.

##### Inference of DbType from OracleDbType

In the `OracleParameter` class, specifying the value of `OracleDbType` infers the value of `DbType` as shown in Table 3-8.

Table 3-8 Inference of System.Data.DbType from OracleDbType

| OracleDbType   | System.Data.DbType  |
|:---------------|:--------------------|
| `Array`        | `Object`            |
| `BFile`        | `Object`            |
| `Blob`         | `Object`            |
| `BinaryFloat`  | `Single`            |
| `BinaryDouble` | `Double`            |
| `Boolean`      | `Boolean`           |
| `Byte`         | `Byte`              |
| `Char`         | `StringFixedLength` |
| `Clob`         | `Object`            |
| `Date`         | `Date`              |
| `Decimal`      | `Decimal`           |
| `Double`       | `Double`            |
| `Int16`        | `Int16`             |
| `Int32`        | `Int32`             |
| `Int64`        | `Int64`             |
| `IntervalDS`   | `Object`            |
| `IntervalYM`   | `Int64`             |
| `Long`         | `String`            |
| `LongRaw`      | `Binary`            |
| `NChar`        | `StringFixedLength` |
| `NClob`        | `Object`            |
| `NVarchar2`    | `String`            |
| `Object`       | `Object`            |
| `Raw`          | `Binary`            |
| `Ref`          | `Object`            |
| `RefCursor`    | `Object`            |
| `Single`       | `Single`            |
| `TimeStamp`    | `DateTime`          |
| `TimeStampLTZ` | `DateTime`          |
| `TimeStampTZ`  | `DateTime`          |
| `Varchar2`     | `String`            |
| `XmlType`      | `String`            |

##### Inference of OracleDbType from DbType

In the `OracleParameter` class, specifying the value of `DbType` infers the value of `OracleDbType` as shown in Table 3-9.

Table 3-9 Inference of OracleDbType from DbType

| System.Data.DbType  | OracleDbType  |
|:--------------------|:--------------|
| `Binary`            | `Raw`         |
| `Boolean`           | `Boolean`     |
| `Byte`              | `Byte`        |
| `Currency`          | Not Supported |
| `Date`              | `Date`        |
| `DateTime`          | `TimeStamp`   |
| `Decimal`           | `Decimal`     |
| `Double`            | `Double`      |
| `Guid`              | Not Supported |
| `Int16`             | `Int16`       |
| `Int32`             | `Int32`       |
| `Int64`             | `Int64 `      |
| `Object`            | `Object`      |
| `Sbyte`             | Not Supported |
| `Single`            | `Single`      |
| `String`            | `Varchar2`    |
| `StringFixedLength` | `Char`        |
| `Time`              | `TimeStamp`   |
| `UInt16`            | Not Supported |
| `UInt32`            | Not Supported |
| `Uint64`            | Not Supported |
| `VarNumeric`        | Not Supported |

##### Inference of DbType and OracleDbType from Value

In the `OracleParameter` class, `Value` is an object type that can be of any .NET Framework data type or ODP.NET type. If the `OracleDbType` and `DbType` properties of the `OracleParameter` class are not specified, the `OracleDbType` property is inferred from the type of the `Value` property.

Table 3-10 shows the inference of `DbType` and `OracleDbType` properties from the `Value` property when the type of `Value` is one of the .NET Framework data types.

Table 3-10 Inference of DbType and OracleDbType from Value (.NET Datatypes)

| Value (.NET Datatypes) | System.Data.DbType | OracleDbType |
|:-----------------------|:-------------------|:-------------|
| `Boolean`              | `Boolean`          | `Boolean`    |
| `Byte`                 | `Byte`             | `Byte`       |
| `Byte[]`               | `Binary`           | `Raw`        |
| `Char / Char []`       | `String`           | `Varchar2`   |
| `DateTime`             | `DateTime`         | `TimeStamp`  |
| `Decimal`              | `Decimal`          | `Decimal`    |
| `Double`               | `Double`           | `Double`     |
| `Float`                | `Single`           | `Single`     |
| `Int16`                | `Int16`            | `Int16`      |
| `Int32`                | `Int32`            | `Int32`      |
| `Int64`                | `Int64`            | `Int64`      |
| `IOracleCustomType`    | `Object`           | `Object`     |
| `Single`               | `Single`           | `Single`     |
| `String`               | `String`           | `Varchar2`   |
| `TimeSpan`             | Object             | `IntervalDS` |

**Note:**

Using other .NET Framework data types as values for the `OracleParameter` class without specifying either the `DbType` or the `OracleDbType` properties raises an exception because inferring `DbType` and `OracleDbType` properties from other .NET Framework data types is not supported.

Table 3-11 shows the inference of `DbType` and `OracleDbType` properties from the `Value` property when type of `Value` is one of `Oracle.DataAccess.Types`.

Table 3-11 Inference of DbType and OracleDbType from Value (ODP.NET Types)

| Value (Oracle.DataAccess.Types) | System.Data.DbType | OracleDbType   |
|:--------------------------------|:-------------------|:---------------|
| `OracleBFile`                   | `Object`           | `BFile`        |
| `OracleBinary`                  | `Binary`           | `Raw`          |
| `OracleBlob`                    | `Object`           | `Blob`         |
| `OracleBoolean`                 | `Boolean`          | `Boolean`      |
| `OracleClob`                    | `Object`           | `Clob`         |
| `OracleDate`                    | `Date`             | `Date`         |
| `OracleDecimal`                 | `Decimal`          | `Decimal`      |
| `OracleIntervalDS`              | `Object`           | `IntervalDS`   |
| `OracleIntervalYM`              | `Int64`            | `IntervalYM`   |
| `OracleRef`                     | `Object`           | `Ref`          |
| `OracleRefCursor`               | `Object`           | `RefCursor`    |
| `OracleString`                  | `String`           | `Varchar2`     |
| `OracleTimeStamp`               | `DateTime`         | `TimeStamp`    |
| `OracleTimeStampLTZ`            | `DateTime`         | `TimeStampLTZ` |
| `OracleTimeStampTZ`             | `DateTime`         | `TimeStampTZ`  |
| `OracleXmlType`                 | `String`           | `XmlType`      |

#### PL/SQL Associative Array Binding

ODP.NET supports PL/SQL Associative Arrays (formerly known as PL/SQL Index-By Tables) binding.

An application can bind an `OracleParameter` object, as a PL/SQL Associative Array, to a PL/SQL stored procedure. The following `OracleParameter` properties are used for this feature:

- `CollectionType`

  This property must be set to `OracleCollectionType.PLSQLAssociativeArray` to bind a PL/SQL Associative Array.

- `ArrayBindSize`

  This property is ignored for the fixed-length element types (such as `Int32`).

  For variable-length element types (such as `Varchar2`), each element in the `ArrayBindSize` property specifies the size of the corresponding element in the `Value` property.

  For `Output` parameters, `InputOutput` parameters, and return values, this property must be set for variable-length variables.

  If the database server supports up to `32 KB VARCHAR2`, then each ODP.NET array element can store up to `32 KB` characters or binary data. If the database server supports up to `4 KB VARCHAR2`, then each ODP.NET array element can store up to `4 KB` characters or `2 KB` binary data.

- `ArrayBindStatus`

  This property specifies the execution status of each element in the `OracleParameter.Value` property.

- `Size`

  This property specifies the maximum number of elements to be bound in the PL/SQL Associative Array.

- `Value`

  This property must be set to an array of values, `null`, or the `DBNull.Value` property.

ODP.NET supports binding parameters of PL/SQL Associative Arrays which contain the following data types.

- `BINARY_FLOAT`

- `CHAR`

- `DATE`

- `NCHAR`

- `NUMBER`

- `NVARCHAR2`

- `RAW`

- `ROWID`

- `UROWID`

- `VARCHAR2`

Using unsupported data types with associative arrays can cause an ORA-600 error.

##### Example of PL/SQL Associative Arrays

This example binds three `OracleParameter` objects as PL/SQL Associative Arrays: `Param1` as an `In` parameter, `Param2` as an `InputOutput` parameter, and `Param3` as an `Output` parameter.

PL/SQL Package: MYPACK

    /* Setup the tables and required PL/SQL:

       connect scott/tiger@oracle
       CREATE TABLE T1(COL1 number, COL2 varchar2(20));

       CREATE or replace PACKAGE MYPACK AS
         TYPE AssocArrayVarchar2_t is table of VARCHAR(20) index by BINARY_INTEGER;
         PROCEDURE TestVarchar2(
           Param1 IN     AssocArrayVarchar2_t,
           Param2 IN OUT AssocArrayVarchar2_t,
           Param3    OUT AssocArrayVarchar2_t);
         END MYPACK;
    /

       CREATE or REPLACE package body MYPACK as
         PROCEDURE TestVarchar2(
           Param1 IN     AssocArrayVarchar2_t,
           Param2 IN OUT AssocArrayVarchar2_t,
           Param3    OUT AssocArrayVarchar2_t)
         IS
         i integer;
         BEGIN
           -- copy a few elements from Param2 to Param1\n
           Param3(1) := Param2(1);
           Param3(2) := NULL;
           Param3(3) := Param2(3);
           -- copy all elements from Param1 to Param2\n
           Param2(1) := Param1(1);
           Param2(2) := Param1(2);
           Param2(3) := Param1(3);
           -- insert some values to db\n
           FOR i IN 1..3 LOOP
             insert into T1 values(i,Param2(i));
           END LOOP;
         END TestVarchar2;
       END MYPACK;
    /
     */

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class AssociativeArraySample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle";
        con.Open();
        Console.WriteLine("Connected to Oracle" + con.ServerVersion);

        OracleCommand cmd = new OracleCommand(
          "begin MyPack.TestVarchar2(:1, :2, :3); end;", con);

        OracleParameter Param1 = cmd.Parameters.Add("1", OracleDbType.Varchar2);
        OracleParameter Param2 = cmd.Parameters.Add("2", OracleDbType.Varchar2);
        OracleParameter Param3 = cmd.Parameters.Add("3", OracleDbType.Varchar2);

        Param1.Direction = ParameterDirection.Input;
        Param2.Direction = ParameterDirection.InputOutput;
        Param3.Direction = ParameterDirection.Output;

        // Specify that we are binding PL/SQL Associative Array
        Param1.CollectionType = OracleCollectionType.PLSQLAssociativeArray;
        Param2.CollectionType = OracleCollectionType.PLSQLAssociativeArray;
        Param3.CollectionType = OracleCollectionType.PLSQLAssociativeArray;

        // Setup the values for PL/SQL Associative Array
        Param1.Value = new string[3] {
          "First Element", "Second Element ", "Third Element "
        };
        Param2.Value = new string[3] {
          "First Element", "Second Element ", "Third Element "
        };
        Param3.Value = null;

        // Specify the maximum number of elements in the PL/SQL Associative Array
        Param1.Size = 3;
        Param2.Size = 3;
        Param3.Size = 3;

        // Setup the ArrayBindSize for Param1
        Param1.ArrayBindSize = new int[3] { 13, 14, 13 };

        // Setup the ArrayBindStatus for Param1
        Param1.ArrayBindStatus = new OracleParameterStatus[3] {
          OracleParameterStatus.Success, OracleParameterStatus.Success,
          OracleParameterStatus.Success};

        // Setup the ArrayBindSize for Param2
        Param2.ArrayBindSize = new int[3] { 20, 20, 20 };

        // Setup the ArrayBindSize for Param3
        Param3.ArrayBindSize = new int[3] { 20, 20, 20 };

        // execute the cmd
        cmd.ExecuteNonQuery();

        //print out the parameter's values
        Console.WriteLine("parameter values after executing the PL/SQL block");
        for (int i = 0; i < 3; i++)
          Console.WriteLine("Param2[{0}] = {1} ", i,
            (cmd.Parameters[1].Value as Array).GetValue(i));

        for (int i = 0; i < 3; i++)
          Console.WriteLine("Param3[{0}] = {1} ", i,
            (cmd.Parameters[2].Value as Array).GetValue(i));

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
        Console.WriteLine("Disconnected");
      }
    }

#### Array Binding

The array bind feature enables applications to bind arrays of a type using the `OracleParameter` class. Using the array bind feature, an application can insert multiple rows into a table in a single database round-trip.

The following example inserts three rows into the `Dept` table with a single database round-trip. The `OracleCommand` `ArrayBindCount` property defines the number of elements of the array to use when executing the statement.

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class ArrayBindSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();
        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle;";
        con.Open();
        Console.WriteLine("Connected successfully");

        int[] myArrayDeptNo = new int[3] { 10, 20, 30 };
        OracleCommand cmd = new OracleCommand();

        // Set the command text on an OracleCommand object
        cmd.CommandText = "insert into dept(deptno) values (:deptno)";
        cmd.Connection = con;

        // Set the ArrayBindCount to indicate the number of values
        cmd.ArrayBindCount = 3;

        // Create a parameter for the array operations
        OracleParameter prm = new OracleParameter("deptno", OracleDbType.Int32);

        prm.Direction = ParameterDirection.Input;
        prm.Value = myArrayDeptNo;

        // Add the parameter to the parameter collection
        cmd.Parameters.Add(prm);

        // Execute the command
        cmd.ExecuteNonQuery();
        Console.WriteLine("Insert Completed Successfully");

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
      }
    }

**See Also:**

"[Value](ParameterValue.md)" for more information

##### OracleParameter Array Bind Properties

The `OracleParameter` class provides two properties for granular control when using the array bind feature:

- `ArrayBindSize`

  The `ArrayBindSize` property is an array of integers specifying the maximum size for each corresponding value in an array. The `ArrayBindSize` property is similar to the `Size` property of an `OracleParameter` object, except the `ArrayBindSize` property specifies the size for each value in an array.

  Before the execution, the application must populate the `ArrayBindSize` property; after the execution, ODP.NET populates it.

  The `ArrayBindSize` property is used only for parameter types that have variable length such as `Clob`, `Blob`, and `Varchar2`. The size is represented in bytes for binary data types, and characters for the Unicode string types. The count for string types does not include the terminating character. The size is inferred from the actual size of the value, if it is not explicitly set. For an output parameter, the size of each value is set by ODP.NET. The `ArrayBindSize` property is ignored for fixed-length data types.

  The maximum `ArrayBindSize` size is `2 GB` for both character and binary data.

- `ArrayBindStatus`

  The `ArrayBindStatus` property is an array of `OracleParameterStatus` values that specify the status of each corresponding value in an array for a parameter. This property is similar to the `Status` property of the `OracleParameter` object, except that the `ArrayBindStatus` property specifies the status for each array value.

  Before the execution, the application must populate the `ArrayBindStatus` property. After the execution, ODP.NET populates the property. Before the execution, an application using the `ArrayBindStatus` property can specify a `NULL` value for the corresponding element in the array for a parameter. After the execution, ODP.NET populates the `ArrayBindStatus` property, indicating whether the corresponding element in the array has a `null` value, or if data truncation occurred when the value was fetched.

##### Error Handling for Array Binding

If an error occurs during an array bind execution, it can be difficult to determine which element in the `Value` property caused the error. ODP.NET provides a way to determine the row where the error occurred, making it easier to find the element in the row that caused the error.

When an `OracleException` object is thrown during an array bind execution, the `OracleErrorCollection` object contains one or more `OracleError` objects. Each of these `OracleError` objects represents an individual error that occurred during the execution, and contains a provider-specific property, `ArrayBindIndex`, which indicates the row number at which the error occurred.

The following example demonstrates error handling for array binding:

    /* Database Setup
    connect scott/tiger@oracle
    drop table depttest;
    create table depttest(deptno number(2));
    */

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class ArrayBindExceptionSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();
        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle;";
        con.Open();

        OracleCommand cmd = new OracleCommand();

        // Start a transaction
        OracleTransaction txn = con.BeginTransaction(IsolationLevel.ReadCommitted);

        try
        {
          int[] myArrayDeptNo = new int[3] { 10, 200000, 30 };
          // int[] myArrayDeptNo = new int[3]{ 10,20,30};

          // Set the command text on an OracleCommand object
          cmd.CommandText = "insert into depttest(deptno) values (:deptno)";
          cmd.Connection = con;

          // Set the ArrayBindCount to indicate the number of values
          cmd.ArrayBindCount = 3;

          // Create a parameter for the array operations
          OracleParameter prm = new OracleParameter("deptno", OracleDbType.Int32);

          prm.Direction = ParameterDirection.Input;
          prm.Value = myArrayDeptNo;

          // Add the parameter to the parameter collection
          cmd.Parameters.Add(prm);

          // Execute the command
          cmd.ExecuteNonQuery();
        }
        catch (OracleException e)
        {
          Console.WriteLine("OracleException {0} occured", e.Message);
          if (e.Number == 24381)
            for (int i = 0; i < e.Errors.Count; i++)
              Console.WriteLine("Array Bind Error {0} occured at Row Number {1}",
                e.Errors[i].Message, e.Errors[i].ArrayBindIndex);

          txn.Commit();
        }
        cmd.Parameters.Clear();
        cmd.CommandText = "select count(*) from depttest";

        decimal rows = (decimal)cmd.ExecuteScalar();

        Console.WriteLine("{0} row have been inserted", rows);
        con.Close();
        con.Dispose();
      }
    }

**See Also:**

"[ArrayBindIndex](ArrayBindIndex.md)" for more information

##### OracleParameterStatus Enumeration Types

Table 3-12 lists `OracleParameterStatus` enumeration values.

Table 3-12 OracleParameterStatus Members

| Member Names  | Description                                                                                                                                                                            |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Success`     | For input parameters, indicates that the input value has been assigned to the column.<br>For output parameters, indicates that the provider assigned an intact value to the parameter. |
| `NullFetched` | Indicates that a `NULL` value has been fetched from a column or an `OUT` parameter.                                                                                                    |
| `NullInsert`  | Indicates that a `NULL` value is to be inserted into a column.                                                                                                                         |
| `Truncation`  | Indicates that truncation has occurred when fetching the data from the column.                                                                                                         |

### Batch Processing

The `OracleDataAdapter` `UpdateBatchSize` property enables batch processing when the `OracleDataAdapter.Update` method is called. `UpdateBatchSize` is a numeric property that indicates how many DataSet rows to update the Oracle database for each round-trip.

This enables the developer to reduce the number of round-trips to the database.

**See Also:**

"[UpdateBatchSize](DataAdapterUpdateBatchSize.md)"

### Statement Caching

Statement caching eliminates the need to parse each SQL or PL/SQL statement before execution by caching server cursors created during the initial statement execution. Subsequent executions of the same statement can reuse the parsed information from the cursor, and then execute the statement without reparsing, for better performance.

In order to see performance gains from statement caching, Oracle recommends caching only those statements that will be repeatedly executed. Furthermore, SQL or PL/SQL statements should use parameters rather than literal values. Doing so takes full advantage of statement caching, because parsed information from parameterized statements can be reused even if the parameter values change in subsequent executions. However, if the literal values in the statements are different, the parsed information cannot be reused unless the subsequent statements also have the same literal values.

#### Statement Caching Connection String Attributes

The following connection string attributes control the behavior of the ODP.NET statement caching feature:

- `Statement` `Cache` `Size`

  This attribute enables or disables ODP.NET statement caching. By default, this attribute is set to `0` (disabled). If it is set to a value greater than `0`, ODP.NET statement caching is enabled and the value specifies the maximum number of statements that can be cached for a connection. Once a connection has cached up to the specified maximum cache size, the least recently used cursor is freed to make room to cache the newly created cursor.

  If self tuning is enabled, then statement caching is enabled as well. The `Statement Cache Size` is configured automatically in such cases.

- `Statement` `Cache` `Purge`

  This attribute provides a way for connections to purge all statements that are cached when a connection is closed or placed back into the connection pool. By default, this attribute is set to `false`, which means that cursors are not freed when connections are placed back into the pool.

#### Enabling Statement Caching through the Registry

To enable statement caching by default for all ODP.NET applications running in a system, without changing the application, set the registry key of `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\ODP.NET\``Assembly_Version` `\StatementCacheSize` to a value greater than `0`. This value specifies the number of cursors that are to be cached on the server.

The default value for the system can be overridden at the connection pool level. The `Statement` `Cache` `Size` attribute can be set to a different size than the registry value or it can be turned off. The `Statement` `Cache` `Size` can also be configured through an XML configuration file.

**See Also:**

[Configuring Oracle Data Provider for .NET](InstallConfig.md) for more details.

#### Statement Caching Methods and Properties

The following property and method are relevant only when statement caching is enabled:

- `OracleCommand.AddToStatementCache` property

  If statement caching is enabled, having this property set to `true` (default) adds statements to the cache when they are executed. If statement caching is disabled or if this property is set to `false`, the executed statement is not cached.

- `OracleConnection.PurgeStatementCache` method

  This method purges all the cached statements by closing all open cursors on the database that are associated with the particular connection. Note that statement caching remains enabled after this call.

#### Connections and Statement Caching

Statement caching is managed separately for each connection. Therefore, executing the same statement on different connections requires parsing once for each connection and caching a separate cursor for each connection.

#### Pooling and Statement Caching

Pooling and statement caching can be used in conjunction. If connection pooling is enabled and the `Statement` `Cache` `Purge` attribute is set to `false`, statements executed on each separate connection are cached throughout the lifetime of the pooled connection.

If the `Statement` `Cache` `Purge` attribute is set to `true`, all the cached cursors are freed when the connection is placed back into the pool. When connection pooling is disabled, cursors are cached during the lifetime of the connection, but the cursors are closed when the `OracleConnection` object is closed or disposed of.

### Self-Tuning

ODP.NET applications can be self-tuned for performance optimization. ODP.NET dynamically monitors application queries during runtime.

**Note:**

Self-tuning for applications does not take place if the `Pooling` connection string attribute is set to `false`. Self-tuning is also not supported inside .NET stored procedures.

The statement cache size ([StatementCacheSize](ConnectionStatementCacheSize.md)) is tuned automatically by monitoring the statements that are executed by the application. The following sections discuss self-tuning in applications:

- Self-Tuning Statement Caching

- Enabling or Disabling Self-Tuning for Applications

- Tracing Optimization Changes

#### Self-Tuning Statement Caching

Statement caching helps improve performance by eliminating the need to re-parse each SQL or PL/SQL statement before execution.

If self-tuning is enabled for an application, then ODP.NET continuously monitors application behavior in order to determine the optimum value for the statement cache size. Any statement cache size value specified in the connection string, configuration file, or registry is ignored.

When the application first initializes, it uses the default value of statement cache size. As the application executes statements, ODP.NET collects statistics that are used to self-tune the value of statement cache size. Self-tuning of statement cache size results in increased performance.

**Note:**

To take full advantage of statement caching, you should not dynamically generate statements, with different inline values, for every statement execution. Instead, use parameterized commands to minimize the number of unique statements that need to be executed and cached. This is because only one statement needs to be cached for every unique command text, regardless of the parameter values and the number of times that the statement is executed.

The maximum number of statements that can be cached per connection is determined by the `MaxStatementCacheSize` configuration attribute. The `MaxStatementCacheSize` value can be specified in the Windows registry or XML configuration file.

The `MaxStatementCacheSize` setting is useful in limiting the number of cached statements, as well as the number of open cursors. This is because a cached statement equates to a cursor being opened on the server. For this reason, you should not set `MaxStatementCacheSize` to a value that is greater than the database `OPEN_CURSORS` setting.

The following Windows registry key is used to configure the `MaxStatementCacheSize` configuration attribute:

    HKLM\Software\Oracle\ODP.NET\version\MaxStatementCacheSize

The `MaxStatementCacheSize` key is of type `REG_SZ`. It can be set to an integer value between 0 and `System.Int32.MaxValue`.

The following example sets the `MaxStatementCacheSize` property in an ADO.NET 2.0, or above, configuration file:

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <oracle.dataaccess.client>
        <settings>
          <add name="MaxStatementCacheSize" value="300"/>
        </settings>
      </oracle.dataaccess.client>
    </configuration>

If self-tuning is disabled for an application, then the value of statement cache size is determined by the settings in the connection string, configuration file, or the registry. If statement cache size is not specified in any of these sources, then the default value of statement cache size is set to 0. To have ODP.NET configured with the same default settings as previous releases of ODP.NET, disable self-tuning and set the `StatementCacheSize` value to 10.

**See Also:**

"Statement Caching"

#### Enabling or Disabling Self-Tuning for Applications

Self-tuning for ODP.NET applications is enabled by default. An application can enable or disable self-tuning using one of the following methods:

- Self-Tuning Connection String Attribute

  An application can modify the `Self Tuning` connection string attribute to enable or disable self-tuning for a particular connection pool. The default value for` Self Tuning` is `true`.

- Windows Registry

  An application can enable or disable self-tuning for a particular version of ODP.NET by modifying the following registry entry:

      HKLM\Software\Oracle\ODP.NET\version\SelfTuning

  The `SelfTuning` key is of type `REG_SZ`. It can be set to either `1` (enabled) or `0` (disabled).

- Configuration File

  An ODP.NET application can modify the application configuration file (`app.config`) or Web configuration file (`web.config`) to enable or disable self-tuning.

  The following example shows how to enable self-tuning in an ADO.NET 2.0 application configuration file:

      <?xml version="1.0" encoding="utf-8" ?>
      <configuration>
        <oracle.dataaccess.client>
          <settings>
            <add name="SelfTuning" value="1"/>
          </settings>
        </oracle.dataaccess.client>
      </configuration>

  **Note:**

  If the optimal statement cache size is known for an application, then you can disable self-tuning and set `StatementCacheSize` to its optimum value in the registry, configuration file, or the application. If self-tuning is disabled and `StatementCacheSize` is not set at all, then the default value of 0 is used for `StatementCacheSize`.

#### Tracing Optimization Changes

Applications can trace optimization changes made by self-tuning. All changes to `StatementCacheSize` are traced. Errors, if any, are also traced.

The `TraceLevel` used for tracing self-tuning is `64`.

**See Also:**

[Table 2-3](InstallUnmanagedConfig.md) for details on `TraceLevel` values
