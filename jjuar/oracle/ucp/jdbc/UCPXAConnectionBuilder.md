Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UCPXAConnectionBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UCPConnectionBuilder.md)
- [Next Class](ValidConnection.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.ucp.jdbc

## Interface UCPXAConnectionBuilder

-

  ------------------------------------------------------------------------



      public interface UCPXAConnectionBuilder

  A builder created from a `PoolXADataSource` object, used to get a connection to the database that the `PoolXADataSource` object represents. The connection properties that were specified for the `PoolXADataSource` are used as the default values by the `UCPXAConnectionBuilder`.
  To use the builder, the corresponding builder method needs to be called for each parameter that needs to be part of the connection request followed by a build() method. The order in which the builder methods are called is not important. However if the same builder attribute is applied more than once, only the most recent value will be considered while building the connection. The builder object can be reused to build more than one connection and the builder attributes will be retained across multiple invocations of the build() method.

  The following example illustrates the use of `UCPXAConnectionBuilder` to get a `XAConnection`:


         PoolXADataSource pdsXa = new PoolXADataSourceImpl();
         OracleShardingKey superShardingKey = pdsXa.createShardingKeyBuilder()
                                                   .subkey("EASTERN_REGION", JDBCType.VARCHAR)
                                                   .build();
         OracleShardingKey shardingKey = pdsXa.createShardingKeyBuilder()
                                              .subkey("PITTSBURGH_BRANCH", JDBCType.VARCHAR)
                                              .build();

         OracleConnection connection = pds.createConnectionBuilder()
                                          .user("rafa")
                                          .password("tennis")
                                          .shardingKey(shardingKey)
                                          .superShardingKey(superShardingKey)
                                          .build();



<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type        | Method and Description                                                                                                                                                                                                   |
    |--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `javax.sql.XAConnection` | `build``()`<br>Builds the XA connection object.                                                                                                                                                                          |
    | `UCPXAConnectionBuilder` | `labels``(java.util.Properties labels)`<br>Sets the labels attribute on the builder                                                                                                                                      |
    | `UCPXAConnectionBuilder` | `password``(java.lang.String password)`<br>Sets the password attribute on the builder                                                                                                                                    |
    | `UCPXAConnectionBuilder` | `pdbRoles``(java.util.Properties pdbRoles)`<br>Sets the PDB roles to be set on the connection from the pool in connection repurposing case for a multitenant database.                                                   |
    | `UCPXAConnectionBuilder` | `proxyProperties``(int proxyType, java.util.Properties proxyProperties)`<br>Sets the proxy properties on the builder that is used to create proxy session of the particular type as specified by the parameter proxyType |
    | `UCPXAConnectionBuilder` | `serviceName``(java.lang.String serviceName)`<br>Sets the service name attribute on the builder                                                                                                                          |
    | `UCPXAConnectionBuilder` | `shardingKey``(oracle.jdbc.OracleShardingKey shardingKey)`                                                                                                                                                               |
    | `UCPXAConnectionBuilder` | `superShardingKey``(oracle.jdbc.OracleShardingKey superShardingKey)`                                                                                                                                                     |
    | `UCPXAConnectionBuilder` | `user``(java.lang.String user)`<br>Sets the user attribute on the builder                                                                                                                                                |

<!-- -->

- - ### Method Detail

    - #### user

          UCPXAConnectionBuilder user(java.lang.String user)

      Sets the user attribute on the builder
      Parameters:
      `user` - the database user on whose behalf the connection is being made

      Returns:
      this builder object

    <!-- -->

    - #### password

          UCPXAConnectionBuilder password(java.lang.String password)

      Sets the password attribute on the builder
      Parameters:
      `password` -

      Returns:
      this connection builder object

    <!-- -->

    - #### labels

          UCPXAConnectionBuilder labels(java.util.Properties labels)

      Sets the labels attribute on the builder
      Parameters:
      `labels` - The requested connection labels.

      Returns:
      this connection builder object

    <!-- -->

    - #### serviceName

          UCPXAConnectionBuilder serviceName(java.lang.String serviceName)

      Sets the service name attribute on the builder
      Parameters:
      `serviceName` - to retrieve the connection

      Returns:
      this connection builder instance

    <!-- -->

    - #### proxyProperties

          UCPXAConnectionBuilder proxyProperties(int proxyType,
                                                 java.util.Properties proxyProperties)

      Sets the proxy properties on the builder that is used to create proxy session of the particular type as specified by the parameter proxyType
      Parameters:
      `proxyType` - create proxy session of this type

      `proxyProperties` - connection with these proxy properties

      Returns:
      this connection builder instance

      See Also:
      `oracle.jdbc.OracleConnection.openProxySession(int type, java.util.Properties prop)} for valid combinations of the proxy session properties`

    <!-- -->

    - #### shardingKey

          UCPXAConnectionBuilder shardingKey(oracle.jdbc.OracleShardingKey shardingKey)

      Parameters:
      `shardingKey` - Sharding Key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

    <!-- -->

    - #### superShardingKey

          UCPXAConnectionBuilder superShardingKey(oracle.jdbc.OracleShardingKey superShardingKey)

      Parameters:
      `superShardingKey` - Super shardingKey key object that needs to be part of connection request

      Returns:
      This instance of the connection builder.

    <!-- -->

    - #### pdbRoles

          UCPXAConnectionBuilder pdbRoles(java.util.Properties pdbRoles)

      Sets the PDB roles to be set on the connection from the pool in connection repurposing case for a multitenant database.
      Parameters:
      `pdbRoles` - PDB roles and their passwords passed in as key value pairs

      Returns:
      This instance of the connection builder.

    <!-- -->

    - #### build

          javax.sql.XAConnection build()
                                throws java.sql.SQLException

      Builds the XA connection object.
      Returns:
      XAConnection created considering the builder attributes

      Throws:
      `java.sql.SQLException` - if there is a failure in building the connection.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UCPXAConnectionBuilder.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UCPConnectionBuilder.md)
- [Next Class](ValidConnection.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2022, Oracle and/or its affiliates.
