Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.sql.query**

## **Class OracleXMLQuery**

- **java.lang.Object**

- - **oracle.xml.sql.query.OracleXMLQuery**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class OracleXMLQuery
      extends java.lang.Object

  **This generates XML from a SQL query. A typical sequence might look like this:**
        import java.sql.*;
        import oracle.xml.sql.query.*;
        import oracle.jdbc.*;

        public class sample
        {
          public static void main(String args[]) throws Exception
          {
            DriverManager.registerDriver(new oracle.jdbc.OracleDriver());
            Connection conn =
                DriverManager.getConnection("jdbc:oracle:oci8:scott/tiger@");
            OracleXMLQuery qry = new OracleXMLQuery(conn, "select * from emp");
            System.out.println(qry.getXMLString());
            conn.close();
          }
        }


<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                      |
    |---------------------------|----------------------------------------------------------------------------|
    | `static int`              | `DTD`<br>Specifies that a DTD is to be generated                           |
    | `static java.lang.String` | `ERROR_TAG`<br>Specifies the default tag name for the `ERROR` document     |
    | `static int`              | `MAXROWS_ALL`<br>Specifies that all rows should be included in the result  |
    | `static int`              | `MAXROWS_DEFAULT`<br>Deprecated. <br>since v2.0; Use `MAXROWS_ALL` instead |
    | `static int`              | `MAXROWS_NONE`<br>Deprecated. <br>since v2.0; Use `0` instead              |
    | `static int`              | `NONE`<br>Specifies that a DTD is not to be generated.                     |
    | `static java.lang.String` | `ROW_TAG`<br>Specifies the default tag name for `ROW` elements.            |
    | `static java.lang.String` | `ROWIDATTR_TAG`<br>Specifies the default tag name for the `ROWIDATTR`.     |
    | `static java.lang.String` | `ROWSET_TAG`<br>Specifies the default tag name for the document.           |
    | `static int`              | `SCHEMA`<br>Specifies that an XML schema is not to be generated.           |
    | `static int`              | `SKIPROWS_ALL`<br>Specifies that all rows be skipped in the result.        |
    | `static int`              | `SKIPROWS_DEFAULT`<br>Deprecated. <br>since v2.0; Use `0` instead          |
    | `static int`              | `SKIPROWS_NONE`<br>Deprecated. <br>since v2.0; Use `0` instead             |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                          |
    |----------------------------------------------------------------------------------------------------------------------|
    | `OracleXMLQuery``(java.sql.Connection conn, java.sql.ResultSet rset)`<br>Constructor for the OracleXMLQueryObject.   |
    | `OracleXMLQuery``(java.sql.Connection conn, java.lang.String query)`<br>Constructor for the `OracleXMLQuery` object. |
    | `OracleXMLQuery``(oracle.xml.sql.dataset.OracleXMLDataSet dset)`<br>Constructor for the OracleXMLQueryObject.        |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                    |
    |-------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                | `bindValue``(java.lang.String bindName, java.lang.String bindValue)`<br>Sets a bind name/value pair.                                                                                                                                      |
    | `void`                                                | `clearBindValues``()`<br>Clears bind name/value pairs.                                                                                                                                                                                    |
    | `void`                                                | `close``()`<br>Closes open resources created by the `OracleXML` engine.                                                                                                                                                                   |
    | `long`                                                | `getNumRowsProcessed``()`<br>Returns the number of rows processed.                                                                                                                                                                        |
    | `void`                                                | `getXML``(oracle.xml.sql.docgen.OracleXMLDocGen doc, int metaType)`<br>NOTE: THIS IS AN INTERNAL CALL Transforms the object-relational data, specified in the constructor, into an XML document which is returned via the `doc` argument. |
    | [`Document`](../../../../org/w3c/dom/Document.md)     | `getXMLDOM``()`<br>Transforms the object-relational data, specified in the constructor, into an XML document.                                                                                                                             |
    | [`Document`](../../../../org/w3c/dom/Document.md)     | `getXMLDOM``(boolean withDTD)`<br>Deprecated. <br>since 1.2.1; please use getXMLDOM(int) instead                                                                                                                                          |
    | [`Document`](../../../../org/w3c/dom/Document.md)     | `getXMLDOM``(int metaType)`<br>Transforms the object-relational data, specified in the constructor, into an XML document.                                                                                                                 |
    | [`Document`](../../../../org/w3c/dom/Document.md)     | `getXMLDOM``(`[`Node`](../../../../org/w3c/dom/Node.md)` root)`<br>Transforms the object-relational data, specified in the constructor, into an XML document.                                                                             |
    | [`Document`](../../../../org/w3c/dom/Document.md)     | `getXMLDOM``(`[`Node`](../../../../org/w3c/dom/Node.md)` root, int metaType)`<br>Transforms the object-relational data, specified in the constructor, into XML.                                                                           |
    | `java.lang.String`                                    | `getXMLMetaData``(int metaType, boolean withVer)`<br>Returns either the DTD or the XMLSchema for the XML document generated by `getXML` calls.                                                                                            |
    | `void`                                                | `getXMLSAX``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` sax)`<br>Transforms the object-relational data, specified in the constructor, into an XML document in SAX form.                                              |
    | [`Document`](../../../../org/w3c/dom/Document.md)`[]` | `getXMLSchema``()`<br>Generates XML Schema(s) corresponding to the query.                                                                                                                                                                 |
    | `void`                                                | `getXMLStream``(`[`Node`](../../../../org/w3c/dom/Node.md)` root, int metaType, java.io.Writer out)`<br>Transforms the object-relational data, specified in the constructor, into XML.                                                    |
    | `java.lang.String`                                    | `getXMLString``()`<br>Transforms the object-relational data, specified in the constructor, into an XML document.                                                                                                                          |
    | `java.lang.String`                                    | `getXMLString``(boolean withDTD)`<br>Deprecated. <br>since 1.2.1; please use getXMLString(int) instead                                                                                                                                    |
    | `java.lang.String`                                    | `getXMLString``(int metaType)`<br>Transforms the object-relational data, specified in the constructor, into an XML document.                                                                                                              |
    | `java.lang.String`                                    | `getXMLString``(`[`Node`](../../../../org/w3c/dom/Node.md)` root)`<br>Transforms the object-relational data, specified in the constructor, into an XML document.                                                                          |
    | `java.lang.String`                                    | `getXMLString``(`[`Node`](../../../../org/w3c/dom/Node.md)` root, int metaType)`<br>Transforms the object-relational data, specified in the constructor, into an XML document.                                                            |
    | `void`                                                | `ignoreEmptyElements``(boolean flag)`<br>Specify if when an element is empty, i.e.                                                                                                                                                        |
    | `void`                                                | `keepCursorState``(boolean alive)`<br>Deprecated. <br>since 1.2.1; use keepObjectOpen instead.                                                                                                                                            |
    | `void`                                                | `keepObjectOpen``(boolean alive)`<br>Specifies whether to keep the input object open after a `getXML()/code> call.`                                                                                                                       |
    | `void`                                                | `removeXSLTParam``(java.lang.String name)`<br>Removes the value of a top-level stylesheet parameter.                                                                                                                                      |
    | `void`                                                | `resetResultSet``()`<br>Resets the result set to start XML generation from the from the first row of the resultset.                                                                                                                       |
    | `void`                                                | `setCollIdAttr``(java.lang.String collIdAttr)`<br>Deprecated. <br>since 1.2.1; please use setCollIdAttrName instead.                                                                                                                      |
    | `void`                                                | `setCollIdAttrName``(java.lang.String attrName)`<br>Sets the name of the collection element separator tag id attribute.                                                                                                                   |
    | `void`                                                | `setDataHeader``(java.io.Reader header, java.lang.String docTag)`<br>Sets the XML data header.                                                                                                                                            |
    | `void`                                                | `setDateFormat``(java.lang.String mask)`<br>Specifies the format of dates used in the XML document.                                                                                                                                       |
    | `void`                                                | `setEncoding``(java.lang.String enc)`<br>Sets the processing instruction for encoding, the PI, in the XML document.                                                                                                                       |
    | `void`                                                | `setErrorTag``(java.lang.String tag)`<br>Sets the tag used to enclose the XML error documents.                                                                                                                                            |
    | `void`                                                | `setException``(java.lang.Exception e)`<br>Allows the user to pass in an exception, and have the XSU handle it.                                                                                                                           |
    | `void`                                                | `setMaxRows``(int rows)`<br>Sets the maximum number of rows to be converted to XML.                                                                                                                                                       |
    | `void`                                                | `setMetaHeader``(java.io.Reader header)`<br>Sets the XML meta header.                                                                                                                                                                     |
    | `void`                                                | `setRaiseException``(boolean flag)`<br>Specifies whether to throw the raised exceptions.                                                                                                                                                  |
    | `void`                                                | `setRaiseNoRowsException``(boolean flag)`<br>Specifies whether to throw an `OracleXMLNoRowsException` if the generated XML document is empty.                                                                                             |
    | `void`                                                | `setRowIdAttrName``(java.lang.String attrName)`<br>Sets the name of the row enclosing tag id attribute.                                                                                                                                   |
    | `void`                                                | `setRowIdAttrValue``(java.lang.String colName)`<br>Specifies the scalar column whose value is assigned to the row id attribute.                                                                                                           |
    | `void`                                                | `setRowIdColumn``(java.lang.String colName)`<br>Deprecated. <br>since 1.2.1 -- please use setRowIdAttrValue instead.                                                                                                                      |
    | `void`                                                | `setRowsetTag``(java.lang.String tag)`<br>Sets the tag used to enclose the XML dataset.                                                                                                                                                   |
    | `void`                                                | `setRowTag``(java.lang.String tag)`<br>Sets the tag to be used to enclose the XML element corresponding to a db. record.                                                                                                                  |
    | `void`                                                | `setSkipRows``(int rows)`<br>Sets the number of rows to skip.                                                                                                                                                                             |
    | `void`                                                | `setSQLToXMLNameEscaping``(boolean flag)`<br>Specifies whether to turn on XML tag escaping for SQL object names, to ensure conversion to valid XML identifiers.                                                                           |
    | `void`                                                | `setStrictLegalXMLCharCheck``(boolean flag)`<br>Tells XSU whether it should do strict checking on the input data (as generated by the query) before generating the XML document.                                                          |
    | `void`                                                | `setStyleSheet``(java.lang.String uri)`<br>Deprecated. <br>since XSU2.0 -- please use `setStylesheetHeader` instead.                                                                                                                      |
    | `void`                                                | `setStyleSheet``(java.lang.String uri, java.lang.String type)`<br>Deprecated. <br>since XSU2.0 -- please use `setStylesheetHeader` instead.                                                                                               |
    | `void`                                                | `setStylesheetHeader``(java.lang.String uri)`<br>Sets the stylesheet header processing instructions in the generated XML document.                                                                                                        |
    | `void`                                                | `setStylesheetHeader``(java.lang.String uri, java.lang.String type)`<br>Sets the stylesheet header processing instructions in the generated XML document.                                                                                 |
    | `void`                                                | `setXSLT``(java.io.Reader stylesheet, java.lang.String ref)`<br>Sets the XSL transformation to be applied to generated XML.                                                                                                               |
    | `void`                                                | `setXSLT``(java.lang.String stylesheet, java.lang.String ref)`<br>Sets the XSL transformation to be applied to generated XML.                                                                                                             |
    | `void`                                                | `setXSLTParam``(java.lang.String name, java.lang.String value)`<br>Sets the value for top-level stylesheet parameter.                                                                                                                     |
    | `void`                                                | `useLowerCaseTagNames``()`<br>Specifies use of lower case for all tag names.                                                                                                                                                              |
    | `void`                                                | `useNullAttributeIndicator``(boolean flag)`<br>Specifies whether to use an XML attribute to indicate NULLness, or by omitting the entity from the XML document.                                                                           |
    | `void`                                                | `useTypeForCollElemTag``(boolean flag)`<br>Specifies the use of collection element's type name as the collection element tag name when called with a `TRUE` value for the `flag` parameter.                                               |
    | `void`                                                | `useUpperCaseTagNames``()`<br>Specifies use of upper case for all tag names.                                                                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### MAXROWS_NONE

          public static final int MAXROWS_NONE

      Deprecated. since v2.0; Use `0` instead
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### MAXROWS_ALL

          public static final int MAXROWS_ALL

      Specifies that all rows should be included in the result
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### MAXROWS_DEFAULT

          public static final int MAXROWS_DEFAULT

      Deprecated. since v2.0; Use `MAXROWS_ALL` instead
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SKIPROWS_NONE

          public static final int SKIPROWS_NONE

      Deprecated. since v2.0; Use `0` instead
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SKIPROWS_ALL

          public static final int SKIPROWS_ALL

      Specifies that all rows be skipped in the result.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SKIPROWS_DEFAULT

          public static final int SKIPROWS_DEFAULT

      Deprecated. since v2.0; Use `0` instead
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NONE

          public static final int NONE

      Specifies that a DTD is not to be generated.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DTD

          public static final int DTD

      Specifies that a DTD is to be generated
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA

          public static final int SCHEMA

      Specifies that an XML schema is not to be generated.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ROWSET_TAG

          public static final java.lang.String ROWSET_TAG

      Specifies the default tag name for the document.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ROW_TAG

          public static final java.lang.String ROW_TAG

      Specifies the default tag name for `ROW` elements.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ERROR_TAG

          public static final java.lang.String ERROR_TAG

      Specifies the default tag name for the `ERROR` document
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ROWIDATTR_TAG

          public static final java.lang.String ROWIDATTR_TAG

      Specifies the default tag name for the `ROWIDATTR`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OracleXMLQuery

          public OracleXMLQuery(java.sql.Connection conn,
                                java.lang.String query)

      Constructor for the `OracleXMLQuery` object.
      Parameters:
      `conn` - database connection

      `query` - the SQL query string

    <!-- -->

    - #### OracleXMLQuery

          public OracleXMLQuery(java.sql.Connection conn,
                                java.sql.ResultSet rset)

      Constructor for the OracleXMLQueryObject.
      Parameters:
      `conn` - database connection

      `rset` - jdbc result set object

    <!-- -->

    - #### OracleXMLQuery

          public OracleXMLQuery(oracle.xml.sql.dataset.OracleXMLDataSet dset)

      Constructor for the OracleXMLQueryObject.
      Parameters:
      `dset` - dataset

  <!-- -->

  - ### Method Detail

    - #### bindValue

          public void bindValue(java.lang.String bindName,
                                java.lang.String bindValue)

      Sets a bind name/value pair. Making this call triggers a dataset refresh.
      Parameters:
      `bindName` - bind name

      `bindValue` - bind value

    <!-- -->

    - #### clearBindValues

          public void clearBindValues()

      Clears bind name/value pairs.

    <!-- -->

    - #### resetResultSet

          public void resetResultSet()

      Resets the result set to start XML generation from the from the first row of the resultset.

    <!-- -->

    - #### getXMLString

          public java.lang.String getXMLString()

      Transforms the object-relational data, specified in the constructor, into an XML document.
      Returns:
      the string representation of the XML document

    <!-- -->

    - #### getXMLString

          public java.lang.String getXMLString(int metaType)

      Transforms the object-relational data, specified in the constructor, into an XML document. The `metaType` argument specifies the type of XML metadata generated with the XML; valid values are `NONE`. and `DTD`, or `SCHEMA` (static fields of this class).
      Parameters:
      `metaType` - type of XML metadata: `NONE`, `DTD`, or `SCHEMA`

      Returns:
      the string representation of the XML document

    <!-- -->

    - #### getXMLString

          public java.lang.String getXMLString(boolean withDTD)

      Deprecated. since 1.2.1; please use getXMLString(int) instead

    <!-- -->

    - #### getXMLString

          public java.lang.String getXMLString(Node root)

      Transforms the object-relational data, specified in the constructor, into an XML document. The `root` argument is considered the "root" element of the XML document if its value is not `null`.
      Parameters:
      `root` - root node to which to append the new XML

      Returns:
      the string representation of the XML document

    <!-- -->

    - #### getXMLString

          public java.lang.String getXMLString(Node root,
                                               int metaType)

      Transforms the object-relational data, specified in the constructor, into an XML document. The `root` argument is considered the "root" element of the XML document if its value is not `null`. The `metaType` argument specifies the type of XML metadata generate with the XML; valid values are `NONE` and `DTD`, static fields of this class. If the root argument is not `null`, the DTD is not generated, even if requested.
      Parameters:
      `root` - root node to which to append the new XML

      `metaType` - type of XML metadata: `NONE`, `DTD`, or `SCHEMA`

      Returns:
      the string representation of the XML document

    <!-- -->

    - #### getXMLDOM

          public Document getXMLDOM()

      Transforms the object-relational data, specified in the constructor, into an XML document.
      Returns:
      the DOM representation of the XML document

    <!-- -->

    - #### getXMLDOM

          public Document getXMLDOM(Node root)

      Transforms the object-relational data, specified in the constructor, into an XML document. The `root` argument is considered the "root" element of the XML document if its value is not `null`.
      Parameters:
      `root` - root node to which to append the new XML

      Returns:
      the string representation of the XML document

    <!-- -->

    - #### getXMLDOM

          public Document getXMLDOM(int metaType)

      Transforms the object-relational data, specified in the constructor, into an XML document. The `metaType` argument specifies the type of XML metadata generate with the XML; valid values are `NONE` and `SCHEMA`, static fields of this class.
      Parameters:
      `metaType` - type of XML metadata: `NONE` or `SCHEMA`

      Returns:
      the string representation of the XML document

    <!-- -->

    - #### getXMLDOM

          public Document getXMLDOM(boolean withDTD)

      Deprecated. since 1.2.1; please use getXMLDOM(int) instead

    <!-- -->

    - #### getXMLDOM

          public Document getXMLDOM(Node root,
                                    int metaType)

      Transforms the object-relational data, specified in the constructor, into XML. If not NULL, the `root` argument is considered the "root" element of the XML doc. The `metaType` argument is used to specify the type of XML metadata the XSU is to generate along with the XML. Currently this value is ignored, and no XML metadata is generated.
      Parameters:
      `root` - root node to which to append the new XML

      `metaType` - the type of XML metadata (NONE, SCHEMA)

      Returns:
      the string representation of the XML document

    <!-- -->

    - #### getXMLStream

          public void getXMLStream(Node root,
                                   int metaType,
                                   java.io.Writer out)

      Transforms the object-relational data, specified in the constructor, into XML. If not NULL, the `root` argument is considered the "root" element of the XML doc. The `metaType` argument is used to specify the type of XML metadata the XSU is to generate along with the XML. The output is written to the stream passed in.
      Parameters:
      `root` - root node to which to append the new XML

      `metaType` - the type of XML metadata (NONE, SCHEMA)

      `out` - the stream to write the output to

    <!-- -->

    - #### getXMLSAX

          public void getXMLSAX(ContentHandler sax)

      Transforms the object-relational data, specified in the constructor, into an XML document in SAX form.
      Parameters:
      `sax` - ContentHandler object to be registered

    <!-- -->

    - #### getXML

          public void getXML(oracle.xml.sql.docgen.OracleXMLDocGen doc,
                             int metaType)

      NOTE: THIS IS AN INTERNAL CALL Transforms the object-relational data, specified in the constructor, into an XML document which is returned via the `doc` argument.
      Parameters:
      `doc` - object containing the generated XML document

      `metaType` - type of XML metadata to generate (NONE or DTD)

    <!-- -->

    - #### getNumRowsProcessed

          public long getNumRowsProcessed()

      Returns the number of rows processed.
      Returns:
      number of rows processed.

    <!-- -->

    - #### getXMLMetaData

          public java.lang.String getXMLMetaData(int metaType,
                                                 boolean withVer)

      Returns either the DTD or the XMLSchema for the XML document generated by `getXML` calls. The `metaType` parameter specifies the type of XML metadata to be generated. The `withVer` parameter specifies whether to generate the version header.
      Parameters:
      `metaType` - type of XML metadata: `NONE` or `DTD`

      `withVer` - `TRUE` to generate the version header

    <!-- -->

    - #### getXMLSchema

          public Document[] getXMLSchema()

      Generates XML Schema(s) corresponding to the query.
      Returns:
      the XML Schema(s)

    <!-- -->

    - #### setMetaHeader

          public void setMetaHeader(java.io.Reader header)

      Sets the XML meta header. The header is inserted at the begining of the metadata section, DTD or XMLSchema, of each XML document generated. The most recently specified meta header is used; a `null` value for the `header` parameter unsets the meta header.
      Parameters:
      `header` - header

    <!-- -->

    - #### setDataHeader

          public void setDataHeader(java.io.Reader header,
                                    java.lang.String docTag)

      Sets the XML data header. The header is inserted at the begining of the query-generated XML entity, the rowset. A `docTag` tag encloses the header and the rowset. The most recently specified data header is used; a `null` value for the `header` parameter unsets the data header.
      Parameters:
      `header` - header

      `docTag` - tag used to enclose the data header and the rowset

    <!-- -->

    - #### setEncoding

          public void setEncoding(java.lang.String enc)

      Sets the processing instruction for encoding, the PI, in the XML document. The default characterset is specified in the encoding PI if the value of the `enc` parameter is `null` or an empty string.
      Parameters:
      `enc` - IANA name for encoding of the XML document

    <!-- -->

    - #### setStrictLegalXMLCharCheck

          public void setStrictLegalXMLCharCheck(boolean flag)

      Tells XSU whether it should do strict checking on the input data (as generated by the query) before generating the XML document. If XSU is using strict checking, and it finds a character that is disallowed in an XML document, then it throws an exception.
      Parameters:
      `flag` - do strict checking?

    <!-- -->

    - #### setDateFormat

          public void setDateFormat(java.lang.String mask)

      Specifies the format of dates used in the XML document. The default setting format, or date mask, should conform to requirements of the `java.text.SimpleDateFormat` class. Setting the `mask` parameter to `null</null> or empty string sets the default mask ``OracleXMLCore.DATE_FORMAT``.`
      Parameters:
      `mask` - the date mask

    <!-- -->

    - #### setRowsetTag

          public void setRowsetTag(java.lang.String tag)

      Sets the tag used to enclose the XML dataset.
      Parameters:
      `tag` - tag name

    <!-- -->

    - #### setRowTag

          public void setRowTag(java.lang.String tag)

      Sets the tag to be used to enclose the XML element corresponding to a db. record.
      Parameters:
      `tag` - tag name

    <!-- -->

    - #### setErrorTag

          public void setErrorTag(java.lang.String tag)

      Sets the tag used to enclose the XML error documents.
      Parameters:
      `tag` - tag name

    <!-- -->

    - #### setRowIdAttrName

          public void setRowIdAttrName(java.lang.String attrName)

      Sets the name of the row enclosing tag id attribute. A `null` or empty string value in the `attrName` omits the row id attribute.
      Parameters:
      `attrName` - attribute name

    <!-- -->

    - #### setRowIdAttrValue

          public void setRowIdAttrValue(java.lang.String colName)

      Specifies the scalar column whose value is assigned to the row id attribute. A `null` or empty string value in the `colName` parameter assigns the row count value to the id attribute, `0`, `1`, `2`, and so on.
      Parameters:
      `colName` - column name

    <!-- -->

    - #### setRowIdColumn

          public void setRowIdColumn(java.lang.String colName)

      Deprecated. since 1.2.1 -- please use setRowIdAttrValue instead.

    <!-- -->

    - #### setCollIdAttrName

          public void setCollIdAttrName(java.lang.String attrName)

      Sets the name of the collection element separator tag id attribute. A `null` or empty string value in the `attrName` omits the separator tag id attribute.
      Parameters:
      `attrName` - attribute name

    <!-- -->

    - #### setCollIdAttr

          public void setCollIdAttr(java.lang.String collIdAttr)

      Deprecated. since 1.2.1; please use setCollIdAttrName instead.

    <!-- -->

    - #### useTypeForCollElemTag

          public void useTypeForCollElemTag(boolean flag)

      Specifies the use of collection element's type name as the collection element tag name when called with a `TRUE` value for the `flag` parameter. By default, the tag name is a concatenation of the tag name and "\_item".
      Parameters:
      `flag` - `TRUE` to use the element's type name as the tag name

    <!-- -->

    - #### useNullAttributeIndicator

          public void useNullAttributeIndicator(boolean flag)

      Specifies whether to use an XML attribute to indicate NULLness, or by omitting the entity from the XML document.
      Parameters:
      `flag` - `TRUE` to use attribute to indicate `null`

    <!-- -->

    - #### ignoreEmptyElements

          public void ignoreEmptyElements(boolean flag)

      Specify if when an element is empty, i.e. \<element/\> or \<element\>\</element\>, should we ignore it in the output or print the empty elements
      Parameters:
      `flag` - true - default which follows W3C XQuery 1.0 spec false - user wants to print the empty elements

    <!-- -->

    - #### setStylesheetHeader

          public void setStylesheetHeader(java.lang.String uri)

      Sets the stylesheet header processing instructions in the generated XML document. A `null` value for `uri` unsets the stylesheet header and type.
      Parameters:
      `uri` - stylesheet URI

    <!-- -->

    - #### setStyleSheet

          public void setStyleSheet(java.lang.String uri)

      Deprecated. since XSU2.0 -- please use `setStylesheetHeader` instead.

    <!-- -->

    - #### setStylesheetHeader

          public void setStylesheetHeader(java.lang.String uri,
                                          java.lang.String type)

      Sets the stylesheet header processing instructions in the generated XML document. A `null` value for `uri` unsets the stylesheet header and type.
      Parameters:
      `uri` - stylesheet URI

      `type` - stylesheet type; default value is `text/xsl`

    <!-- -->

    - #### setStyleSheet

          public void setStyleSheet(java.lang.String uri,
                                    java.lang.String type)

      Deprecated. since XSU2.0 -- please use `setStylesheetHeader` instead.

    <!-- -->

    - #### setXSLT

          public void setXSLT(java.lang.String stylesheet,
                              java.lang.String ref)

      Sets the XSL transformation to be applied to generated XML. Replaces a previously registered stylesheet. To deregister the stylesheet, pass a `null` in the `stylesheet` parameter.
      Parameters:
      `stylesheet` - the stylesheet URI

      `ref` - URL for include, import and external entities

    <!-- -->

    - #### setXSLT

          public void setXSLT(java.io.Reader stylesheet,
                              java.lang.String ref)

      Sets the XSL transformation to be applied to generated XML. Replaces a previously registered stylesheet. To deregister the stylesheet, pass a `null` in the `stylesheet` parameter.
      Parameters:
      `stylesheet` - the stylesheet

      `ref` - URL for include, import and external entities

    <!-- -->

    - #### setXSLTParam

          public void setXSLTParam(java.lang.String name,
                                   java.lang.String value)

      Sets the value for top-level stylesheet parameter. The `value` parameter is expected to be a valid XPath expression; literal `String` values have to be explicitly quoted. This method is a no-op if no stylesheet is registered.
      Parameters:
      `name` - parameter name

      `value` - parameter value as an XPATH expression

    <!-- -->

    - #### removeXSLTParam

          public void removeXSLTParam(java.lang.String name)

      Removes the value of a top-level stylesheet parameter. This method is a no-op if no stylesheet is registered.
      Parameters:
      `name` - parameter name

    <!-- -->

    - #### setSQLToXMLNameEscaping

          public void setSQLToXMLNameEscaping(boolean flag)

      Specifies whether to turn on XML tag escaping for SQL object names, to ensure conversion to valid XML identifiers.
      Parameters:
      `flag` - `TRUE` to turn on SQL to XML escaping

    <!-- -->

    - #### useLowerCaseTagNames

          public void useLowerCaseTagNames()

      Specifies use of lower case for all tag names. This call should be made only after after all the desired tags are set.

    <!-- -->

    - #### useUpperCaseTagNames

          public void useUpperCaseTagNames()

      Specifies use of upper case for all tag names. This call should be made only after after all the desired tags are set.

    <!-- -->

    - #### setException

          public void setException(java.lang.Exception e)

      Allows the user to pass in an exception, and have the XSU handle it.
      Parameters:
      `e` - the exception to be processed by the XSU.

    <!-- -->

    - #### setRaiseException

          public void setRaiseException(boolean flag)

      Specifies whether to throw the raised exceptions. By defualt, or if the value of `flag` parameter is `FALSE`, the SQL exceptions are caught and used to generate an XML exception message document.
      Parameters:
      `flag` - `TRUE` to throw raised exception

    <!-- -->

    - #### setRaiseNoRowsException

          public void setRaiseNoRowsException(boolean flag)

      Specifies whether to throw an `OracleXMLNoRowsException` if the generated XML document is empty. By default, the exception is not thrown.
      Parameters:
      `flag` - `TRUE` to throw `OracleXMLNoRowsException`

    <!-- -->

    - #### setMaxRows

          public void setMaxRows(int rows)

      Sets the maximum number of rows to be converted to XML. By default, no maximum is set. Use the `MAXROWS_ALL` field to explicitly specify the maximum number of rows.
      Parameters:
      `rows` - maximum number of rows to generate

    <!-- -->

    - #### setSkipRows

          public void setSkipRows(int rows)

      Sets the number of rows to skip. By default, no rows are skipped. Use `SKIPROWS_ALL` to skip all the rows.
      Parameters:
      `rows` - number of rows to skip

    <!-- -->

    - #### close

          public void close()

      Closes open resources created by the `OracleXML` engine. This call will not effect result sets supplied by the user.

    <!-- -->

    - #### keepObjectOpen

          public void keepObjectOpen(boolean alive)

      Specifies whether to keep the input object open after a `getXML()/code> call. If the input object remains open, successive calls to ``getXML`` return successive sets of rows. By default, ``getXML()`` calls that do not use a ``ResultSet`` object close both the ``ResultSet`` and ``Statement`` objects. The ``close()`` function explicitly closes the cursor state.`
      Parameters:
      `alive` - `TRUE` to keep the object open

    <!-- -->

    - #### keepCursorState

          public void keepCursorState(boolean alive)

      Deprecated. since 1.2.1; use keepObjectOpen instead.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
