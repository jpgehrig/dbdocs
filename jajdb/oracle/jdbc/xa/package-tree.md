Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev](../replay/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.jdbc.xa

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - oracle.jdbc.pool.[OracleDataSource](../pool/OracleDataSource.md) (implements oracle.jdbc.datasource.[OracleDataSource](../datasource/OracleDataSource.md), javax.naming.[Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.pool.[OracleConnectionPoolDataSource](../pool/OracleConnectionPoolDataSource.md) (implements oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md))
      - oracle.jdbc.xa.[OracleXADataSource](OracleXADataSource.md) (implements oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md))
  - oracle.jdbc.xa.[OracleMultiPhaseArgs](OracleMultiPhaseArgs.md)
  - oracle.jdbc.pool.[OraclePooledConnection](../pool/OraclePooledConnection.md) (implements oracle.jdbc.datasource.[OraclePooledConnection](../datasource/OraclePooledConnection.md), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.xa.[OracleXAConnection](OracleXAConnection.md) (implements oracle.jdbc.datasource.[OracleXAConnection](../datasource/OracleXAConnection.md))
  - oracle.jdbc.xa.[OracleXAConnectionBuilderImpl](OracleXAConnectionBuilderImpl.md) (implements oracle.jdbc.[OracleXAConnectionBuilder](../OracleXAConnectionBuilder.md))
  - oracle.jdbc.xa.[OracleXAResource](OracleXAResource.md) (implements javax.transaction.xa.[XAResource](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true))
  - oracle.jdbc.xa.[OracleXid](OracleXid.md) (implements java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), javax.transaction.xa.[Xid](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/Xid.html?is-external=true))
  - java.lang.[Throwable](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true) (implements java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - java.lang.[Exception](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true)
      - javax.transaction.xa.[XAException](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)
        - oracle.jdbc.xa.[OracleXAException](OracleXAException.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev](../replay/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
