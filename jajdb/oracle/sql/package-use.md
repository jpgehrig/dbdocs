Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Uses of Package oracle.sql

- **Packages that use [oracle.sql](package-summary.md)**

  | Package         | Description                                                                                                                                               |
  |-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc     | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                                                         |
  | oracle.jdbc.aq  | This package is an Oracle JDBC extension that provides interfaces to access the Advanced Queuing feature of Oracle for enterprise messaging applications. |
  | oracle.jdbc.dcn | This package is an Oracle JDBC extension that provides interfaces to access the Database Change Notification feature of Oracle.                           |
  | oracle.sql      | A package of classes that represent java SQL types and Oracle specific SQL types.                                                                         |

- **Classes in [oracle.sql](package-summary.md) used by [oracle.jdbc](../jdbc/package-summary.md)**

  | Class and Description                                                                                                                                              |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [ARRAY](class-use/ARRAY.md)<br>Deprecated. <br>Use java.sql.Array interface for declaration instead of using concrete class oracle.sql.ARRAY.                      |
  | [BFILE](class-use/BFILE.md)<br>Deprecated. <br>Use oracle.jdbc.OracleBfile interface for declaration instead of using concrete class oracle.sql.BFILE.             |
  | [BINARY_DOUBLE](class-use/BINARY_DOUBLE.md)<br>The BINARY_DOUBLE class is a representation of the Oracle BINARY_DOUBLE datatype.                                   |
  | [BINARY_FLOAT](class-use/BINARY_FLOAT.md)<br>The BINARY_FLOAT class is a representation of the Oracle BINARY_FLOAT datatype.                                       |
  | [BLOB](class-use/BLOB.md)<br>Deprecated. <br>Use java.sql.Blob interface for declaration instead of using concrete class oracle.sql.BLOB.                          |
  | [CHAR](class-use/CHAR.md)<br>The Oracle specific representation of characters.                                                                                     |
  | [CLOB](class-use/CLOB.md)<br>Deprecated. <br>Use java.sql.Clob interface for declaration instead of using concrete class oracle.sql.CLOB.                          |
  | [CustomDatum](class-use/CustomDatum.md)<br>This is an interface for encapsulating SQL Types into Java types of the user's choice.                                  |
  | [CustomDatumFactory](class-use/CustomDatumFactory.md)<br>This interface complements CustomDatum.                                                                   |
  | [DATE](class-use/DATE.md)<br>**DATE Class**                                                                                                                        |
  | [Datum](class-use/Datum.md)<br>The root of Oracle native datatype hierarchy.                                                                                       |
  | [INTERVALDS](class-use/INTERVALDS.md)<br>**INTERVALDS Class**                                                                                                      |
  | [INTERVALYM](class-use/INTERVALYM.md)<br>**INTERVALYM Class**                                                                                                      |
  | [NUMBER](class-use/NUMBER.md)<br>**NUMBER Class**                                                                                                                  |
  | [OPAQUE](class-use/OPAQUE.md)<br>Deprecated. <br>Use oracle.jdbc.OracleOpaque interface for declaration instead of using concrete class oracle.sql.OPAQUE.         |
  | [ORAData](class-use/ORAData.md)<br>Oracle interface for customized user-defined types.                                                                             |
  | [ORADataFactory](class-use/ORADataFactory.md)<br>ORAData factory interface.                                                                                        |
  | [RAW](class-use/RAW.md)<br>The RAW class is a representation of the Oracle RAW datatype.                                                                           |
  | [REF](class-use/REF.md)<br>Deprecated. <br>Use java.sql.Ref interface for declaration instead of using concrete class oracle.sql.REF.                              |
  | [ROWID](class-use/ROWID.md)<br>The ROWID class is a representation of the Oracle ROWID datatype.                                                                   |
  | [STRUCT](class-use/STRUCT.md)<br>Deprecated. <br>Use java.sql.Struct interface for declaration instead of using concrete class oracle.sql.STRUCT.                  |
  | [StructDescriptor](class-use/StructDescriptor.md)<br>Deprecated. <br>Use factory method Connection.createStruct to create an instance of java.sql.Struct directly. |
  | [TIMESTAMP](class-use/TIMESTAMP.md)<br>**TIMESTAMP Class**                                                                                                         |
  | [TIMESTAMPLTZ](class-use/TIMESTAMPLTZ.md)<br>**TIMESTAMPLTZ Class**                                                                                                |
  | [TIMESTAMPTZ](class-use/TIMESTAMPTZ.md)<br>**TIMESTAMPTZ Class**                                                                                                   |
  | [TypeDescriptor](class-use/TypeDescriptor.md)<br>The descriptor of pre-defined types.                                                                              |

