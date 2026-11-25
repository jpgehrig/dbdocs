This property specifies the forward HTTP proxy host port for tunneling TLS/SSL client connections.

### Declaration

    // C#
    public static int HttpsProxyPort { get; set; }

### Property Type

`System.Int32`

### Values

Proxy port number. Default is none.

### Usage Notes

This property forwards the HTTP proxy host port that receives HTTP CONNECT method. This parameter should be used along with `HTTPS_PROXY`. It takes effect only when `SQLNET.USE_HTTPS_PROXY=on` is set in `sqlnet.ora`.

### Example

    //C#
    HttpsProxyPort=80

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
