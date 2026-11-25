Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UCPConnectionBuilder.md)
- Use
- [Tree](../../../../overview-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Interface oracle.ucp.jdbc.UCPConnectionBuilder

- **Packages that use [UCPConnectionBuilder](../UCPConnectionBuilder.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [UCPConnectionBuilder](../UCPConnectionBuilder.md) in [oracle.ucp.jdbc](../package-summary.md)

    **Methods in [oracle.ucp.jdbc](../package-summary.md) that return [UCPConnectionBuilder](../UCPConnectionBuilder.md)**

    | Modifier and Type                                    | Method and Description                                                                                                                                                                                                                                                      |
    |------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | PoolDataSource.[`createConnectionBuilder`](../PoolDataSource.md)`()`<br>Creates a new UCPConnectionBuilder instance.                                                                                                                                                        |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | PoolDataSourceImpl.[`createConnectionBuilder`](../PoolDataSourceImpl.md)`()`                                                                                                                                                                                                |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`labels`](../UCPConnectionBuilder.md)`(java.util.Properties labels)`<br>Sets the labels attribute on the builder                                                                                                                                      |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`password`](../UCPConnectionBuilder.md)`(java.lang.String password)`<br>Sets the password attribute on the builder                                                                                                                                    |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`pdbRoles`](../UCPConnectionBuilder.md)`(java.util.Properties pdbRoles)`<br>Sets the PDB roles to be set on the connection from the pool in connection repurposing case for a multitenant database.                                                   |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`proxyProperties`](../UCPConnectionBuilder.md)`(int proxyType, java.util.Properties proxyProperties)`<br>Sets the proxy properties on the builder that is used to create proxy session of the particular type as specified by the parameter proxyType |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`serviceName`](../UCPConnectionBuilder.md)`(java.lang.String serviceName)`<br>Sets the service name attribute on the builder                                                                                                                          |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`shardingKey`](../UCPConnectionBuilder.md)`(oracle.jdbc.OracleShardingKey shardingKey)`                                                                                                                                                               |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`superShardingKey`](../UCPConnectionBuilder.md)`(oracle.jdbc.OracleShardingKey superShardingKey)`                                                                                                                                                     |
    | [`UCPConnectionBuilder`](../UCPConnectionBuilder.md) | UCPConnectionBuilder.[`user`](../UCPConnectionBuilder.md)`(java.lang.String user)`<br>Sets the user attribute on the builder                                                                                                                                                |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UCPConnectionBuilder.md)
- Use
- [Tree](../../../../overview-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
