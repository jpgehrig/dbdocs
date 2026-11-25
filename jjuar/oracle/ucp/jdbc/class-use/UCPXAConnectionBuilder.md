Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UCPXAConnectionBuilder.md)
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

## Uses of Interface oracle.ucp.jdbc.UCPXAConnectionBuilder

- **Packages that use [UCPXAConnectionBuilder](../UCPXAConnectionBuilder.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [UCPXAConnectionBuilder](../UCPXAConnectionBuilder.md) in [oracle.ucp.jdbc](../package-summary.md)

    **Methods in [oracle.ucp.jdbc](../package-summary.md) that return [UCPXAConnectionBuilder](../UCPXAConnectionBuilder.md)**

    | Modifier and Type                                        | Method and Description                                                                                                                                                                                                                                                          |
    |----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | PoolXADataSource.[`createXAConnectionBuilder`](../PoolXADataSource.md)`()`<br>Creates a new XAConnectionBuilder instance.                                                                                                                                                       |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | PoolXADataSourceImpl.[`createXAConnectionBuilder`](../PoolXADataSourceImpl.md)`()`                                                                                                                                                                                              |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`labels`](../UCPXAConnectionBuilder.md)`(java.util.Properties labels)`<br>Sets the labels attribute on the builder                                                                                                                                      |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`password`](../UCPXAConnectionBuilder.md)`(java.lang.String password)`<br>Sets the password attribute on the builder                                                                                                                                    |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`pdbRoles`](../UCPXAConnectionBuilder.md)`(java.util.Properties pdbRoles)`<br>Sets the PDB roles to be set on the connection from the pool in connection repurposing case for a multitenant database.                                                   |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`proxyProperties`](../UCPXAConnectionBuilder.md)`(int proxyType, java.util.Properties proxyProperties)`<br>Sets the proxy properties on the builder that is used to create proxy session of the particular type as specified by the parameter proxyType |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`serviceName`](../UCPXAConnectionBuilder.md)`(java.lang.String serviceName)`<br>Sets the service name attribute on the builder                                                                                                                          |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`shardingKey`](../UCPXAConnectionBuilder.md)`(oracle.jdbc.OracleShardingKey shardingKey)`                                                                                                                                                               |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`superShardingKey`](../UCPXAConnectionBuilder.md)`(oracle.jdbc.OracleShardingKey superShardingKey)`                                                                                                                                                     |
    | [`UCPXAConnectionBuilder`](../UCPXAConnectionBuilder.md) | UCPXAConnectionBuilder.[`user`](../UCPXAConnectionBuilder.md)`(java.lang.String user)`<br>Sets the user attribute on the builder                                                                                                                                                |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UCPXAConnectionBuilder.md)
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
