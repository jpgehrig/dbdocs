ODP.NET enables applications to run stored procedures with `REF CURSOR` parameters without using explicit binding for these parameters in the .NET code. ODP.NET unmanaged and managed drivers support `REF CURSOR` implicit binding through configuration done in .NET configuration files.

For a read-only result set, such as a `REF CURSOR` using `OracleDataReader`, `REF CURSOR` schema information is retrieved automatically.

For some scenarios, such as when updateable `REF CURSOR`s or Entity Framework is used, developers need to define the` REF CURSOR` schema information so that the application can bind the implicit `REF CURSOR`. Entity Framework applications use implicit `REF CURSOR` binding to instantiate complex types from `REF CURSOR` data. Applications must specify `REF CURSOR` bind and metadata information in the `app.config`, `web.config,` or `machine.config` .NET configuration file.

The attributes supplied in the .NET configuration file are also used when the application requests for schema information from the `OracleDataReader` object that represents a `REF CURSOR`. This means that for `REF CURSOR`s that are created using a `SELECT` from a single table, the application can update that table through the use of `OracleDataAdapter` and `OracleCommandBuilder`.

When using the Entity Framework, function imports can return an implicitly-bound `REF CURSOR`. The `REF CURSOR` can be returned as a collection of complex types or entity types. To return a complex type collection, the .NET configuration file needs to define the `REF CURSOR` bind and metadata information. To return an entity type collection, only the bind information needs to be defined in the .NET configuration file.

This section contains the following topics:

- Specifying REF CURSOR Bind and Metadata Information in the .NET Configuration File

- Sample Configuration File and Application

- Usage Considerations

### Specifying REF CURSOR Bind and Metadata Information in the .NET Configuration File

Specify the `REF CURSOR` information in the `oracle.dataacccess.client` configuration section of the .NET configuration file. Use an `<add>` element for each piece of information. The `add` element uses `name`-`value` attributes to specify `REF CURSOR` information. Use the following format to specify bind information:

    <add name="SchemaName.PackageName.StoredProcedureName.RefCursor.RefCursorParameterPositionOrName"
    value="implicitRefCursor bindinfo='mode=InputOutput|Output|ReturnValue'" />

Use the following format to specify metadata information:

    <add name="SchemaName.PackageName.StoredProcedureName.RefCursorMetaData.RefCursorParameterPositionorName.Column.ColumnOrdinal"
    value="implicitRefCursor metadata=AttributesList" />

Each `REF CURSOR` column needs to have an `add` element defined for it. For example, if you have a `REF CURSOR` returning five columns, then you need to define five `add` elements in the config file.

Each `add` element contains the `name` and `value` attributes. The `value` attribute must begin with the word `implicitRefCursor` followed by the `bindinfo` or `metadata` attribute for specifying bind or metadata information.

The `bindinfo` information is used by ODP.NET for binding `REF CURSOR` parameters. The `metadata` information is used by ODP.NET to associate the schema information with the appropriate `REF CURSOR`. The metadata comprises of an attributes list that includes parameters together with their values.

The `SchemaName`, `PackageName`, and `StoredProcedureName` are case-sensitive. In order to run a stored procedure with implicit `REF CURSOR` binding, the `SchemaName``.``PackageName``.``StoredProcedureName` portion of the `name` attribute must exactly match the name specified in the data dictionary for that stored procedure.

**Note:**

If the application uses implicit `REF CURSOR` binding feature outside of Entity Framework, then the .NET configuration file and `OracleCommand CommandText `do not require the schema name concatenated before the stored procedure name.

If any schema, package, or stored procedure name in the database contains lowercase characters, then it must be enclosed within double quotation marks (`"`) in the config file to preserve the case. Double quotation marks are used within the `name` attribute by using `&quot;` when needed. For example, if the schema name is `HrSchema`, the package name is `HrPackage`, and the stored procedure name is `HrStoredProcedure` in the database, the config file should use the following:

    <add name="&quot;HrSchema&quot;.&quot;HrPackage&quot;.&quot;HrStoredProcedure&quot;.RefCursorMetaData . . . />

