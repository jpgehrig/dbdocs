This property specifies the destination directory to output provider traces.

### Declaration

    // C#
    public static string TraceFileLocation { get; set; }

### Property Type

`System.String`

### Remarks

On Windows, the default `TraceFileLocation` is `<``Windows user temporary folder``>\ODP.NET\core\trace`. On Linux, the default is `<``current user temporary folder``>/ODP.NET/core/trace`. If you modify the trace file location, then do not use a write-protected directory, such as` C:\` on Windows. Write-protection may prevent ODP.NET from being able to write a trace file to that particular directory location.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
