This property specifies the time to wait before retrying connecting to a service that becomes unavailable. Default value is 90 seconds. Whenever a database service becomes unavailable, such as due to a service being relocated, an application can encounter numerous connectivity errors during this time. To avoid unnecessary connection attempts to an unavailable service which will result in an error, the driver will block any connection attempts until the service is up or until this property's specified time limit expires from the time when the service DOWN event was received, whichever comes first.

### Declaration

    // C#
    public static string ServiceRelocationConnectionTimeout { get; set; }

### Property Type

`System.String`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