By default, Oracle Database stores these names as uppercase characters. ODP.NET assumes default behavior, and converts all names to uppercase characters unless you explicitly preserve the case by using double quotation marks.

**Note:**

The `SchemaName`, `PackageName`, `StoredProcedureName`, or `ParameterName` cannot contain a period ("`.`") in the name. For example, `P.0` is an unacceptable parameter name.

Depending on whether the application uses bind-by-name or bind-by-position, the `RefCursorParameterPositionOrName` portion of the name attribute must be set with the correct parameter position (for bind by position) or parameter name (for bind by name). For functions, the position is 0-based, where the position 0 represents the return value. For procedures, the position is 1-based, as there are no return values for procedures. For example, if a stored procedure accepts five parameters, returning only two `REF CURSOR`s in the third and fifth parameter positions, then the .NET config `REF CURSOR` bind information should contain one entry for position 3 and one entry for position 5.

If bind-by-name is used, the attribute name is used to identify the `REF CURSOR` parameter. The `name` should use the same name and case as the one specified in the data dictionary for that stored procedure.

For `bindinfo`, the `mode` specifies the parameter direction of the parameter. The mode must be either `InputOutput`, `Output`, or `ReturnValue`.

**Note:**

Implicit `REF CURSOR` binding for an input `REF CURSOR` parameter is not supported.

An exception is thrown at runtime if the .NET configuration file contains an entry for a `REF CURSOR` whose `mode` is set to `Input`.

For `metadata`, The `AttributesList` contains the list of parameters. Table 3-18 describes the parameters that can be included in the `AttributesList`.

Example 3-5 shows a sample `add` element that uses `bindinfo`. Here, the schema name is `SCOTT` and the stored procedure name is `TESTPROC`. The parameter name is `parameter1`. The mode is `output`.

Example 3-6 shows a sample `add` element that uses `metadata`.

Table 3-18 Allowed Parameters in Attributes List

