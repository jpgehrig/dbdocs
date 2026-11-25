This property specifies the generated trace level to trace ODP.NET calls and diagnose provider issues. Errors will always be traced. Default value is 0 indicating tracing is disabled.

### Declaration

    // C#
    public static int TraceLevel { get; set; }

### Property Type

`System.Int32 `

Valid Values:

- 1 = public APIs

- 2 = private APIs

- 4 = network APIs/data

These values can be bitwise ORed. To enable all traces, set TraceLevel to 7.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
