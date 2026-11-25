Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../jdbc/xa/client/package-summary.md)
- Next Package

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Package oracle.sql

A package of classes that represent java SQL types and Oracle specific SQL types.

See: Description

- **Interface Summary**

  | Interface                                   | Description                                                                            |
  |---------------------------------------------|----------------------------------------------------------------------------------------|
  | [CustomDatum](CustomDatum.md)               | This is an interface for encapsulating SQL Types into Java types of the user's choice. |
  | [CustomDatumFactory](CustomDatumFactory.md) | This interface complements CustomDatum.                                                |
  | [ORAData](ORAData.md)                       | Oracle interface for customized user-defined types.                                    |
  | [ORADataFactory](ORADataFactory.md)         | ORAData factory interface.                                                             |

- **Class Summary**

  | Class                                                     | Description                                                                                                                                |
  |-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
  | [ANYDATA](ANYDATA.md)                                     | This class is the Java mapping of the SYS.ANYDATA SQL type.                                                                                |
  | [ARRAY](ARRAY.md)                                         | Deprecated<br>Use java.sql.Array interface for declaration instead of using concrete class oracle.sql.ARRAY.                               |
  | [ArrayDescriptor](ArrayDescriptor.md)                     | Deprecated<br>Use factory method OracleConnection.createOracleArray to create an instance of java.sql.Array directly.                      |
  | [AttributeDescriptor](AttributeDescriptor.md)             |                                                                                                                                            |
  | [BFILE](BFILE.md)                                         | Deprecated<br>Use oracle.jdbc.OracleBfile interface for declaration instead of using concrete class oracle.sql.BFILE.                      |
  | [BINARY_DOUBLE](BINARY_DOUBLE.md)                         | The BINARY_DOUBLE class is a representation of the Oracle BINARY_DOUBLE datatype.                                                          |
  | [BINARY_FLOAT](BINARY_FLOAT.md)                           | The BINARY_FLOAT class is a representation of the Oracle BINARY_FLOAT datatype.                                                            |
  | [BLOB](BLOB.md)                                           | Deprecated<br>Use java.sql.Blob interface for declaration instead of using concrete class oracle.sql.BLOB.                                 |
  | [CHAR](CHAR.md)                                           | The Oracle specific representation of characters.                                                                                          |
  | [CharacterBuffer](CharacterBuffer.md)                     | This class allows the program to construct an array of bytes in some representation using the 32 bit values returned by a CharacterWalker. |
  | [CharacterSet](CharacterSet.md)                           | This class encapsulates methods and attributes of the character sets defined by Oracle.                                                    |
  | [CharacterSetWithConverter](CharacterSetWithConverter.md) | This is an abstract base class that all character sets that use CharacterConverter are based on.                                           |
  | [CharacterWalker](CharacterWalker.md)                     | A CharacterWalker lets you walk through the characters that are represented as a sequence of bytes in some CharacterSet.                   |
  | [CLOB](CLOB.md)                                           | Deprecated<br>Use java.sql.Clob interface for declaration instead of using concrete class oracle.sql.CLOB.                                 |
  | [ConcreteProxyUtil](ConcreteProxyUtil.md)                 | This class has helper methods for all concrete class needs proxification.                                                                  |
  | [ConverterArchive](ConverterArchive.md)                   | This class allows a program to serialize an object and put it into a regular file or archive it into a zip file.                           |
  | [DATE](DATE.md)                                           | **DATE Class**                                                                                                                             |
  | [Datum](Datum.md)                                         | The root of Oracle native datatype hierarchy.                                                                                              |
  | [DatumWithConnection](DatumWithConnection.md)             | A supper class for some Oracle specific datatypes, such as BFILE, BLOB, etc.                                                               |
  | [INTERVALDS](INTERVALDS.md)                               | **INTERVALDS Class**                                                                                                                       |
  | [INTERVALYM](INTERVALYM.md)                               | **INTERVALYM Class**                                                                                                                       |
  | [JAVA_STRUCT](JAVA_STRUCT.md)                             | A class for structured data type.                                                                                                          |
  | [NCLOB](NCLOB.md)                                         | Deprecated<br>Use java.sql.NClob interface for declaration instead of using concrete class oracle.sql.NCLOB.                               |
  | [NUMBER](NUMBER.md)                                       | **NUMBER Class**                                                                                                                           |
  | [OPAQUE](OPAQUE.md)                                       | Deprecated<br>Use oracle.jdbc.OracleOpaque interface for declaration instead of using concrete class oracle.sql.OPAQUE.                    |
  | [OpaqueDescriptor](OpaqueDescriptor.md)                   | Deprecated<br>OPAQUE types cannot be created on the client side.                                                                           |
  | [RAW](RAW.md)                                             | The RAW class is a representation of the Oracle RAW datatype.                                                                              |
  | [REF](REF.md)                                             | Deprecated<br>Use java.sql.Ref interface for declaration instead of using concrete class oracle.sql.REF.                                   |
  | [ROWID](ROWID.md)                                         | The ROWID class is a representation of the Oracle ROWID datatype.                                                                          |
  | [STRUCT](STRUCT.md)                                       | Deprecated<br>Use java.sql.Struct interface for declaration instead of using concrete class oracle.sql.STRUCT.                             |
  | [StructDescriptor](StructDescriptor.md)                   | Deprecated<br>Use factory method Connection.createStruct to create an instance of java.sql.Struct directly.                                |
  | [TIMESTAMP](TIMESTAMP.md)                                 | **TIMESTAMP Class**                                                                                                                        |
  | [TIMESTAMPLTZ](TIMESTAMPLTZ.md)                           | **TIMESTAMPLTZ Class**                                                                                                                     |
  | [TIMESTAMPTZ](TIMESTAMPTZ.md)                             | **TIMESTAMPTZ Class**                                                                                                                      |
  | [TypeDescriptor](TypeDescriptor.md)                       | The descriptor of pre-defined types.                                                                                                       |

## Package oracle.sql Description

A package of classes that represent java SQL types and Oracle specific SQL types.

Since:
9*i*

Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../jdbc/xa/client/package-summary.md)
- Next Package

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
