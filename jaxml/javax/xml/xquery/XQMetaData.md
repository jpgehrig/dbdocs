Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQItemType.md)**
- **[Next Class](XQPreparedExpression.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**javax.xml.xquery**

## **Interface XQMetaData**

-

  ------------------------------------------------------------------------

  **
  **

      public interface XQMetaData

  **`XQMetaData` interface provides information about the data source, in various aspects, such as the product name and version identification, supported features, specific behaviors, user information, product limits and so forth.

  An object implementing this interface is obtained from the connection object by calling the `getMetaData()` method, for example:
  **
        XQMetaData metaData = connection.getMetaData();
        String productVersion = metaData.getProductVersion();
          ...


  **Since the metadata object depends on the connection, all its methods would raise an exception if the connection it is created from is no longer valid.**
  **See Also:**
  **[`XQConnection`](XQConnection.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                       |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getMaxExpressionLength``()`<br>Gets the maximum number of characters allowed in an expression in this data source.                                                                          |
    | `int`              | `getMaxUserNameLength``()`<br>Gets the maximum number of characters allowed in a user name.                                                                                                  |
    | `int`              | `getProductMajorVersion``()`<br>Gets the major version of this product.                                                                                                                      |
    | `int`              | `getProductMinorVersion``()`<br>Gets the minor version of this product.                                                                                                                      |
    | `java.lang.String` | `getProductName``()`<br>Gets the name of this product.                                                                                                                                       |
    | `java.lang.String` | `getProductVersion``()`<br>Gets the full version of this product.                                                                                                                            |
    | `java.util.Set`    | `getSupportedXQueryEncodings``()`<br>Returns a set of `java.lang.String`, each of which specifies a character encoding method the XQJ implmentation supports to parse the XQuery query text. |
    | `java.lang.String` | `getUserName``()`<br>Gets the user name associated with this connection.                                                                                                                     |
    | `int`              | `getXQJMajorVersion``()`<br>Gets the major version number of XQJ specification supported by this implementation.                                                                             |
    | `int`              | `getXQJMinorVersion``()`<br>Gets the minor version number of XQJ specification supported by this implementation.                                                                             |
    | `java.lang.String` | `getXQJVersion``()`<br>Gets the full version of XQJ specification supported by this implementation.                                                                                          |
    | `boolean`          | `isFullAxisFeatureSupported``()`<br>Query if XQuery full axis feature is supported in this connection.                                                                                       |
    | `boolean`          | `isModuleFeatureSupported``()`<br>Query if XQuery module feature is supported in this connection.                                                                                            |
    | `boolean`          | `isReadOnly``()`<br>Query if the associated conection is restricted for read only use.                                                                                                       |
    | `boolean`          | `isSchemaImportFeatureSupported``()`<br>Query if XQuery schema import feature is supported in this connection.                                                                               |
    | `boolean`          | `isSchemaValidationFeatureSupported``()`<br>Query if XQuery schema validation feature is supported in this connection.                                                                       |
    | `boolean`          | `isSerializationFeatureSupported``()`<br>Query if XQuery serialization feature is supported in this connection.                                                                              |
    | `boolean`          | `isStaticTypingExtensionsSupported``()`<br>Query if XQuery static typing extensions are supported in this connection.                                                                        |
    | `boolean`          | `isStaticTypingFeatureSupported``()`<br>Query if XQuery static typing feature is supported in this data source.                                                                              |
    | `boolean`          | `isTransactionSupported``()`<br>Query if transaction is supported in this data source.                                                                                                       |
    | `boolean`          | `isUserDefinedXMLSchemaTypeSupported``()`<br>Check if the user defined XML schema type is supported in this connection.                                                                      |
    | `boolean`          | `isXQueryEncodingDeclSupported``()`<br>Query if the XQuery encoding declaration is supported by the XQJ implementation.                                                                      |
    | `boolean`          | `isXQueryEncodingSupported``(java.lang.String encoding)`<br>Query if a character encoding method of the XQuery query text is supported by the XQJ implmentation.                             |
    | `boolean`          | `isXQueryXSupported``()`<br>Query if XQueryX format is supported in this data source.                                                                                                        |
    | `boolean`          | `wasCreatedFromJDBCConnection``()`<br>Query if this connection was created from a JDBC connection.                                                                                           |

<!-- -->

- - ### Method Detail

    - #### getProductMajorVersion

          int getProductMajorVersion()
                              throws XQException

      Gets the major version of this product.
      Returns:
      a integer indicating the major version of this product

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getProductMinorVersion

          int getProductMinorVersion()
                              throws XQException

      Gets the minor version of this product.
      Returns:
      a integer indicating the minor version of this product

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getProductName

          java.lang.String getProductName()
                                   throws XQException

      Gets the name of this product. The value of string returned by this method is implementation-defined.
      Returns:
      a string indicating the product name

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getProductVersion

          java.lang.String getProductVersion()
                                      throws XQException

      Gets the full version of this product. The format and value of the string returned by this method is implementation-defined.
      Returns:
      a string indicating the product version

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getXQJMajorVersion

          int getXQJMajorVersion()
                          throws XQException

      Gets the major version number of XQJ specification supported by this implementation.
      Returns:
      an integer indicating the XQJ major version

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getXQJMinorVersion

          int getXQJMinorVersion()
                          throws XQException

      Gets the minor version number of XQJ specification supported by this implementation.
      Returns:
      an integer indicating the XQJ minor version

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getXQJVersion

          java.lang.String getXQJVersion()
                                  throws XQException

      Gets the full version of XQJ specification supported by this implementation.
      Returns:
      a string indicating the version of XQJ specification

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isReadOnly

          boolean isReadOnly()
                      throws XQException

      Query if the associated conection is restricted for read only use.
      Returns:
      `true` if the associated connection is for read-only; `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isXQueryXSupported

          boolean isXQueryXSupported()
                              throws XQException

      Query if XQueryX format is supported in this data source.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isTransactionSupported

          boolean isTransactionSupported()
                                  throws XQException

      Query if transaction is supported in this data source.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isStaticTypingFeatureSupported

          boolean isStaticTypingFeatureSupported()
                                          throws XQException

      Query if XQuery static typing feature is supported in this data source.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isSchemaImportFeatureSupported

          boolean isSchemaImportFeatureSupported()
                                          throws XQException

      Query if XQuery schema import feature is supported in this connection.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isSchemaValidationFeatureSupported

          boolean isSchemaValidationFeatureSupported()
                                              throws XQException

      Query if XQuery schema validation feature is supported in this connection.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isFullAxisFeatureSupported

          boolean isFullAxisFeatureSupported()
                                      throws XQException

      Query if XQuery full axis feature is supported in this connection.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isModuleFeatureSupported

          boolean isModuleFeatureSupported()
                                    throws XQException

      Query if XQuery module feature is supported in this connection.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isSerializationFeatureSupported

          boolean isSerializationFeatureSupported()
                                           throws XQException

      Query if XQuery serialization feature is supported in this connection.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isStaticTypingExtensionsSupported

          boolean isStaticTypingExtensionsSupported()
                                             throws XQException

      Query if XQuery static typing extensions are supported in this connection.
      Returns:
      `true` if so; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getUserName

          java.lang.String getUserName()
                                throws XQException

      Gets the user name associated with this connection.
      Returns:
      the user's name

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getMaxExpressionLength

          int getMaxExpressionLength()
                              throws XQException

      Gets the maximum number of characters allowed in an expression in this data source.
      Returns:
      the maximum length of expression as an integer. A zero value means that there is no limit or the limit is unknown

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getMaxUserNameLength

          int getMaxUserNameLength()
                            throws XQException

      Gets the maximum number of characters allowed in a user name.
      Returns:
      the maximum length of user name as an integer. A zero value means that there is no limit or the limit is unknown

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### wasCreatedFromJDBCConnection

          boolean wasCreatedFromJDBCConnection()
                                        throws XQException

      Query if this connection was created from a JDBC connection.
      Returns:
      `true`, if this connection was created from a JDBC connection, `false` otherwise.

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isXQueryEncodingDeclSupported

          boolean isXQueryEncodingDeclSupported()
                                         throws XQException

      Query if the XQuery encoding declaration is supported by the XQJ implementation.
      Returns:
      `true` if the XQuery encoding declaration is supported; `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### getSupportedXQueryEncodings

          java.util.Set getSupportedXQueryEncodings()
                                             throws XQException

      Returns a set of `java.lang.String`, each of which specifies a character encoding method the XQJ implmentation supports to parse the XQuery query text.
      For an example, for an XQJ impmentation which is able to parse the XQuery encoded in "UTF-8" or "UTF-16", it returns a `java.util.Set` of "UTF-8" and "UTF-16". If the implemetation is not able to generate a list of encodings supported, an empty set is returned. If a non-empty set is returned, the encodings returned in this set are guaranteed to be supported. Note that encodings not in the returned set might also be supported. For example, if the set has two encoding methods: 'UTF-8' and 'UTF-16', they are supported by the implementation. However, this does not mean 'Shift-Js' is not supported. It might be supported.
      Returns:
      a `java.util.Set` of `java.lang.String`, each of which is an XQuery query text encoding method

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

    <!-- -->

    - #### isXQueryEncodingSupported

          boolean isXQueryEncodingSupported(java.lang.String encoding)
                                     throws XQException

      Query if a character encoding method of the XQuery query text is supported by the XQJ implmentation.
      Parameters:
      `encoding` - `String` representing the character encoding method of the XQuery query text.

      Returns:
      `true` if an XQuery query character encoding method is supported, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is no longer valid, or (2) the specified `encoding` parameter is `null`

    <!-- -->

    - #### isUserDefinedXMLSchemaTypeSupported

          boolean isUserDefinedXMLSchemaTypeSupported()
                                               throws XQException

      Check if the user defined XML schema type is supported in this connection. If this method returns `true`, then `XQItemAccessor.instanceOf(XQItemType)` must be able to determine if the type of an `XQItemAccessor` is an instance of the `XQItemType` even if either of them is a user defined XML schema type which is defined by the non-predefined XML schema. The pre-defined XML Schema refers to the XML schema whose schema URL is `"http://www.w3.org/2001/XMLSchema"`
      Returns:
      `true` if the user defined XML schema type is supported in this connection, `false` otherwise.

      Throws:
      [`XQException`](XQException.md) - if the connection is no longer valid

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQItemType.md)**
- **[Next Class](XQPreparedExpression.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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
