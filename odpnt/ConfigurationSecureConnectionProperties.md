`OracleConfiguration`Secure Connection properties are listed in Table 6-32.

Table 6-32 OracleConfiguration Secure Connection Properties

| Property                                                                           | Description                                                                                                                                        |
|:-----------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| [HttpsProxy](ConfigurationHttpsProxy.md)                                           | Specifies HTTP proxy host name for tunneling SSL client connections                                                                                |
| [HttpsProxyPort](ConfigurationHttpsProxyPort.md)                                   | Specifies the forward HTTP proxy host port for tunneling TLS/SSL client connections                                                                |
| [SqlNetAuthenticationServices](ConfigurationSqlNetAuthenticationServices.md)       | Enables one or more authentication services, such as TCP/IP with SSL                                                                               |
| [SqlNetEncryptionClient](ConfigurationSqlNetEncryptionClient.md)                   | Specifies the encryption client behavior                                                                                                           |
| [SqlNetEncryptionTypesClient](ConfigurationSqlNetEncryptionTypesClient.md)         | Specifies encryption algorithms that the client can use                                                                                            |
| [SqlNetCryptoChecksumClient](ConfigurationSqlNetCryptoChecksumClient.md)           | Specifies the checksum client behavior                                                                                                             |
| [SqlNetCryptoChecksumTypesClient](ConfigurationSqlNetCryptoChecksumTypesClient.md) | Specifies the crypto-checksum algorithms the client can use                                                                                        |
| [SqlNetWalletOverride](ConfigurationSqlNetWalletOverride.md)                       | Specifies whether the client overrides the strong authentication credential with the stored wallet password credential for the database connection |
| [SSLServerDNMatch](ConfigurationSSLServerDNMatch.md)                               | Enforces the database server distinguished name (DN) matches its service name                                                                      |
| [SSLVersion](ConfigurationSSLVersion.md)                                           | Enforces the connection to use a specific SSL/TLS version                                                                                          |
| [UseHttpsProxy](ConfigurationUseHttpsProxy.md)                                     | Enables forward HTTP proxy tunneling client connections                                                                                            |
| [WalletLocation](ConfigurationWalletLocation.md)                                   | Specifies the location of wallets                                                                                                                  |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
