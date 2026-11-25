The two major aspects to network security are authentication and data confidentiality. The type of authentication and data confidentiality is dependent on how you connect to the database, either through Oracle Net or Java Database Connectivity (JDBC) connection. The following table provides the security description for Oracle Net and JDBC connections:

| Connection Security | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Net          | The database can require both authentication and authorization before allowing a user to connect to it. Oracle Net database connection security can require one or more of the following:<br>• A user name and password for client verification. For each connection request, a user name and password configured within Oracle Net has to be provided.<br>• Advanced Networking Option for encryption, kerberos, or secureId.<br>• SSL for certificate authentication. |
| JDBC                | The JDBC connection security that is required is similar to the constraints required on an Oracle Net database connection.                                                                                                                                                                                                                                                                                                                                              |

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/introducing-oracle-net-services.md)

- [Oracle Database Security Guide](../dbseg/configuring-thin-jdbc-client-network.md)

- [Oracle Database JDBC Developer’s Guide](../jjdbc/introducing-JDBC.md)