- **Classes in [oracle.sql](package-summary.md) used by [oracle.jdbc.aq](../jdbc/aq/package-summary.md)**

  | Class and Description                                                                                                                             |
  |---------------------------------------------------------------------------------------------------------------------------------------------------|
  | [ANYDATA](class-use/ANYDATA.md)<br>This class is the Java mapping of the SYS.ANYDATA SQL type.                                                    |
  | [RAW](class-use/RAW.md)<br>The RAW class is a representation of the Oracle RAW datatype.                                                          |
  | [STRUCT](class-use/STRUCT.md)<br>Deprecated. <br>Use java.sql.Struct interface for declaration instead of using concrete class oracle.sql.STRUCT. |

- **Classes in [oracle.sql](package-summary.md) used by [oracle.jdbc.dcn](../jdbc/dcn/package-summary.md)**

  | Class and Description                                                                            |
  |--------------------------------------------------------------------------------------------------|
  | [ROWID](class-use/ROWID.md)<br>The ROWID class is a representation of the Oracle ROWID datatype. |

- **Classes in [oracle.sql](package-summary.md) used by [oracle.sql](package-summary.md)**

  | Class and Description                                                                                                                                                      |
  |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [ANYDATA](class-use/ANYDATA.md)<br>This class is the Java mapping of the SYS.ANYDATA SQL type.                                                                             |
  | [ARRAY](class-use/ARRAY.md)<br>Deprecated. <br>Use java.sql.Array interface for declaration instead of using concrete class oracle.sql.ARRAY.                              |
  | [ArrayDescriptor](class-use/ArrayDescriptor.md)<br>Deprecated. <br>Use factory method OracleConnection.createOracleArray to create an instance of java.sql.Array directly. |
  | [AttributeDescriptor](class-use/AttributeDescriptor.md)                                                                                                                    |
  | [BFILE](class-use/BFILE.md)<br>Deprecated. <br>Use oracle.jdbc.OracleBfile interface for declaration instead of using concrete class oracle.sql.BFILE.                     |
  | [BLOB](class-use/BLOB.md)<br>Deprecated. <br>Use java.sql.Blob interface for declaration instead of using concrete class oracle.sql.BLOB.                                  |
  | [CharacterSet](class-use/CharacterSet.md)<br>This class encapsulates methods and attributes of the character sets defined by Oracle.                                       |
  | [CLOB](class-use/CLOB.md)<br>Deprecated. <br>Use java.sql.Clob interface for declaration instead of using concrete class oracle.sql.CLOB.                                  |
  | [CustomDatum](class-use/CustomDatum.md)<br>This is an interface for encapsulating SQL Types into Java types of the user's choice.                                          |
  | [DATE](class-use/DATE.md)<br>**DATE Class**                                                                                                                                |
  | [Datum](class-use/Datum.md)<br>The root of Oracle native datatype hierarchy.                                                                                               |
  | [DatumWithConnection](class-use/DatumWithConnection.md)<br>A supper class for some Oracle specific datatypes, such as BFILE, BLOB, etc.                                    |
  | [NUMBER](class-use/NUMBER.md)<br>**NUMBER Class**                                                                                                                          |
  | [OpaqueDescriptor](class-use/OpaqueDescriptor.md)<br>Deprecated. <br>OPAQUE types cannot be created on the client side.                                                    |
  | [ORAData](class-use/ORAData.md)<br>Oracle interface for customized user-defined types.                                                                                     |
  | [RAW](class-use/RAW.md)<br>The RAW class is a representation of the Oracle RAW datatype.                                                                                   |
  | [STRUCT](class-use/STRUCT.md)<br>Deprecated. <br>Use java.sql.Struct interface for declaration instead of using concrete class oracle.sql.STRUCT.                          |
  | [StructDescriptor](class-use/StructDescriptor.md)<br>Deprecated. <br>Use factory method Connection.createStruct to create an instance of java.sql.Struct directly.         |
  | [TIMESTAMP](class-use/TIMESTAMP.md)<br>**TIMESTAMP Class**                                                                                                                 |
  | [TIMESTAMPTZ](class-use/TIMESTAMPTZ.md)<br>**TIMESTAMPTZ Class**                                                                                                           |
  | [TypeDescriptor](class-use/TypeDescriptor.md)<br>The descriptor of pre-defined types.                                                                                      |

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
