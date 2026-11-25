This property causes executed statements to be cached when the property is set to `true` and statement caching is enabled. If statement caching is disabled or if this property is set to `false`, the executed statement is not cached.

### Declaration

    // C#
    public bool AddToStatementCache{get; set;}

### Return Value

Returns `bool` value. A value of `true` indicates that statements are being added to the cache, `false` indicates otherwise.

### Property Value

A `bool` value that indicates that the statements will be cached when they are executed, if statement caching is enabled.

### Remarks

Default is `true`.

`AddToStatementCache` is ignored if statement caching is disabled. Statement caching is enabled by setting the `Statement` `Cache` `Size` connection string attribute to a value greater than `0`.

When statement caching is enabled, however, this property provides a way to selectively add statements to the cache.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class AddToStatementCacheSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle;" +
          "statement cache size=10";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        OracleCommand cmd = new OracleCommand("select * from emp", con);

        if (cmd.AddToStatementCache)
          Console.WriteLine("Added to the statement cache:" + cmd.CommandText);
        else
          Console.WriteLine("Not added to the statement cache:" + cmd.CommandText);

        // The execution of "select * from emp" will be added to the statement cache
        // because statement cache size is greater than 0 and OracleCommand's
        // AddToStatementCache is true by default.
        OracleDataReader readerEmp = cmd.ExecuteReader();

        // Do not add "select * from dept" to the statement cache
        cmd.CommandText = "select * from dept";
        cmd.AddToStatementCache = false;

        if (cmd.AddToStatementCache)
          Console.WriteLine("Added to the statement cache:" + cmd.CommandText);
        else
          Console.WriteLine("Not added to the statement cache:" + cmd.CommandText);

        // The execution of "select * from dept" will not be added to the
        // statement cache because AddToStatementCache is set to false.
        OracleDataReader readerDept = cmd.ExecuteReader();

        // Clean up
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- "[Statement Caching](featOraCommand.md)"

- [ConnectionString](ConnectionConnectionString.md)
