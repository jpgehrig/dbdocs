This property specifies HTTP proxy host name for tunneling SSL client connections.

### Declaration

    // C#
    public static string HttpsProxy { get; set; }

### Property Type

`System.String`

### Values

HTTP proxy host name or IP address that can make an outbound connection to the internet hosts. Default is none.

### Usage Notes

Clients can tunnel secure connections over forward HTTP proxy using HTTP CONNECT method. This helps in accessing the public cloud database service as it eliminates the requirement to open an outbound port on a client side firewall. This parameter is applicable only to TCP/IP connections with SSL/TLS.

This value takes effect only when `SQLNET.USE_HTTPS_PROXY=on` is set in `sqlnet.ora`. Increase the forward web proxy read timeout for requests to a higher value depending on client queries. Otherwise, the forward web proxy closes the connection assuming that no requests are made from the client.

This parameter is applicable with Oracle Connection Manager on the database server side.

### Example

    //C#
    HttpsProxy=www-proxy.mycompany.com

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
