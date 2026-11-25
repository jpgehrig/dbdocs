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

- **[Prev Class](XMLContext.md)**
- **[Next Class](XMLTypeFactory.md)**

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

## **Class XMLType**

- **java.lang.Object**

- - **oracle.sql.Datum**

  - - **oracle.sql.DatumWithConnection**

    - - **oracle.sql.OPAQUE**

      - - **oracle.xdb.XMLType**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, java.sql.SQLXML, oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.ObjectData, oracle.jdbc.internal.OracleDatumWithConnection, oracle.jdbc.internal.XMLTypeIntf, oracle.jdbc.OracleOpaque, oracle.sql.ORAData**

  <!-- -->

  **Direct Known Subclasses:**
  **[SQLXMLType](SQLXMLType.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLType
      extends oracle.sql.OPAQUE
      implements oracle.jdbc.internal.XMLTypeIntf

  **Class that deals with XMLType objects.**
  **See Also:**
  **[Serialized Form](../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                       |
    |---------------------------|---------------------------------------------------------------------------------------------|
    | `static int`              | `_SQL_TYPECODE`<br>Deprecated.                                                              |
    | `static int`              | `CONNTYPE_KPRB`<br>Deprecated.                                                              |
    | `static int`              | `CONNTYPE_OCI8`<br>Deprecated.                                                              |
    | `static int`              | `CONNTYPE_THIN`<br>Deprecated.                                                              |
    | `static java.lang.String` | `DECODE_ON_CLIENT`<br>Client-side binary XML decoding property name.                        |
    | `static int`              | `DEF_INDENT`<br>Deprecated.                                                                 |
    | `static java.lang.String` | `ENCODE_ON_CLIENT`<br>Client-side binary XML encoding property name.                        |
    | `static int`              | `MAX_INDENT`<br>Deprecated.                                                                 |
    | `static int`              | `MAX_PFLAG`<br>Deprecated.                                                                  |
    | `static int`              | `PRINT_DEFAULT_PROPERTY`<br>Deprecated.                                                     |
    | `static int`              | `PRINT_NOPRETTY`<br>Deprecated.                                                             |
    | `static int`              | `PRINT_PRETTY`<br>Deprecated.                                                               |
    | `static int`              | `XMLTYPE_PICKLE_AS_BINXML`                                                                  |
    | `static int`              | `XMLTYPE_PICKLE_AS_TEXT`<br>Flags to specify pickle preference, used in setPicklePreference |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XMLType``(java.sql.Connection conn, oracle.sql.BLOB xmlval, int csid)`<br>Deprecated. <br>use oracle.jdbc.OracleBlob someBlob; SQLXML newXML = someBlob.toSQLXML();                                                                                                         |
    | `XMLType``(java.sql.Connection conn, byte[] bytes)`<br>Deprecated.                                                                                                                                                                                                           |
    | `XMLType``(java.sql.Connection conn, oracle.sql.CLOB xmlval)`<br>Deprecated. <br>use createXML(Connection, OracleClob);                                                                                                                                                      |
    | `XMLType``(java.sql.Connection conn, oracle.sql.CLOB xmlval, java.lang.String schemaURL, boolean wellformed, boolean valid)`<br>Deprecated. <br>use oracle.jdbc.OracleClob someClob; SQLXML newXML = someClob.toSQLXML(); newXML.setSchemaURL(surl);                         |
    | `XMLType``(java.sql.Connection conn, `[`Document`](../../org/w3c/dom/Document.md)` domdoc)`<br>Deprecated. <br>use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); DOMResult domResult = newXML.setResult(DOMResult.class); domResult.setNode(myNode);    |
    | `XMLType``(java.sql.Connection conn, java.io.InputStream is)`<br>Construct an XMLType given a InputStream containing the XML data.                                                                                                                                           |
    | `XMLType``(java.sql.Connection conn, `[`Node`](../../org/w3c/dom/Node.md)` node)`<br>Deprecated. <br>use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); DOMResult domResult = newXML.setResult(DOMResult.class); domResult.setNode(myNode);              |
    | `XMLType``(java.sql.Connection conn, java.lang.String xmlval)`<br>Deprecated. <br>use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval);                                                                                           |
    | `XMLType``(java.sql.Connection conn, java.lang.String xmlval, java.lang.String schemaURL, boolean wellformed, boolean valid)`<br>Deprecated. <br>use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval); newXML.setSchemaURL(surl); |
    | `XMLType``(oracle.sql.OpaqueDescriptor type, java.sql.Connection conn, java.lang.Object value)`<br>Deprecated.                                                                                                                                                               |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                                                                                                                                         |
    |------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                                                          | `cleanupCache``(boolean forcemode)`<br>Clean-up method for an internal cache used for Binary XML decoding.                                                                                                                                                                     |
    | `void`                                                                 | `close``()`<br>Deprecated. <br>use SQLXML sqlxml; sqlxml.free();                                                                                                                                                                                                               |
    | `XMLType`                                                              | `createSchemaBasedXML``(java.lang.String schemaURL)`<br>Deprecated.                                                                                                                                                                                                            |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, oracle.sql.CLOB xmlval)`<br>Deprecated. <br>use createXML(Connection, OracleClob);                                                                                                                                                      |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, oracle.sql.CLOB xmlval, java.lang.String schemaURL, boolean wellformed, boolean valid)`<br>Deprecated. <br>use oracle.jdbc.OracleClob someClob; SQLXML newXML = someClob.toSQLXML(); newXML.setSchemaURL(surl);                         |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, `[`Document`](../../org/w3c/dom/Document.md)` domdoc)`<br>Deprecated. <br>use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); DOMResult domResult = newXML.setResult(DOMResult.class); domResult.setNode(myNode);    |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, java.io.InputStream is)`<br>Create an XMLType given a InputStream containing the XML data.                                                                                                                                              |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, oracle.jdbc.OracleBlob xmlval, int csid)`<br>Create an XMLType given a OracleBlob containing the XML data                                                                                                                               |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, oracle.jdbc.OracleClob xmlval)`<br>Create an XMLType given a OracleClob containing the XML data                                                                                                                                         |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, oracle.jdbc.OracleClob xmlval, java.lang.String schemaURL)`<br>Create an XMLType given a OracleClob containing the XML data                                                                                                             |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, java.lang.String xmlval)`<br>Deprecated. <br>use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval);                                                                                           |
    | `static XMLType`                                                       | `createXML``(java.sql.Connection conn, java.lang.String xmlval, java.lang.String schemaURL, boolean wellformed, boolean valid)`<br>Deprecated. <br>use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval); newXML.setSchemaURL(surl); |
    | `static XMLType`                                                       | `createXML``(oracle.sql.OPAQUE opq)`<br>Deprecated. <br>Use SQLXML newXML = resultSet.getSQLXML(columnNumber);                                                                                                                                                                 |
    | `boolean`                                                              | `existsNode``(java.lang.String xpath, java.lang.String nsmap)`<br>Deprecated.                                                                                                                                                                                                  |
    | `XMLType`                                                              | `extract``(java.lang.String xpath, java.lang.String nsmap)`<br>Deprecated.                                                                                                                                                                                                     |
    | `void`                                                                 | `free``()`                                                                                                                                                                                                                                                                     |
    | `java.io.InputStream`                                                  | `getBinaryStream``()`                                                                                                                                                                                                                                                          |
    | `oracle.sql.BLOB`                                                      | `getBlobVal``(int csid)`<br>Deprecated. <br>use toBlob(int csid)                                                                                                                                                                                                               |
    | `oracle.sql.BLOB`                                                      | `getBlobVal``(int csid, int pflag, int indent)`<br>Deprecated. <br>use toBlob(int csid)                                                                                                                                                                                        |
    | `java.io.Reader`                                                       | `getCharacterStream``()`                                                                                                                                                                                                                                                       |
    | `oracle.sql.CLOB`                                                      | `getClobVal``()`<br>Deprecated. <br>- use toClob()                                                                                                                                                                                                                             |
    | `oracle.sql.CLOB`                                                      | `getClobVal``(int pflag, int indent)`<br>Deprecated. <br>- use toClob()                                                                                                                                                                                                        |
    | [`Document`](../../org/w3c/dom/Document.md)                            | `getDocument``()`<br>Deprecated. <br>- use SQLXML sqlxml; DOMSource domSource = sqlxml.getSource(DOMSource.class); Document doc = (Document)domSource.getNode();                                                                                                               |
    | [`XDBDocFragment`](dom/XDBDocFragment.md)                              | `getDocumentFragment``()`<br>Deprecated. <br>- use SQLXML sqlxml; DOMSource domSource = sqlxml.getSource(DOMSource.class); Document doc = (Document)domSource.getNode();                                                                                                       |
    | [`Document`](../../org/w3c/dom/Document.md)                            | `getDOM``()`<br>Deprecated. <br>- use SQLXML sqlxml; DOMSource domSource = sqlxml.getSource(DOMSource.class); Document doc = (Document)domSource.getNode();                                                                                                                    |
    | `java.io.InputStream`                                                  | `getInputStream``()`<br>Deprecated. <br>- use SQLXML sqlxml; InputStream is = sqlxml.getBinaryStream()                                                                                                                                                                         |
    | `java.io.InputStream`                                                  | `getInputStream``(int pflag, int indent)`<br>Deprecated. <br>- use SQLXML sqlxml; InputStream is = sqlxml.getBinaryStream()                                                                                                                                                    |
    | `java.lang.String`                                                     | `getNamespace``()`<br>Deprecated.                                                                                                                                                                                                                                              |
    | `java.lang.String`                                                     | `getRootElement``()`<br>Deprecated.                                                                                                                                                                                                                                            |
    | `java.lang.String`                                                     | `getSchemaURL``()`<br>Return the schema URL (i.e. location of the schema to which this XMLType conforms)                                                                                                                                                                       |
    | `<T extends `[`Source`](../../javax/xml/transform/Source.md)`>`<br>`T` | `getSource``(java.lang.Class<T> sourceClass)`                                                                                                                                                                                                                                  |
    | `java.lang.String`                                                     | `getString``()`                                                                                                                                                                                                                                                                |
    | `java.lang.String`                                                     | `getStringVal``()`<br>Deprecated. <br>- use SQLXML sqlxml; String s = sqlxml.getString()                                                                                                                                                                                       |
    | `java.lang.String`                                                     | `getStringVal``(int pflag, int indent)`<br>Deprecated. <br>- use SQLXML sqlxml; String s = sqlxml.getString()                                                                                                                                                                  |
    | `boolean`                                                              | `isBinXml``()`<br>Function to check if the XMLType is schema based.                                                                                                                                                                                                            |
    | `boolean`                                                              | `isFragment``()`<br>Function to check if the XMLType is a regular document or a document fragment.                                                                                                                                                                             |
    | `boolean`                                                              | `isSchemaBased``()`<br>Function to check if the XMLType is schema based.                                                                                                                                                                                                       |
    | `boolean`                                                              | `isSchemaValid``(java.lang.String schurl, java.lang.String elname)`<br>Function to check if the XMLType is schema based.                                                                                                                                                       |
    | `boolean`                                                              | `isSchemaValidated``()`<br>Return TRUE if the document has been validated against its schema                                                                                                                                                                                   |
    | `void`                                                                 | `schemaValidate``()`<br>Validate the schema-based document against its own schema.                                                                                                                                                                                             |
    | `java.io.OutputStream`                                                 | `setBinaryStream``()`                                                                                                                                                                                                                                                          |
    | `void`                                                                 | `setBinaryXML``()`<br>Function to mark the XML type as Binary XML                                                                                                                                                                                                              |
    | `void`                                                                 | `setBinaryXMLEncoding``(java.lang.String encoding)`<br>Sets the client requested encoding for retrieving Binary XML.                                                                                                                                                           |
    | `java.io.Writer`                                                       | `setCharacterStream``()`                                                                                                                                                                                                                                                       |
    | `void`                                                                 | `setMetadataConn``(java.lang.Object metaconn)`<br>Function to set the metadata connection to be used for getting Binary XML token data                                                                                                                                         |
    | `void`                                                                 | `setPicklePreference``(int pref)`<br>Function to set how the XMLType will be sent across the wire.                                                                                                                                                                             |
    | `<T extends `[`Result`](../../javax/xml/transform/Result.md)`>`<br>`T` | `setResult``(java.lang.Class<T> resultClass)`                                                                                                                                                                                                                                  |
    | `void`                                                                 | `setSchemaURL``(java.lang.String schemaURL)`<br>This function sets schema URL.                                                                                                                                                                                                 |
    | `void`                                                                 | `setSchemaValidated``(boolean validateFlag)`<br>This function sets the VALIDATED flag to indicate that the XMLType has been validated or not.                                                                                                                                  |
    | `void`                                                                 | `setString``(java.lang.String str)`                                                                                                                                                                                                                                            |
    | `oracle.jdbc.OracleBlob`                                               | `toBlob``(int csid)`<br>Get the OracleBlob value containing the XMLdata from the XMLType                                                                                                                                                                                       |
    | `oracle.jdbc.OracleClob`                                               | `toClob``()`<br>Get the OracleClob value containing the XMLdata from the XMLType                                                                                                                                                                                               |
    | `XMLType`                                                              | `transform``(XMLType xsldoc, java.lang.String parammap)`<br>Function to transform the XMLType using the given XSL document.                                                                                                                                                    |
    | `void`                                                                 | `writeToOutputStream``(java.io.OutputStream os)`<br>Deprecated.                                                                                                                                                                                                                |
    | `void`                                                                 | `writeToOutputStream``(java.io.OutputStream os, int pflag, int indent)`<br>Deprecated.                                                                                                                                                                                         |

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

- - ### Field Detail

    - #### \_SQL_TYPECODE

          public static final int _SQL_TYPECODE

      Deprecated. 
      A constant set to OPAQUE oracle type. Required for the ORADATA interface.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### ENCODE_ON_CLIENT

          public static final java.lang.String ENCODE_ON_CLIENT

      Client-side binary XML encoding property name.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DECODE_ON_CLIENT

          public static final java.lang.String DECODE_ON_CLIENT

      Client-side binary XML decoding property name.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNTYPE_THIN

          public static final int CONNTYPE_THIN

      Deprecated. 
      Thin connection type.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNTYPE_OCI8

          public static final int CONNTYPE_OCI8

      Deprecated. 
      OCI8 connection type.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CONNTYPE_KPRB

          public static final int CONNTYPE_KPRB

      Deprecated. 
      KPRB connection type.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DEF_INDENT

          public static final int DEF_INDENT

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### MAX_INDENT

          public static final int MAX_INDENT

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### MAX_PFLAG

          public static final int MAX_PFLAG

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PRINT_DEFAULT_PROPERTY

          public static final int PRINT_DEFAULT_PROPERTY

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PRINT_PRETTY

          public static final int PRINT_PRETTY

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PRINT_NOPRETTY

          public static final int PRINT_NOPRETTY

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### XMLTYPE_PICKLE_AS_TEXT

          public static final int XMLTYPE_PICKLE_AS_TEXT

      Flags to specify pickle preference, used in setPicklePreference
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### XMLTYPE_PICKLE_AS_BINXML

          public static final int XMLTYPE_PICKLE_AS_BINXML

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         java.lang.String xmlval)
                  throws java.sql.SQLException

      Deprecated. use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval);
      Construct an XMLType given the string containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the string containing the XML data

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         java.lang.String xmlval,
                         java.lang.String schemaURL,
                         boolean wellformed,
                         boolean valid)
                  throws java.sql.SQLException

      Deprecated. use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval); newXML.setSchemaURL(surl);
      Construct an XMLType given the string containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the string containing the XML data

      `schemaURL` - the schema URL for the XMLType

      `wellformed` - XML document is well-formed

      `valid` - XML document is valid

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         oracle.sql.CLOB xmlval)
                  throws java.sql.SQLException

      Deprecated. use createXML(Connection, OracleClob);
      Construct an XMLType given a CLOB containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the CLOB containing the XML data

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         oracle.sql.CLOB xmlval,
                         java.lang.String schemaURL,
                         boolean wellformed,
                         boolean valid)
                  throws java.sql.SQLException

      Deprecated. use oracle.jdbc.OracleClob someClob; SQLXML newXML = someClob.toSQLXML(); newXML.setSchemaURL(surl);
      Construct an XMLType given a CLOB containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the CLOB containing the XML data

      `schemaURL` - the schema URL for the XMLType

      `wellformed` - XML document is well-formed

      `valid` - XML document is valid

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         oracle.sql.BLOB xmlval,
                         int csid)
                  throws java.sql.SQLException

      Deprecated. use oracle.jdbc.OracleBlob someBlob; SQLXML newXML = someBlob.toSQLXML();
      Construct an XMLType given a BLOB containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the BLOB containing the XML data

      `csid` - the charset id.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         java.io.InputStream is)
                  throws java.sql.SQLException

      Construct an XMLType given a InputStream containing the XML data. Note: This takes the bytes "as is" and puts them into the server. Data must be in the database characterset.
      Parameters:
      `conn` - the connection object to be used.

      `is` - the InputStream containing the XML data.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(oracle.sql.OpaqueDescriptor type,
                         java.sql.Connection conn,
                         java.lang.Object value)
                  throws java.sql.SQLException

      Deprecated. 
      Create an XMLType given an opaque descriptor, connection and a pickled image.
      Parameters:
      `type` - the opaque type descriptor to be used.

      `conn` - the connection object to be used.

      `value` - the pickled image bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         Document domdoc)
                  throws java.sql.SQLException

      Deprecated. use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); DOMResult domResult = newXML.setResult(DOMResult.class); domResult.setNode(myNode);
      Constructor to create an XMLType given an instance of the DOM document
      Parameters:
      `domdoc` - the DOM Document which represents the DOM tree

      `conn` - the connection object to be used.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         Node node)
                  throws java.sql.SQLException

      Deprecated. use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); DOMResult domResult = newXML.setResult(DOMResult.class); domResult.setNode(myNode);
      Constructor to create an XMLType given an instance of the DOM Node
      Parameters:
      `conn` - the JDBC Connection (only THIN supported)

      `node` - the DOM node

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### XMLType

          public XMLType(java.sql.Connection conn,
                         byte[] bytes)
                  throws java.sql.SQLException

      Deprecated. 
      Create an XMLType given an XMLType image, as bytes
      Parameters:
      `conn` - the JDBC Connection (only THIN supported)

      `bytes` - the image bytes

      Throws:
      `java.sql.SQLException`

  <!-- -->

  - ### Method Detail

    - #### setPicklePreference

          public void setPicklePreference(int pref)
                                   throws java.sql.SQLException

      Function to set how the XMLType will be sent across the wire. i.e. as Binary XML or text
      Parameters:
      `pref` - XMLTYPE_PICKLE_AS_TEXT or XMLTYPE_PICKLE_AS_BINXML

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setMetadataConn

          public void setMetadataConn(java.lang.Object metaconn)
                               throws java.sql.SQLException

      Function to set the metadata connection to be used for getting Binary XML token data
      Parameters:
      `metaconn` - Metadata connection of type Connection

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setBinaryXML

          public void setBinaryXML()
                            throws java.sql.SQLException

      Function to mark the XML type as Binary XML
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(oracle.sql.OPAQUE opq)
                                   throws java.sql.SQLException

      Deprecated. Use SQLXML newXML = resultSet.getSQLXML(columnNumber);
      Create an XMLType given the opaque type containing the XMLType bytes
      Parameters:
      `opq` - the opaque data object from which the XMLType is to be generated

      Returns:
      the created XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          java.lang.String xmlval)
                                   throws java.sql.SQLException

      Deprecated. use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval);
      Create an XMLType given the string containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the string containing the XML data

      Returns:
      the created XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          java.lang.String xmlval,
                                          java.lang.String schemaURL,
                                          boolean wellformed,
                                          boolean valid)
                                   throws java.sql.SQLException

      Deprecated. use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); newXML.setString(xmlval); newXML.setSchemaURL(surl);
      Create an XMLType given the string containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the string containing the XML data

      `schemaURL` - the schema URL for the XMLType

      `wellformed` - XML document is well-formed

      `valid` - XML document is valid

      Returns:
      the created XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          oracle.sql.CLOB xmlval)
                                   throws java.sql.SQLException

      Deprecated. use createXML(Connection, OracleClob);
      Create an XMLType given a CLOB containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the CLOB containing the XML data

      Returns:
      the created XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          oracle.sql.CLOB xmlval,
                                          java.lang.String schemaURL,
                                          boolean wellformed,
                                          boolean valid)
                                   throws java.sql.SQLException

      Deprecated. use oracle.jdbc.OracleClob someClob; SQLXML newXML = someClob.toSQLXML(); newXML.setSchemaURL(surl);
      Create an XMLType given a CLOB containing the XML data
      Parameters:
      `conn` - the connection object to be used.

      `xmlval` - the CLOB containing the XML data

      `schemaURL` - the schema URL for the XMLType

      `wellformed` - XML document is well-formed

      `valid` - XML document is valid

      Returns:
      the created XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          java.io.InputStream is)
                                   throws java.sql.SQLException

      Create an XMLType given a InputStream containing the XML data. Note: This takes the bytes from the InputStream "as is", and sends them into the server. This assumes data is in the database characterset.
      Parameters:
      `conn` - the connection object to be used.

      `is` - the InputStream containing the XML data

      Returns:
      the created XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getStringVal

          public java.lang.String getStringVal()
                                        throws java.sql.SQLException

      Deprecated. - use SQLXML sqlxml; String s = sqlxml.getString()
      Get the string value containing the XML data from the XMLType.
      Returns:
      the string containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getStringVal

          public java.lang.String getStringVal(int pflag,
                                               int indent)
                                        throws java.sql.SQLException

      Deprecated. - use SQLXML sqlxml; String s = sqlxml.getString()
      Get the string value containing the XML data from the XMLType.
      Parameters:
      `pflag` - flags to control print

      `indent` - indent output by "indent" characters

      Returns:
      the string containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getClobVal

          public oracle.sql.CLOB getClobVal()
                                     throws java.sql.SQLException

      Deprecated. - use toClob()
      Get the CLOB value containing the XML data from the XMLType. Note: The lob might be a temporary one and any code should check for isTemporary and free the lob if necessary.
      Returns:
      the CLOB containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getClobVal

          public oracle.sql.CLOB getClobVal(int pflag,
                                            int indent)
                                     throws java.sql.SQLException

      Deprecated. - use toClob()
      Get the CLOB value containing the XML data from the XMLType. Note: The lob might be a temporary one and any code should check for isTemporary and free the lob if necessary.
      Parameters:
      `pflag` - flags to control print

      `indent` - indent output by "indent" characters

      Returns:
      the CLOB containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getBlobVal

          public oracle.sql.BLOB getBlobVal(int csid)
                                     throws java.sql.SQLException

      Deprecated. use toBlob(int csid)
      Get the BLOB value containing the XML data from the XMLType. Note: The lob might be a temporary one and any code should check for isTemporary and free the lob if necessary.
      Parameters:
      `csid` - The character set ID.

      Returns:
      the BLOB containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getBlobVal

          public oracle.sql.BLOB getBlobVal(int csid,
                                            int pflag,
                                            int indent)
                                     throws java.sql.SQLException

      Deprecated. use toBlob(int csid)
      Get the BLOB value containing the XML data from the XMLType. Note: The lob might be a temporary one and any code should check for isTemporary and free the lob if necessary.
      Parameters:
      `csid` - The character set ID.

      `pflag` - flags to control print

      `indent` - indent output by "indent" characters

      Returns:
      the BLOB containing the XML data bytes.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getInputStream

          public java.io.InputStream getInputStream()
                                             throws java.sql.SQLException

      Deprecated. - use SQLXML sqlxml; InputStream is = sqlxml.getBinaryStream()
      Get an InputStream from the XMLType, applications can read XML data from the stream
      Returns:
      the InputStream for the XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getInputStream

          public java.io.InputStream getInputStream(int pflag,
                                                    int indent)
                                             throws java.sql.SQLException

      Deprecated. - use SQLXML sqlxml; InputStream is = sqlxml.getBinaryStream()
      Get an InputStream from the XMLType, applications can read XML data from the stream
      Parameters:
      `pflag` - flags to control print

      `indent` - indent output by "indent" characters

      Returns:
      the InputStream for the XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### writeToOutputStream

          public void writeToOutputStream(java.io.OutputStream os)
                                   throws java.sql.SQLException

      Deprecated. 
      Write the contents of the XMLType to an OutputStream
      Parameters:
      `os` - The OutputStream to which the contents are written.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### writeToOutputStream

          public void writeToOutputStream(java.io.OutputStream os,
                                          int pflag,
                                          int indent)
                                   throws java.sql.SQLException

      Deprecated. 
      Write the contents of the XMLType to an OutputStream
      Parameters:
      `os` - The OutputStream to which the contents are written.

      `pflag` - flags to control print

      `indent` - indent output by "indent" characters

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          Document domdoc)
                                   throws java.sql.SQLException

      Deprecated. use java.sql.Connection myconn; SQLXML newXML = myconn.createSQLXML(); DOMResult domResult = newXML.setResult(DOMResult.class); domResult.setNode(myNode);
      Create an XMLType given an instance of the DOM document
      Parameters:
      `domdoc` - the DOM Document which represents the DOM tree

      `conn` - the JDBC Connection

      Returns:
      the constructed XMLType.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### extract

          public XMLType extract(java.lang.String xpath,
                                 java.lang.String nsmap)
                          throws java.sql.SQLException

      Deprecated. 
      Function to extract the given set of nodes from the XMLType. This set of nodes is specified by the xpath expression. The original XMLType remains unchanged. Works only in the thick case
      Parameters:
      `xpath` - the xpath expression which specifies the nodes to search for.

      `nsmap` - the map of namespaces which resolves the prefixes in the xpath expression. format is "xmlns=a.com xmlns:b=b.com"

      Returns:
      XMLType which contains the extracted nodes. null if no nodes match the specified expression.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### existsNode

          public boolean existsNode(java.lang.String xpath,
                                    java.lang.String nsmap)
                             throws java.sql.SQLException

      Deprecated. 
      Function to check for the existence of the given set of nodes in the XMLType. This set of nodes is specified by the xpath expression.
      Parameters:
      `xpath` - the xpath expression which specifies the nodes to search for.

      `nsmap` - the map of namespaces which resolves the prefixes in the xpath expression. format is "xmlns=a.com xmlns:b=b.com"

      Returns:
      TRUE if specified nodes exist in the XMLType else FALSE

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### transform

          public XMLType transform(XMLType xsldoc,
                                   java.lang.String parammap)
                            throws java.sql.SQLException

      Function to transform the XMLType using the given XSL document. The new (transformed) XML document is returned.
      Parameters:
      `xsldoc` - the XSL document to be applied to the XMLType

      `parammap` - the top level parameters to be passed to the XSL transformation. This should be of the format "a=b c=d e=f". This can be null.

      Returns:
      the transformed XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### isFragment

          public boolean isFragment()
                             throws java.sql.SQLException

      Function to check if the XMLType is a regular document or a document fragment.
      Returns:
      TRUE if doc is a fragment else FALSE

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDocumentFragment

          public XDBDocFragment getDocumentFragment()
                                             throws java.sql.SQLException

      Deprecated. - use SQLXML sqlxml; DOMSource domSource = sqlxml.getSource(DOMSource.class); Document doc = (Document)domSource.getNode();
      Function to return XDBDocFragment if XMLType instance is a fragment
      Returns:
      XDDBDocFragment if XMLType instance is a fragment, else null

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### isSchemaValid

          public boolean isSchemaValid(java.lang.String schurl,
                                       java.lang.String elname)
                                throws java.sql.SQLException

      Function to check if the XMLType is schema based.
      Parameters:
      `schurl` - the URL of the schema to be validated against; if this is null then the documents own schema URL is used (if one exists).

      `elname` - the name of the root element of the schema

      Returns:
      TRUE if doc is schema based else FALSE

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createSchemaBasedXML

          public XMLType createSchemaBasedXML(java.lang.String schemaURL)
                                       throws java.sql.SQLException

      Deprecated. 
      Create a schema-based XML
      Parameters:
      `schemaURL` - The schema URL

      Returns:
      an XMLType object based on the given schema

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getRootElement

          public java.lang.String getRootElement()
                                          throws java.sql.SQLException

      Deprecated. 
      Return the root element name
      Returns:
      the root element name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getSchemaURL

          public java.lang.String getSchemaURL()
                                        throws java.sql.SQLException

      Return the schema URL (i.e. location of the schema to which this XMLType conforms)
      Returns:
      the schema URL

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setSchemaURL

          public void setSchemaURL(java.lang.String schemaURL)
                            throws java.sql.SQLException

      This function sets schema URL.
      Parameters:
      `schemaURL` - the schema URL to be set.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### isSchemaBased

          public boolean isSchemaBased()
                                throws java.sql.SQLException

      Function to check if the XMLType is schema based.
      Returns:
      TRUE if doc is schema based else FALSE

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### isBinXml

          public boolean isBinXml()
                           throws java.sql.SQLException

      Function to check if the XMLType is schema based.
      Returns:
      TRUE if doc is schema based else FALSE

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNamespace

          public java.lang.String getNamespace()
                                        throws java.sql.SQLException

      Deprecated. 
      return the default namespace of the XMLType document
      Returns:
      the namespace of the XMLType document

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### schemaValidate

          public void schemaValidate()
                              throws java.sql.SQLException

      Validate the schema-based document against its own schema.
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### isSchemaValidated

          public boolean isSchemaValidated()
                                    throws java.sql.SQLException

      Return TRUE if the document has been validated against its schema
      Returns:
      TRUE if the document has been validated against its schema

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setSchemaValidated

          public void setSchemaValidated(boolean validateFlag)
                                  throws java.sql.SQLException

      This function sets the VALIDATED flag to indicate that the XMLType has been validated or not.
      Parameters:
      `validateFlag` - True indicates that the XMLType has been validated. False indicates that the XMLType has not been validated.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDOM

          public Document getDOM()
                          throws java.sql.SQLException

      Deprecated. - use SQLXML sqlxml; DOMSource domSource = sqlxml.getSource(DOMSource.class); Document doc = (Document)domSource.getNode();
      Gets the DOM document associated with the XMLType. This document is the org.w3c.dom.Document. The caller can perform all the DOM operations on the Document. If the document is a binary document the getDOM function will return null. NOTE: This function is for the old java APIs. Use getDocument() for the unified APIs
      Returns:
      the DOM Document object associated with the XMLType

      Throws:
      `java.sql.SQLException`

      See Also:
      [`Document`](../../org/w3c/dom/Document.md)

    <!-- -->

    - #### getDocument

          public Document getDocument()
                               throws java.sql.SQLException

      Deprecated. - use SQLXML sqlxml; DOMSource domSource = sqlxml.getSource(DOMSource.class); Document doc = (Document)domSource.getNode();
      Gets the DOM document associated with the XMLType. This document is the org.w3c.dom.Document. The caller can perform all the DOM operations on the Document. If the document is a binary document the getDOM function will return null.
      Returns:
      the DOM Document object associated with the XMLType

      Throws:
      `java.sql.SQLException`

      See Also:
      [`Document`](../../org/w3c/dom/Document.md)

    <!-- -->

    - #### close

          public void close()

      Deprecated. use SQLXML sqlxml; sqlxml.free();
      Function to free/close the XMLType. Any operation after this will result in a SQLException. Applications need to call close else a memory leak will result.

    <!-- -->

    - #### setBinaryXMLEncoding

          public void setBinaryXMLEncoding(java.lang.String encoding)
                                    throws java.sql.SQLException

      Sets the client requested encoding for retrieving Binary XML.
      Parameters:
      `encoding` - The encoding.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### cleanupCache

          public static void cleanupCache(boolean forcemode)

      Clean-up method for an internal cache used for Binary XML decoding.
      Parameters:
      `forcemode` - If true, purges the entire cache; otherwise only mappings with values already garbage collected are removed from the cache.

    <!-- -->

    - #### getString

          public java.lang.String getString()
                                     throws java.sql.SQLException

      Specified by:
      `getString` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getBinaryStream

          public java.io.InputStream getBinaryStream()
                                              throws java.sql.SQLException

      Specified by:
      `getBinaryStream` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getCharacterStream

          public java.io.Reader getCharacterStream()
                                            throws java.sql.SQLException

      Specified by:
      `getCharacterStream` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getSource

          public <T extends Source> T getSource(java.lang.Class<T> sourceClass)
                                         throws java.sql.SQLException

      Specified by:
      `getSource` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### free

          public void free()
                    throws java.sql.SQLException

      Specified by:
      `free` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setBinaryStream

          public java.io.OutputStream setBinaryStream()
                                               throws java.sql.SQLException

      Specified by:
      `setBinaryStream` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setResult

          public <T extends Result> T setResult(java.lang.Class<T> resultClass)
                                         throws java.sql.SQLException

      Specified by:
      `setResult` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setCharacterStream

          public java.io.Writer setCharacterStream()
                                            throws java.sql.SQLException

      Specified by:
      `setCharacterStream` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setString

          public void setString(java.lang.String str)
                         throws java.sql.SQLException

      Specified by:
      `setString` in interface `java.sql.SQLXML`

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          oracle.jdbc.OracleClob xmlval)
                                   throws java.sql.SQLException

      Create an XMLType given a OracleClob containing the XML data
      Parameters:
      `conn` - the connection object to be used

      `xmlval` - the OracleClob containing the XML data

      Returns:
      the created the XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          oracle.jdbc.OracleClob xmlval,
                                          java.lang.String schemaURL)
                                   throws java.sql.SQLException

      Create an XMLType given a OracleClob containing the XML data
      Parameters:
      `conn` - the connection object to be used

      `xmlval` - the OracleClob containing the XML data

      `schemaURL` - the schema URL for the XMLType

      Returns:
      the created the XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createXML

          public static XMLType createXML(java.sql.Connection conn,
                                          oracle.jdbc.OracleBlob xmlval,
                                          int csid)
                                   throws java.sql.SQLException

      Create an XMLType given a OracleBlob containing the XML data
      Parameters:
      `conn` - the connection object to be used

      `xmlval` - the OracleBlob containing the XML data

      `csid` - the character set id

      Returns:
      the created the XMLType

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### toClob

          public oracle.jdbc.OracleClob toClob()
                                        throws java.sql.SQLException

      Get the OracleClob value containing the XMLdata from the XMLType
      Returns:
      the OracleClob containing the XML data bytes

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### toBlob

          public oracle.jdbc.OracleBlob toBlob(int csid)
                                        throws java.sql.SQLException

      Get the OracleBlob value containing the XMLdata from the XMLType
      Parameters:
      `csid` - the character set id

      Returns:
      the OracleBlob containing the XML data bytes

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

- **[Prev Class](XMLContext.md)**
- **[Next Class](XMLTypeFactory.md)**

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