| Name               | Type                                    | Required/Optional for Entity Framework | Description                                                                                                                                                                                                     |
|:-------------------|:----------------------------------------|:---------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ColumnName`       | `System.String`                         | Required                               | The name of the column.                                                                                                                                                                                         |
| `ProviderType`     | `Oracle.DataAccess.Client.OracleDbType` | Required                               | The database column type (`OracleDbType`) of the column                                                                                                                                                         |
| `NativeDataType`   | `System.String`                         | Required                               | The Oracle type. For example, `NCLOB`.                                                                                                                                                                          |
| `BaseColumnName`   | `System.String`                         | Optional                               | The name of the column in the database if an alias is used for the column.                                                                                                                                      |
| `BaseSchemaName`   | `System.String`                         | Optional                               | The name of the schema in the database that contains the column.                                                                                                                                                |
| `BaseTableName`    | `System.String`                         | Optional                               | The name of the table or view in the database that contains the column.                                                                                                                                         |
| `ColumnSize`       | `System.Int64`                          | Optional                               | The maximum possible length of a value in the column                                                                                                                                                            |
| `NumericPrecision` | `System.Int16`                          | Optional                               | The maximum precision of the column, if the column is a numeric data type.                                                                                                                                      |
| `NumericScale`     | `System.Int16`                          | Optional                               | The maximum scale of the column, if the column is a numeric data type.                                                                                                                                          |
| `IsUnique`         | `System.Boolean`                        | Optional                               | Indicates whether or not the column is unique.                                                                                                                                                                  |
| `IsKey`            | `System.Boolean`                        | Optional                               | Indicates whether or not the column is a key column. For a table to be updated with the `REF CURSOR` information, at least one of the columns in the `REF CURSOR` metadata should have this value set to `true` |
| `IsRowID`          | `System.Boolean`                        | Optional                               | `true` if the column is a `ROWID`, otherwise `false`.                                                                                                                                                           |
| `DataType`         | `System.RuntimeType`                    | Optional                               | Maps to the common language runtime type.                                                                                                                                                                       |
| `AllowDBNull`      | `System.Boolean`                        | Optional                               | `true` if null values are allowed, otherwise `false`                                                                                                                                                            |
| `IsAliased`        | `System.Boolean`                        | Optional                               | `true` if the column is an alias; otherwise `false`.                                                                                                                                                            |
| `IsByteSemantic`   | `System.Boolean`                        | Optional                               | `IsByteSemantic` is:<br>• `true` if the `ColumnSize` value uses bytes semantics<br>• `false` if `ColumnSize` uses character semantics                                                                           |
| `IsExpression`     | `System.Boolean`                        | Optional                               | `true` if the column is an expression, else `false`.                                                                                                                                                            |
| `IsHidden`         | `System.Boolean`                        | Optional                               | `true` if the column is hidden, else `false`.                                                                                                                                                                   |
| `IsReadOnly`       | `System.Boolean`                        | Optional                               | `true` if the column is read-only, else `false`                                                                                                                                                                 |
| `IsLong`           | `System.Boolean`                        | Optional                               | `true` if the column is of `LONG``, LONG RAW, BLOB, CLOB, `or<br>`BFILE` type, else `false`.                                                                                                                    |
| `UdtTypeName`      | `System.String`                         | Optional                               | The type name of the UDT.                                                                                                                                                                                       |
| `ProviderDBType`   | `System.Data.DbType`                    | Optional                               | `System.Data.DbType`                                                                                                                                                                                            |
| `ObjectName`       | `System.String`                         | Optional                               | Represents the name of the object.                                                                                                                                                                              |

Some of the attributes, listed in Table 3-18, automatically have their values set using the result set's metadata. Developers can override these default values by setting a value explicitly.

You may have to explicitly define some attributes listed as optional for certain operations. For example, updateable `REF CURSOR` requires the developer to define key information.

Example 3-5 Using the add Element with bindinfo

    <add name="SCOTT.TESTPROC.RefCursor.parameter1" value="implicitRefCursor
     bindinfo='mode=Output'" />

Example 3-6 Using the add Element with metadata

    <add name="scott.TestProc.RefCursorMetaData.parameter1.Column.0"
    value="implicitRefCursor metadata='ColumnName=EMPNO;BaseColumnName=EMPNO;
    BaseSchemaName=SCOTT;BaseTableName=EMP;NativeDataType=number;
    ProviderType=Int32;DataType=System.Int32;ColumnSize=4;AllowDBNull=false;
    IsKey=true'" />

### Sample Configuration File and Application

This section builds a sample application to illustrate implicit `REF CURSOR` binding. It contains the following topics:

- Sample Stored Procedure and Function

- Sample Application Configuration File

- Sample Application That Uses the Configuration File

#### Sample Stored Procedure and Function

    CREATE OR REPLACE FUNCTION GETEMP (
      EMPID IN NUMBER) return sys_refcursor is
      emp sys_refcursor;
    BEGIN
      OPEN emp FOR SELECT empno, ename FROM emp where empno = EMPID;
      return emp;
    END;
    /

    CREATE OR REPLACE PROCEDURE "GetEmpAndDept" (
      EMPS OUT sys_refcursor,
      DEPTS OUT sys_refcursor) AS
    BEGIN
      OPEN EMPS for SELECT empno, ename from emp;
      OPEN DEPTS for SELECT deptno, dname from dept;
    END;
    /

#### Sample Application Configuration File

    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <oracle.dataaccess.client>
        <settings>

          <!-- The following is for SCOTT.GETEMP -->
          <add name="SCOTT.GETEMP.RefCursor.0"
               value="implicitRefCursor bindinfo='mode=ReturnValue'" />

          <!-- The following is for SCOTT.GETEMP's REF CURSOR metadata -->
          <add name="SCOTT.GETEMP.RefCursorMetaData.0.Column.0"
               value="implicitRefCursor metadata='ColumnName=EMPNO;
               BaseColumnName=EMPNO;BaseSchemaName=SCOTT;BaseTableName=EMP;
               NativeDataType=number;ProviderType=Int32;ProviderDBType=Int32;
               DataType=System.Int32;ColumnSize=4;NumericPrecision=10;
               NumericScale=3;AllowDBNull=false;IsKey=true'" />

          <add name="SCOTT.GETEMP.RefCursorMetaData.0.Column.1"
               value="implicitRefCursor metadata='ColumnName=ENAME;
               BaseColumnName=ENAME;BaseSchemaName=SCOTT;BaseTableName=EMP;
               NativeDataType=varchar2;ProviderType=Varchar2;
               ProviderDBType=String;DataType=System.String;
               ColumnSize=10;AllowDBNull=true'" />

          <!-- The following is for "SCOTT"."GetEmpAndDept" -->
          <add name="SCOTT.&quot;GetEmpAndDept&quot;.RefCursor.EMPS"
               value="implicitRefCursor bindinfo='mode=Output'" />

          <!-- The following is for SCOTT.GETEMP's EMPS REF CURSOR metadata -->
          <add name="SCOTT.&quot;GetEmpAndDept&quot;
               .RefCursorMetaData.EMPS.Column.0"
               value="implicitRefCursor metadata='ColumnName=EMPNO;
               BaseColumnName=EMPNO;BaseSchemaName=SCOTT;BaseTableName=EMP;
               NativeDataType=number;ProviderType=Int32;ProviderDBType=Int32;
               DataType=System.Int32;ColumnSize=4;NumericPrecision=10;
               NumericScale=3;AllowDBNull=false;IsKey=true'" />

          <add name="SCOTT.&quot;GetEmpAndDept&quot;
               .RefCursorMetaData.EMPS.Column.1"
               value="implicitRefCursor metadata='ColumnName=ENAME;
               BaseColumnName=ENAME;BaseSchemaName=SCOTT;BaseTableName=EMP;
               NativeDataType=varchar2;ProviderType=Varchar2;
               ProviderDBType=String;DataType=System.String;
               ColumnSize=10;AllowDBNull=true'" />

          <!-- The following is for SCOTT.GETEMP's DEPTS REF CURSOR metadata -->
          <add name="SCOTT.&quot;GetEmpAndDept&quot;.RefCursor.DEPTS"
               value="implicitRefCursor bindinfo='mode=Output'" />

          <add name="SCOTT.&quot;GetEmpAndDept&quot;
               .RefCursorMetaData.DEPTS.Column.0"
               value="implicitRefCursor metadata='ColumnName=DEPTNO;
               BaseColumnName=DEPTNO;BaseSchemaName=SCOTT;BaseTableName=DEPT;
               NativeDataType=number;ProviderType=Int32;ProviderDBType=Int32;
               DataType=System.Int32;ColumnSize=4;NumericPrecision=10;
               NumericScale=3;AllowDBNull=false;IsKey=true'" />

          <add name="SCOTT.&quot;GetEmpAndDept&quot;
               .RefCursorMetaData.DEPTS.Column.1"
               value="implicitRefCursor metadata='ColumnName=DNAME;
               BaseColumnName=DNAME;BaseSchemaName=SCOTT;BaseTableName=DEPT;
               NativeDataType=varchar2;ProviderType=Varchar2;
               ProviderDBType=String;DataType=System.String;
               ColumnSize=10;AllowDBNull=true'" />
          </settings>
      </oracle.dataaccess.client>
    </configuration>

#### Sample Application That Uses the Configuration File

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class Program
    {
      static void Main(string[] args)
      {
        try
        {
          // Open a connection
          string constr =
            "User Id=scott;Password=tiger;Data Source=inst1";
          OracleConnection con = new OracleConnection(constr);
          con.Open();

          // Use implicit REF CURSOR binding
          //   to execute SCOTT.GETEMP function
          // Use bind by position as configured
          //   in app.config for SCOT.GETEMP
          OracleCommand cmd = con.CreateCommand();
          cmd.CommandText = "SCOTT.GETEMP";
          cmd.CommandType = CommandType.StoredProcedure;
          cmd.BindByName = false;
          OracleParameter empid = cmd.Parameters.Add("empid",
            OracleDbType.Int32, ParameterDirection.Input);
          empid.Value = 7654;

          // Populate the DataSet
          OracleDataAdapter adapter = new OracleDataAdapter(cmd);
          DataSet ds = new DataSet();
          adapter.Fill(ds);
          Console.WriteLine("Retrieved {0} row from EMP",
            ds.Tables[0].Rows.Count);

          // Use implicit REF CURSOR binding
          //   to execute "SCOTT"."GetEmpAndDept" procedure
          // Use bind by name as configured
          //   in app.config for "SCOTT"."GetEmpAndDept"
          cmd = con.CreateCommand();
          cmd.CommandText = "\"SCOTT\".\"GetEmpAndDept\"";
          cmd.CommandType = CommandType.StoredProcedure;
          cmd.BindByName = true;
          adapter = new OracleDataAdapter(cmd);
          adapter.Fill(ds);
          Console.WriteLine("Retrieved {0} rows from DEPT",
            ds.Tables[1].Rows.Count);
        }
        catch (Exception ex)
        {
          // Output the message
          Console.WriteLine(ex.Message);
          if (ex.InnerException != null)
          {
            // If any details are available regarding
            // errors in the app.config, print them out
            Console.WriteLine(ex.InnerException.Message);
            if (ex.InnerException.InnerException != null)
            {
              Console.WriteLine(
                ex.InnerException.InnerException.Message);
            }
          }
        }
      }
    }

### Usage Considerations

This section discusses the following usage considerations when using implicit `REF CURSOR`:

- CommandText Property Considerations

- Bind Considerations

- Overloaded Stored Procedures

- Type Initialization Exceptions

- Using Stored Functions with Function Import

#### CommandText Property Considerations

ODP.NET applications should ensure that the stored procedure name and the `OracleCommand CommandText` match exactly. Let's take a scenario where the stored procedure name in the database is `SCOTT.TESTPROC`. Now, if the `CommandText` uses `TESTPROC`, ODP.NET will look for entries matching `TESTPROC` only. The current schema name will not be automatically appended to `TESTPROC`. So, the correct `CommandText` to use in this scenario would be `SCOTT.TESTPROC`.

Also, the `CommandText` is case-sensitive and must use the same case as the stored procedure name in the database. So if the stored procedure name in the database is `SCOTT.Testproc`, then the `CommandText` must use `SCOTT.Testproc`.

#### Bind Considerations

If information about a `REF CURSOR` parameter has been added to the configuration file, then applications should not try to explicitly bind the `REF CURSOR` parameter to `OracleCommand`. ODP.NET automatically binds the `REF CURSOR` parameter at the appropriate locations based on the information provided in the configuration file. If the application stored procedure also has non-`REF CURSOR` parameters, then these parameters must still be explicitly bound to `OracleCommand`.

If the information specified in the configuration file for a stored procedure identifies the `REF CURSOR` parameter by name, then all the other non-`REF CURSOR` parameters should also be bound by name. Also the `BindByName` property for the `OracleCommand` object should be set to `true` in this case. Entity Framework always uses BindByName to run stored procedures. Your .NET configuration file parameter names must use the same case that was used when creating the stored procedure in the database.

If the `OracleCommand` `BindByName` property is set to `false` (default), then ODP.NET assumes that the parameters have been bound based on their position, and all parameters have been specified in the correct order. For such cases, the parameters specified in the configuration file are bound in the same order in which they appear in the configuration file.

#### Overloaded Stored Procedures

ODP.NET does not support multiple stored procedures with the same name inside the configuration file. If an ODP.NET application uses an overloaded stored procedure, the application can store only one overloaded stored procedure information in the configuration file.

#### Type Initialization Exceptions

Type initialization exceptions can be caused by invalid .NET configuration file entries. Evaluate the exception that is caught as well as its inner exceptions to determine the .NET configuration file entry or the attribute setting that is causing the exception.

ODP.NET tracing logs the valid and invalid .NET configuration file entries that ODP.NET has parsed. To look for .NET configuration file related entries, set the `TraceLevel` to the Entry, exit, and SQL statement information level setting. Trace entries related to implicit `REF CURSOR` binding have a `(REFCURSOR)` entry along with `(ERROR),` if any errors are encountered.

#### Using Stored Functions with Function Import

Function Import only supports stored procedures, and does not support functions. When using the Add Function Import dialog for the Entity Data Model that you have created, the Get Column Information button does not return the metadata information for the `REF CURSOR` that is being returned by a stored function, even if it is configured properly in the .NET configuration file.
