This property specifies the ODP.NET connection performance counters to publish so that they can be monitored.

### Declaration

    // C#
    public static Int64 PerformanceCounters { get; set; }

### Property Type

`System.Int64`

### Remarks

ODP.NET enables monitoring many different connection counters, including pooled and non-pooled connections. These counters can be monitored individually or together. Developers can set which counters to monitor prior to application startup using the `PerformanceCounters` property.

By default, performance counters are not enabled.

**See Also:**

- [Connection Performance Counters](featConnecting.md) for more information on setting up and configuring counters.

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
