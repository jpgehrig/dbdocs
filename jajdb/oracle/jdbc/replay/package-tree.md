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

- [Prev](../pool/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.jdbc.replay

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - oracle.jdbc.replay.[OracleDataSourceFactory](OracleDataSourceFactory.md)
  - oracle.jdbc.replay.[OracleDataSourceImpl](OracleDataSourceImpl.md) (implements javax.naming.spi.[ObjectFactory](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true), oracle.jdbc.replay.internal.OracleDataSource, javax.naming.[Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.replay.[OracleConnectionPoolDataSourceImpl](OracleConnectionPoolDataSourceImpl.md) (implements javax.naming.spi.[ObjectFactory](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true), oracle.jdbc.replay.internal.OracleConnectionPoolDataSource, javax.naming.[Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
      - oracle.jdbc.replay.[OracleXADataSourceImpl](OracleXADataSourceImpl.md) (implements javax.naming.spi.[ObjectFactory](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true), oracle.jdbc.replay.internal.OracleXADataSource, javax.naming.[Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))

## Interface Hierarchy

- javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)
  - javax.sql.[ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true)
    - oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md) (also extends oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md))
      - oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md) (also extends oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md))
        - oracle.jdbc.replay.[OracleXADataSource](OracleXADataSource.md) (also extends oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md))
  - javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true) (also extends java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true))
    - oracle.jdbc.datasource.[OracleDataSource](../datasource/OracleDataSource.md) (also extends oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md))
      - oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)
        - oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md) (also extends oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md))
          - oracle.jdbc.replay.[OracleXADataSource](OracleXADataSource.md) (also extends oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md))
  - oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md)
    - oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md) (also extends javax.sql.[ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true))
      - oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md) (also extends oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md))
        - oracle.jdbc.replay.[OracleXADataSource](OracleXADataSource.md) (also extends oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md))
    - oracle.jdbc.datasource.[OracleDataSource](../datasource/OracleDataSource.md) (also extends javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true))
      - oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)
        - oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md) (also extends oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md))
          - oracle.jdbc.replay.[OracleXADataSource](OracleXADataSource.md) (also extends oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md))
    - oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md) (also extends javax.sql.[XADataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true))
      - oracle.jdbc.replay.[OracleXADataSource](OracleXADataSource.md) (also extends oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md))
  - javax.sql.[XADataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)
    - oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md) (also extends oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md))
      - oracle.jdbc.replay.[OracleXADataSource](OracleXADataSource.md) (also extends oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md))
- oracle.jdbc.replay.[ConnectionInitializationCallback](ConnectionInitializationCallback.md)
- oracle.jdbc.replay.[ReplayableConnection](ReplayableConnection.md)
- oracle.jdbc.replay.[ReplayStatistics](ReplayStatistics.md)
- java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)
  - javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true) (also extends javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true))
    - oracle.jdbc.datasource.[OracleDataSource](../datasource/OracleDataSource.md) (also extends oracle.jdbc.datasource.[OracleCommonDataSource](../datasource/OracleCommonDataSource.md))
      - oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)
        - oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md) (also extends oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md))
          - oracle.jdbc.replay.[OracleXADataSource](OracleXADataSource.md) (also extends oracle.jdbc.datasource.[OracleXADataSource](../datasource/OracleXADataSource.md))

## Enum Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<E\> (implements java.lang.[Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<T\>, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.replay.[ReplayableConnection.StatisticsReportType](ReplayableConnection.StatisticsReportType.md)

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

- [Prev](../pool/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
