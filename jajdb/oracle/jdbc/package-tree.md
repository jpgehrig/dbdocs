Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
-

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Hierarchy For Package oracle.jdbc

Package Hierarchies:

- [All Packages](../../overview-tree.md)

## Class Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - java.util.[EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true) (implements java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.[LogicalTransactionIdEvent](LogicalTransactionIdEvent.md)
  - oracle.jdbc.[OracleConnectionWrapper](OracleConnectionWrapper.md) (implements oracle.jdbc.[OracleConnection](OracleConnection.md))
  - oracle.jdbc.[OracleConnectionWrapper.CloseInvocationHandler](OracleConnectionWrapper.CloseInvocationHandler.md) (implements java.lang.reflect.[InvocationHandler](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/InvocationHandler.html?is-external=true))
  - oracle.jdbc.[OracleDatabaseMetaData](OracleDatabaseMetaData.md) (implements oracle.jdbc.internal.AdditionalDatabaseMetaData)
  - oracle.jdbc.driver.OracleDriver (implements java.sql.[Driver](http://download.oracle.com/javase/8/docs/api/java/sql/Driver.html?is-external=true))
    - oracle.jdbc.[OracleDriver](OracleDriver.md)
  - oracle.jdbc.[OracleTemporalField](OracleTemporalField.md)
  - oracle.jdbc.[OracleTypes](OracleTypes.md)
  - java.security.[Permission](http://download.oracle.com/javase/8/docs/api/java/security/Permission.html?is-external=true) (implements java.security.[Guard](http://download.oracle.com/javase/8/docs/api/java/security/Guard.html?is-external=true), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - java.security.[BasicPermission](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true) (implements java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
      - oracle.jdbc.[OracleSQLPermission](OracleSQLPermission.md)
  - java.lang.[Throwable](http://download.oracle.com/javase/8/docs/api/java/lang/Throwable.html?is-external=true) (implements java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - java.lang.[Exception](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true)
      - oracle.jdbc.[OracleDatabaseException](OracleDatabaseException.md)

## Interface Hierarchy

- oracle.jdbc.[AccessToken](AccessToken.md)
- java.sql.[Array](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)
  - oracle.jdbc.[OracleArray](OracleArray.md)
- java.lang.[AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true)
  - java.sql.[Connection](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) (also extends java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true))
    - oracle.jdbc.[OracleConnection](OracleConnection.md)
  - java.sql.[ResultSet](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) (also extends java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true))
    - oracle.jdbc.[OracleResultSet](OracleResultSet.md)
  - java.sql.[Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true) (also extends java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true))
    - oracle.jdbc.[OracleStatement](OracleStatement.md)
      - oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md) (also extends java.sql.[PreparedStatement](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true))
        - oracle.jdbc.[OracleCallableStatement](OracleCallableStatement.md) (also extends java.sql.[CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true))
    - java.sql.[PreparedStatement](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)
      - java.sql.[CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)
        - oracle.jdbc.[OracleCallableStatement](OracleCallableStatement.md) (also extends oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md))
      - oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md) (also extends oracle.jdbc.[OracleStatement](OracleStatement.md))
        - oracle.jdbc.[OracleCallableStatement](OracleCallableStatement.md) (also extends java.sql.[CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true))
- java.sql.[Blob](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)
  - oracle.jdbc.[OracleBlob](OracleBlob.md)
- java.sql.[Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)
  - java.sql.[NClob](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true)
    - oracle.jdbc.[OracleNClob](OracleNClob.md) (also extends oracle.jdbc.[OracleClob](OracleClob.md))
  - oracle.jdbc.[OracleClob](OracleClob.md)
    - oracle.jdbc.[OracleNClob](OracleNClob.md) (also extends java.sql.[NClob](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true))
