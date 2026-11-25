Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](RealInputStream.md)**
- **[Next Class](XDBError.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xdb**

## **Class SQLXMLType**

- **java.lang.Object**

- - **oracle.sql.Datum**

  - - **oracle.sql.DatumWithConnection**

    - - **oracle.sql.OPAQUE**

      - - **[oracle.xdb.XMLType](XMLType.md)**

        - - **oracle.xdb.SQLXMLType**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, java.sql.SQLXML, oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.ObjectData, oracle.jdbc.internal.OracleDatumWithConnection, oracle.jdbc.internal.XMLTypeIntf, oracle.jdbc.OracleOpaque, oracle.sql.ORAData**

  ------------------------------------------------------------------------

  **
  **

      public class SQLXMLType
      extends XMLType
      implements java.sql.SQLXML

  **See Also:**
  **[Serialized Form](../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from class oracle.xdb.[XMLType](XMLType.md)**

      **[`_SQL_TYPECODE`](XMLType.md)`, `[`CONNTYPE_KPRB`](XMLType.md)`, `[`CONNTYPE_OCI8`](XMLType.md)`, `[`CONNTYPE_THIN`](XMLType.md)`, `[`DECODE_ON_CLIENT`](XMLType.md)`, `[`DEF_INDENT`](XMLType.md)`, `[`ENCODE_ON_CLIENT`](XMLType.md)`, `[`MAX_INDENT`](XMLType.md)`, `[`MAX_PFLAG`](XMLType.md)`, `[`PRINT_DEFAULT_PROPERTY`](XMLType.md)`, `[`PRINT_NOPRETTY`](XMLType.md)`, `[`PRINT_PRETTY`](XMLType.md)`, `[`XMLTYPE_PICKLE_AS_BINXML`](XMLType.md)`, `[`XMLTYPE_PICKLE_AS_TEXT`](XMLType.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------|
    | `SQLXMLType``()`                                                                                                           |
    | `SQLXMLType``(java.sql.Connection conn, java.io.InputStream is)`                                                           |
    | `SQLXMLType``(java.sql.Connection conn, java.io.InputStream is, java.lang.String kind)`                                    |
    | `SQLXMLType``(java.sql.Connection conn, long cstate)`                                                                      |
    | `SQLXMLType``(oracle.sql.OpaqueDescriptor type, java.sql.Connection conn, java.lang.Object value)`                         |
    | `SQLXMLType``(oracle.sql.OpaqueDescriptor type, java.sql.Connection conn, java.lang.Object value, java.lang.String kind)`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                      | Method and Description                                                                                                                 |
    |------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                 | `free``()`                                                                                                                             |
    | `java.io.InputStream`                                                  | `getBinaryStream``()`<br>SQLXML method Get the value containing the XML data from the XMLType as a InputStream                         |
    | `java.io.Reader`                                                       | `getCharacterStream``()`<br>SQLXML method Get the value containing the XML data from the XMLType as a InputStream                      |
    | `<T extends `[`Source`](../../javax/xml/transform/Source.md)`>`<br>`T` | `getSource``(java.lang.Class<T> sourceClass)`<br>SQLXML method Get the value containing the XML data from the XMLType as a InputStream |
    | `java.lang.String`                                                     | `getString``()`<br>SQLXML method Get the string value containing the XML data from the XMLType.                                        |
    | `java.io.OutputStream`                                                 | `setBinaryStream``()`<br>SQLXML method Set the string value containing the XML data to the XMLType.                                    |
    | `java.io.Writer`                                                       | `setCharacterStream``()`<br>SQLXML method Set the string value containing the XML data to the XMLType.                                 |
    | `<T extends `[`Result`](../../javax/xml/transform/Result.md)`>`<br>`T` | `setResult``(java.lang.Class<T> resultClass)`                                                                                          |
    | `void`                                                                 | `setString``(java.lang.String str)`<br>SQLXML method Set the string value containing the XML data to the XMLType.                      |

    - ### Methods inherited from class oracle.xdb.[XMLType](XMLType.md)

      [`cleanupCache`](XMLType.md)`, `[`close`](XMLType.md)`, `[`createSchemaBasedXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`createXML`](XMLType.md)`, `[`existsNode`](XMLType.md)`, `[`extract`](XMLType.md)`, `[`getBlobVal`](XMLType.md)`, `[`getBlobVal`](XMLType.md)`, `[`getClobVal`](XMLType.md)`, `[`getClobVal`](XMLType.md)`, `[`getDocument`](XMLType.md)`, `[`getDocumentFragment`](XMLType.md)`, `[`getDOM`](XMLType.md)`, `[`getInputStream`](XMLType.md)`, `[`getInputStream`](XMLType.md)`, `[`getNamespace`](XMLType.md)`, `[`getRootElement`](XMLType.md)`, `[`getSchemaURL`](XMLType.md)`, `[`getStringVal`](XMLType.md)`, `[`getStringVal`](XMLType.md)`, `[`isBinXml`](XMLType.md)`, `[`isFragment`](XMLType.md)`, `[`isSchemaBased`](XMLType.md)`, `[`isSchemaValid`](XMLType.md)`, `[`isSchemaValidated`](XMLType.md)`, `[`schemaValidate`](XMLType.md)`, `[`setBinaryXML`](XMLType.md)`, `[`setBinaryXMLEncoding`](XMLType.md)`, `[`setMetadataConn`](XMLType.md)`, `[`setPicklePreference`](XMLType.md)`, `[`setSchemaURL`](XMLType.md)`, `[`setSchemaValidated`](XMLType.md)`, `[`toBlob`](XMLType.md)`, `[`toClob`](XMLType.md)`, `[`transform`](XMLType.md)`, `[`writeToOutputStream`](XMLType.md)`, `[`writeToOutputStream`](XMLType.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.OPAQUE

      `getACProxy, getBytesValue, getDescriptor, getImageLength, getImageOffset, getJavaSqlConnection, getMap, getOracleMetaData, getSQLTypeName, getValue, isConvertibleTo, makeJdbcArray, setACProxy, setDescriptor, setImage, setImageLength, setValue, stringValue, toBytes, toClass, toClass, toJdbc, toJdbc`

    <!-- -->

    - ### Methods inherited from class oracle.sql.DatumWithConnection

      `assertNotNull, assertNotNull, getConnection, getInternalConnection, getOracleConnection, getPhysicalConnection, setPhysicalConnectionOf`

    <!-- -->

    - ### Methods inherited from class oracle.sql.Datum

      `asciiStreamValue, bigDecimalValue, binaryStreamValue, booleanValue, bytesHashCode, byteValue, characterStreamValue, compareBytes, dateValue, doubleValue, equals, floatValue, getBytes, getLength, getStream, intValue, isNull, longValue, setBytes, setShareBytes, shareBytes, stringValue, timestampValue, timestampValue, timeValue, timeValue`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleOpaque

      `getBytesValue, getDescriptor, getImageLength, getImageOffset, getJavaSqlConnection, getMap, isConvertibleTo, makeJdbcArray, setDescriptor, setImage, setImageLength, setValue, toBytes, toClass, toClass, toJdbc, toJdbc`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `asciiStreamValue, bigDecimalValue, binaryStreamValue, booleanValue, byteValue, characterStreamValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getLength, getOracleConnection, getStream, intValue, longValue, setBytes, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, stringValue, timestampValue, timestampValue, timeValue, timeValue`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.OracleOpaque

      `getOracleMetaData, getSQLTypeName, getValue`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.ACProxyable

      `getACProxy, setACProxy`

    <!-- -->

    - ### Methods inherited from interface oracle.sql.ORAData

      `toDatum`

<!-- -->

- - ### Constructor Detail

    - #### SQLXMLType

          public SQLXMLType(java.sql.Connection conn,
                            java.io.InputStream is)
                     throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### SQLXMLType

          public SQLXMLType(java.sql.Connection conn,
                            java.io.InputStream is,
                            java.lang.String kind)
                     throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### SQLXMLType

          public SQLXMLType(oracle.sql.OpaqueDescriptor type,
                            java.sql.Connection conn,
                            java.lang.Object value)
                     throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### SQLXMLType

          public SQLXMLType(oracle.sql.OpaqueDescriptor type,
                            java.sql.Connection conn,
                            java.lang.Object value,
                            java.lang.String kind)
                     throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### SQLXMLType

          public SQLXMLType(java.sql.Connection conn,
                            long cstate)
                     throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### SQLXMLType

          public SQLXMLType()
                     throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

  <!-- -->

  - ### Method Detail

    - #### free

          public void free()

      Specified by:
      `free` in interface `java.sql.SQLXML`

      Overrides:
      [`free`](XMLType.md) in class [`XMLType`](XMLType.md)

    <!-- -->

    - #### getString

          public java.lang.String getString()
                                     throws java.sql.SQLException

      SQLXML method Get the string value containing the XML data from the XMLType.
      Specified by:
      `getString` in interface `java.sql.SQLXML`

      Overrides:
      [`getString`](XMLType.md) in class [`XMLType`](XMLType.md)

      Returns:
      the string containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getBinaryStream

          public java.io.InputStream getBinaryStream()
                                              throws java.sql.SQLException

      SQLXML method Get the value containing the XML data from the XMLType as a InputStream
      Specified by:
      `getBinaryStream` in interface `java.sql.SQLXML`

      Overrides:
      [`getBinaryStream`](XMLType.md) in class [`XMLType`](XMLType.md)

      Returns:
      the InputStream containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getCharacterStream

          public java.io.Reader getCharacterStream()
                                            throws java.sql.SQLException

      SQLXML method Get the value containing the XML data from the XMLType as a InputStream
      Specified by:
      `getCharacterStream` in interface `java.sql.SQLXML`

      Overrides:
      [`getCharacterStream`](XMLType.md) in class [`XMLType`](XMLType.md)

      Returns:
      the Reader containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getSource

          public <T extends Source> T getSource(java.lang.Class<T> sourceClass)
                                         throws java.sql.SQLException

      SQLXML method Get the value containing the XML data from the XMLType as a InputStream
      Specified by:
      `getSource` in interface `java.sql.SQLXML`

      Overrides:
      [`getSource`](XMLType.md) in class [`XMLType`](XMLType.md)

      Returns:
      the Reader containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setString

          public void setString(java.lang.String str)
                         throws java.sql.SQLException

      SQLXML method Set the string value containing the XML data to the XMLType.
      Specified by:
      `setString` in interface `java.sql.SQLXML`

      Overrides:
      [`setString`](XMLType.md) in class [`XMLType`](XMLType.md)

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setCharacterStream

          public java.io.Writer setCharacterStream()
                                            throws java.sql.SQLException

      SQLXML method Set the string value containing the XML data to the XMLType.
      Specified by:
      `setCharacterStream` in interface `java.sql.SQLXML`

      Overrides:
      [`setCharacterStream`](XMLType.md) in class [`XMLType`](XMLType.md)

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setBinaryStream

          public java.io.OutputStream setBinaryStream()
                                               throws java.sql.SQLException

      SQLXML method Set the string value containing the XML data to the XMLType.
      Specified by:
      `setBinaryStream` in interface `java.sql.SQLXML`

      Overrides:
      [`setBinaryStream`](XMLType.md) in class [`XMLType`](XMLType.md)

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setResult

          public <T extends Result> T setResult(java.lang.Class<T> resultClass)
                                         throws java.sql.SQLException

      Specified by:
      `setResult` in interface `java.sql.SQLXML`

      Overrides:
      [`setResult`](XMLType.md) in class [`XMLType`](XMLType.md)

      Throws:
      `java.sql.SQLException`

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](RealInputStream.md)**
- **[Next Class](XDBError.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
