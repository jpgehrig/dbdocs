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

- [Prev](../jdbc/xa/client/package-tree.md)
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Hierarchy For Package oracle.sql

Package Hierarchies:

- [All Packages](../../overview-tree.md)

## Class Hierarchy

- java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)
  - oracle.sql.[ANYDATA](ANYDATA.md) (implements oracle.jdbc.[OracleData](../jdbc/OracleData.md), oracle.sql.[ORAData](ORAData.md))
  - oracle.sql.[AttributeDescriptor](AttributeDescriptor.md)
  - oracle.sql.[CharacterBuffer](CharacterBuffer.md)
  - oracle.sql.[CharacterSet](CharacterSet.md)
    - oracle.sql.[CharacterSetWithConverter](CharacterSetWithConverter.md)
  - oracle.sql.[CharacterWalker](CharacterWalker.md)
  - oracle.sql.[ConcreteProxyUtil](ConcreteProxyUtil.md)
  - oracle.sql.[ConverterArchive](ConverterArchive.md)
  - oracle.sql.[Datum](Datum.md) (implements java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.sql.[BINARY_DOUBLE](BINARY_DOUBLE.md)
    - oracle.sql.[BINARY_FLOAT](BINARY_FLOAT.md)
    - oracle.sql.[CHAR](CHAR.md)
    - oracle.sql.[DATE](DATE.md) (implements oracle.jdbc.internal.OracleDate)
    - oracle.sql.[DatumWithConnection](DatumWithConnection.md) (implements oracle.jdbc.internal.OracleDatumWithConnection)
      - oracle.sql.[ARRAY](ARRAY.md) (implements oracle.jdbc.internal.OracleArray, oracle.jdbc.internal.OracleConcreteProxy)
      - oracle.sql.[BFILE](BFILE.md) (implements oracle.jdbc.internal.OracleBfile, oracle.jdbc.internal.OracleConcreteProxy)
      - oracle.sql.[BLOB](BLOB.md) (implements oracle.jdbc.internal.OracleBlob, oracle.jdbc.internal.OracleConcreteProxy)
      - oracle.sql.[CLOB](CLOB.md) (implements oracle.jdbc.internal.OracleClob, oracle.jdbc.internal.OracleConcreteProxy)
        - oracle.sql.[NCLOB](NCLOB.md) (implements oracle.jdbc.internal.OracleNClob)
      - oracle.sql.[OPAQUE](OPAQUE.md) (implements oracle.jdbc.internal.OracleOpaque)
      - oracle.sql.[REF](REF.md) (implements java.lang.[Cloneable](http://download.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true), oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleRef, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
      - oracle.sql.[STRUCT](STRUCT.md) (implements oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleStruct)
        - oracle.sql.[JAVA_STRUCT](JAVA_STRUCT.md)
    - oracle.sql.[INTERVALDS](INTERVALDS.md)
    - oracle.sql.[INTERVALYM](INTERVALYM.md)
    - oracle.sql.[NUMBER](NUMBER.md) (implements oracle.jdbc.internal.OracleNumber)
    - oracle.sql.[RAW](RAW.md)
    - oracle.sql.[ROWID](ROWID.md) (implements oracle.jdbc.internal.OracleRowId)
    - oracle.sql.[TIMESTAMP](TIMESTAMP.md) (implements oracle.jdbc.internal.OracleTimestamp, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.sql.[TIMESTAMPLTZ](TIMESTAMPLTZ.md)
    - oracle.sql.[TIMESTAMPTZ](TIMESTAMPTZ.md) (implements oracle.jdbc.internal.OracleTimestampWithTimeZone)
  - oracle.sql.[TypeDescriptor](TypeDescriptor.md) (implements oracle.jdbc.[OracleData](../jdbc/OracleData.md), oracle.jdbc.internal.OracleTypeMetaData, oracle.sql.[ORAData](ORAData.md), java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.sql.[ArrayDescriptor](ArrayDescriptor.md) (implements oracle.jdbc.internal.OracleTypeMetaData.Array, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.sql.[OpaqueDescriptor](OpaqueDescriptor.md) (implements oracle.jdbc.internal.OracleTypeMetaData.Opaque, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))
    - oracle.sql.[StructDescriptor](StructDescriptor.md) (implements oracle.jdbc.internal.OracleTypeMetaData.Struct, java.io.[Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true))

## Interface Hierarchy

- oracle.jdbc.internal.ObjectData
  - oracle.sql.[CustomDatum](CustomDatum.md)
  - oracle.sql.[ORAData](ORAData.md)
- oracle.jdbc.internal.ObjectDataFactory
  - oracle.sql.[CustomDatumFactory](CustomDatumFactory.md)
  - oracle.sql.[ORADataFactory](ORADataFactory.md)

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

- [Prev](../jdbc/xa/client/package-tree.md)
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