- java.lang.[Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<T\>
  - oracle.jdbc.[OracleShardingKey](OracleShardingKey.md)
- java.util.[EventListener](http://download.oracle.com/javase/8/docs/api/java/util/EventListener.html?is-external=true)
  - oracle.jdbc.[LogicalTransactionIdEventListener](LogicalTransactionIdEventListener.md)
- oracle.jdbc.[NotificationRegistration](NotificationRegistration.md)
- oracle.jdbc.[OracleBfile](OracleBfile.md)
- oracle.jdbc.[OracleConnectionBuilder](OracleConnectionBuilder.md)
- oracle.jdbc.[OracleData](OracleData.md)
- oracle.jdbc.[OracleDataFactory](OracleDataFactory.md)
- oracle.jdbc.[OracleOCIFailover](OracleOCIFailover.md)
- oracle.jdbc.[OracleOpaque](OracleOpaque.md)
- oracle.jdbc.[OraclePooledConnectionBuilder](OraclePooledConnectionBuilder.md)
- oracle.jdbc.[OracleShardingKeyBuilder](OracleShardingKeyBuilder.md)
- oracle.jdbc.[OracleTranslatingConnection](OracleTranslatingConnection.md)
- oracle.jdbc.[OracleTypeMetaData](OracleTypeMetaData.md)
  - oracle.jdbc.[OracleTypeMetaData.Array](OracleTypeMetaData.Array.md)
  - oracle.jdbc.[OracleTypeMetaData.Opaque](OracleTypeMetaData.Opaque.md)
  - oracle.jdbc.[OracleTypeMetaData.Struct](OracleTypeMetaData.Struct.md)
- oracle.jdbc.[OracleXAConnectionBuilder](OracleXAConnectionBuilder.md)
- java.sql.[Ref](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)
  - oracle.jdbc.[OracleRef](OracleRef.md)
- java.sql.[Savepoint](http://download.oracle.com/javase/8/docs/api/java/sql/Savepoint.html?is-external=true)
  - oracle.jdbc.[OracleSavepoint](OracleSavepoint.md)
- java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)
  - oracle.jdbc.[LogicalTransactionId](LogicalTransactionId.md)
- java.sql.[Struct](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)
  - oracle.jdbc.[OracleStruct](OracleStruct.md)
- java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)
  - java.sql.[Connection](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) (also extends java.lang.[AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true))
    - oracle.jdbc.[OracleConnection](OracleConnection.md)
  - java.sql.[DatabaseMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/DatabaseMetaData.html?is-external=true)
    - oracle.jdbc.[AdditionalDatabaseMetaData](AdditionalDatabaseMetaData.md)
  - java.sql.[ParameterMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ParameterMetaData.html?is-external=true)
    - oracle.jdbc.[OracleParameterMetaData](OracleParameterMetaData.md)
  - java.sql.[ResultSet](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) (also extends java.lang.[AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true))
    - oracle.jdbc.[OracleResultSet](OracleResultSet.md)
  - java.sql.[ResultSetMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true)
    - oracle.jdbc.[OracleResultSetMetaData](OracleResultSetMetaData.md)
      - oracle.jdbc.[StructMetaData](StructMetaData.md)
  - java.sql.[Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true) (also extends java.lang.[AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true))
    - oracle.jdbc.[OracleStatement](OracleStatement.md)
      - oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md) (also extends java.sql.[PreparedStatement](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true))
        - oracle.jdbc.[OracleCallableStatement](OracleCallableStatement.md) (also extends java.sql.[CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true))
    - java.sql.[PreparedStatement](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)
      - java.sql.[CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)
        - oracle.jdbc.[OracleCallableStatement](OracleCallableStatement.md) (also extends oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md))
      - oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md) (also extends oracle.jdbc.[OracleStatement](OracleStatement.md))
        - oracle.jdbc.[OracleCallableStatement](OracleCallableStatement.md) (also extends java.sql.[CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true))

## Enum Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<E\> (implements java.lang.[Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<T\>, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.jdbc.[OracleTypeMetaData.Kind](OracleTypeMetaData.Kind.md)
    - oracle.jdbc.[OracleTypeMetaData.ArrayStorage](OracleTypeMetaData.ArrayStorage.md)
    - oracle.jdbc.[OracleType](OracleType.md) (implements java.sql.[SQLType](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true))
    - oracle.jdbc.[OracleTranslatingConnection.SqlTranslationVersion](OracleTranslatingConnection.SqlTranslationVersion.md)
    - oracle.jdbc.[OracleResultSetMetaData.SecurityAttribute](OracleResultSetMetaData.SecurityAttribute.md)
    - oracle.jdbc.[OracleResultSet.AuthorizationIndicator](OracleResultSet.AuthorizationIndicator.md)
    - oracle.jdbc.[OracleDatabaseMetaData.DataTypeSource](OracleDatabaseMetaData.DataTypeSource.md)
    - oracle.jdbc.[OracleConnection.DatabaseShutdownMode](OracleConnection.DatabaseShutdownMode.md)
    - oracle.jdbc.[OracleConnection.DatabaseStartupMode](OracleConnection.DatabaseStartupMode.md)
    - oracle.jdbc.[OracleConnection.CommitOption](OracleConnection.CommitOption.md)
    - oracle.jdbc.[OracleConnection.DRCPState](OracleConnection.DRCPState.md)
    - oracle.jdbc.[OracleConnection.ConnectionValidation](OracleConnection.ConnectionValidation.md)
    - oracle.jdbc.[NotificationRegistration.RegistrationState](NotificationRegistration.RegistrationState.md)
    - oracle.jdbc.[LargeObjectAccessMode](LargeObjectAccessMode.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- Tree
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
-

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
