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

- **[Prev Class](OXQDataFactory.md)**
- **[Next Class](OXQDebugListener.md)**

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

**oracle.xml.xquery**

## **Class OXQDataSource**

- **java.lang.Object**

- - **oracle.xml.xquery.OXQDataSource**

<!-- -->

- **All Implemented Interfaces:**
  **[XQDataSource](../../../javax/xml/xquery/XQDataSource.md)**

  ------------------------------------------------------------------------

  **
  **

      public final class OXQDataSource
      extends java.lang.Object
      implements XQDataSource

  **Implements [`javax.xml.xquery.XQDataSource`](../../../javax/xml/xquery/XQDataSource.md).**
  **Since:**
  **12.1**

  **See Also:**
  **[`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                    |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `DEBUG_MODE`<br>A property that when set to `"true"`, debugging will be enabled; otherwise, debugging will be disabled.                                                                                  |
    | `static java.lang.String` | `DISABLE_EXPRESSION_TRACKING`<br>A property that when set to `"true"` will prevent a connection from tracking open expressions that are created from it.                                                 |
    | `static java.lang.String` | `DOM_PASS_THROUGH`<br>A property that when set to `"true"` relaxes XML data model conversions.                                                                                                           |
    | `static java.lang.String` | `IMPORT_SHARING`<br>A property that when set to `"true"`, schema and module imports will be shared among queries from the same connection.                                                               |
    | `static java.lang.String` | `PESSIMISTIC_TYPE_CHECKING`<br>A property that determines if optimistic or pessimistic type checking will be used at compile time.                                                                       |
    | `static java.lang.String` | `USE_EXTERNAL_STORAGE`<br>A property that when set to `"true"` will cause the query processor use an instance of [`oracle.xml.scalable.PageManager`](../scalable/PageManager.md) when materializing XML. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------|
    | `OXQDataSource``()`<br>Constructs a data source with default properties.                                        |
    | `OXQDataSource``(java.util.Properties inProperties)`<br>Constructs a data source with the specified properties. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                     |
    |-------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) | `getConnection``()`<br>Attempts to create a connection to an XML datasource.                                                                                               |
    | [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) | `getConnection``(java.sql.Connection con)`<br>Attempts to create a connection to an XML datasource using an existing JDBC connection.                                      |
    | [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) | `getConnection``(java.lang.String username, java.lang.String passwd)`<br>Attempts to establish a connection to an XML datasource using the supplied username and password. |
    | `int`                                                       | `getLoginTimeout``()`<br>Gets the maximum time in seconds that this datasource can wait while attempting to connect to a database.                                         |
    | `java.io.PrintWriter`                                       | `getLogWriter``()`<br>Retrieves the log writer for this `XQDataSource` object.                                                                                             |
    | `java.lang.String`                                          | `getProperty``(java.lang.String name)`<br>Returns the current value of the named property if set, else `null`.                                                             |
    | `java.lang.String[]`                                        | `getSupportedPropertyNames``()`<br>Returns an array containing the property names supported by this `XQDataSource`.                                                        |
    | `void`                                                      | `setLoginTimeout``(int seconds)`<br>Sets the maximum time in seconds that this datasource will wait while attempting to connect to a database.                             |
    | `void`                                                      | `setLogWriter``(java.io.PrintWriter out)`<br>Sets the log writer for this `XQDataSource` object to the given `java.io.PrintWriter` object.                                 |
    | `void`                                                      | `setProperties``(java.util.Properties props)`<br>Sets the data source properties from the specified `Properties` instance.                                                 |
    | `void`                                                      | `setProperty``(java.lang.String name, java.lang.String value)`<br>Sets the named property to the specified value.                                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PESSIMISTIC_TYPE_CHECKING

          public static final java.lang.String PESSIMISTIC_TYPE_CHECKING

      A property that determines if optimistic or pessimistic type checking will be used at compile time. In general, pessimistic type checking will fail whenever the derived type of an expression is not a subtype of the expected type. Optimistic type checking will fail whenever the derived type of an expression does not intersect the expected type. More simply put, pessimistic mode raises an error at compile time if a type might not be correct at runtime. Optimistic mode, on the other hand, only raises an error at compile time when the runtime type check will certainly fail.
      When set to `"true"`, pessimistic type checking will be used. For any other value, optimistic type checking will be used. The default value is `"false"`.

      See Also:
      [`XQDataSource.setProperty(String, String)`](../../../javax/xml/xquery/XQDataSource.md), [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEBUG_MODE

          public static final java.lang.String DEBUG_MODE

      A property that when set to `"true"`, debugging will be enabled; otherwise, debugging will be disabled. The default value of this property is `"false"`
      See Also:
      [`XQDataSource.setProperty(String, String)`](../../../javax/xml/xquery/XQDataSource.md), [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### IMPORT_SHARING

          public static final java.lang.String IMPORT_SHARING

      A property that when set to `"true"`, schema and module imports will be shared among queries from the same connection. The default value of this property is `"false"`
      See Also:
      [`XQDataSource.setProperty(String, String)`](../../../javax/xml/xquery/XQDataSource.md), [`OXQConnection.getEntityLoader(int)`](OXQConnection.md), [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DOM_PASS_THROUGH

          public static final java.lang.String DOM_PASS_THROUGH

      A property that when set to `"true"` relaxes XML data model conversions. XQuery is designed to process instances of the [XQuery and XPath data model](http://www.w3.org/TR/xpath-datamodel/) (XDM). In several places, the XQJ API facilitates consuming XDM as DOM. For example, [`XQItemAccessor.getNode()`](../../../javax/xml/xquery/XQItemAccessor.md) returns the XDM node as a DOM node. The conversion from XDM to DOM is specified in two parts: [XDM Infoset Mapping](http://www.w3.org/TR/xpath-datamodel/#infoset_mapping) and [Appendix C](http://www.w3.org/TR/DOM-Level-3-Core/infoset-mapping.html) of the DOM specification.
      When the input data to the query is DOM and the output of the query is consumed as DOM, it may be desirable to avoid the required data model conversions to improve performance. When this this property is set to `"true"` DOM may be queried directly without conversion. Note, the processor can not conform strictly to the specifications when in this mode. For example, CDATA nodes, adjacent text nodes, empty text nodes, entity reference nodes, and document type nodes may all appear in the result. The default value of this property is `"false"`.

      See Also:
      [`XQDataSource.setProperty(String, String)`](../../../javax/xml/xquery/XQDataSource.md), [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### USE_EXTERNAL_STORAGE

          public static final java.lang.String USE_EXTERNAL_STORAGE

      A property that when set to `"true"` will cause the query processor use an instance of [`oracle.xml.scalable.PageManager`](../scalable/PageManager.md) when materializing XML. There are two scenarios in which the `PageManager` may be used:
      1.  If data is bound to the query and the binding mode is [`BINDING_MODE_IMMEDIATE`](../../../javax/xml/xquery/XQConstants.md), then the bound value will be copied into the `PageManager`. In this case, all pages will be released (deleted) by the time the corresponding [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) or [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) is closed.
      2.  If the query processor needs to materialize intermediate results while processing the query, it will use the `PageManager`. In this case, all pages will be released (deleted) by the time the corresponding `XQResultSequence` is closed.

      This property must be used in combination with [`OXQDynamicContext.setPageManager(oracle.xml.scalable.PageManager)`](OXQDynamicContext.md) Using external storage may drastically reduce the main memory needed to process a query but it may also make query processing take longer.
      See Also:
      [`XQDataSource.setProperty(String, String)`](../../../javax/xml/xquery/XQDataSource.md), [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DISABLE_EXPRESSION_TRACKING

          public static final java.lang.String DISABLE_EXPRESSION_TRACKING

      A property that when set to `"true"` will prevent a connection from tracking open expressions that are created from it. This is intended for use in cases where multiple threads access the connection and the synchronization needed to track open expressions causes performance problems. When expression tracking is disabled, an attempt to call [`XQConnection.close()`](../../../javax/xml/xquery/XQConnection.md) will raise an error so this can only be used in cases where relying on the connection to close expressions is not needed.
      See Also:
      [`XQDataSource.setProperty(String, String)`](../../../javax/xml/xquery/XQDataSource.md), [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OXQDataSource

          public OXQDataSource()

      Constructs a data source with default properties.

    <!-- -->

    - #### OXQDataSource

          public OXQDataSource(java.util.Properties inProperties)
                        throws XQException

      Constructs a data source with the specified properties.
      Parameters:
      `inProperties` - the data source properties, may not be `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if `inProperties` is `null` or if a given property is not supported

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public XQConnection getConnection()
                                     throws XQException

      Attempts to create a connection to an XML datasource.
      Specified by:
      [`getConnection`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getConnection

          public XQConnection getConnection(java.sql.Connection con)
                                     throws XQException

      Attempts to create a connection to an XML datasource using an existing JDBC connection. An XQJ implementation is not required to support this method. If it is not supported, then an exception (`XQException`) is thrown. The XQJ and JDBC connections will operate under the same transaction context.
      Specified by:
      [`getConnection`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `con` - an existing JDBC connection

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) a datasource access error occurs, (2) the implementation does not support this method of getting an `XQConnection`, or (3) if the `con` parameter is `null`

    <!-- -->

    - #### getConnection

          public XQConnection getConnection(java.lang.String username,
                                            java.lang.String passwd)
                                     throws XQException

      Attempts to establish a connection to an XML datasource using the supplied username and password.
      Specified by:
      [`getConnection`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `username` - the user on whose behalf the connection is being made

      `passwd` - the user's password

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### setLoginTimeout

          public void setLoginTimeout(int seconds)
                               throws XQException

      Sets the maximum time in seconds that this datasource will wait while attempting to connect to a database. A value of zero specifies that the timeout is the default system timeout if there is one; otherwise, it specifies that there is no timeout. When a `XQDataSource` object is created, the login timeout is initially zero. It is implementation-defined whether the specified login timeout is actually used by the data source implementation. If the connection is created over an existing JDBC connection, then the login timeout value from the underlying JDBC connection may be used.
      Specified by:
      [`setLoginTimeout`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `seconds` - the datasource login time limit

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLoginTimeout

          public int getLoginTimeout()
                              throws XQException

      Gets the maximum time in seconds that this datasource can wait while attempting to connect to a database. A value of zero means that the timeout is the default system timeout if there is one; otherwise, it means that there is no timeout. When a XQDataSource object is created, the login timeout is initially zero. It is implementation-defined whether the returned login timeout is actually used by the data source implementation.
      Specified by:
      [`getLoginTimeout`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      the datasource login time limit

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### setLogWriter

          public void setLogWriter(java.io.PrintWriter out)
                            throws XQException

      Sets the log writer for this `XQDataSource` object to the given `java.io.PrintWriter` object. The log writer is a character output stream to which all logging and tracing messages for this datasource will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. When a `XQDataSource` object is created the log writer is initially `null`; in other words, the default is for logging to be disabled.
      Specified by:
      [`setLogWriter`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `out` - the new log writer; to disable logging, set to `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLogWriter

          public java.io.PrintWriter getLogWriter()
                                           throws XQException

      Retrieves the log writer for this `XQDataSource` object. The log writer is a character output stream to which all logging and tracing messages for this datasource will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. When a `XQDataSource` object is created, the log writer is initially `null`; in other words, the default is for logging to be disabled.
      Specified by:
      [`getLogWriter`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      the log writer for this datasource or `null` if logging is disabled

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getSupportedPropertyNames

          public java.lang.String[] getSupportedPropertyNames()

      Returns an array containing the property names supported by this `XQDataSource`. Implementations that support user name and password must recognize the user name and password properties listed below.

      |            |                                                |
      |------------|------------------------------------------------|
      | `user`     | the user name to use for creating a connection |
      | `password` | the password to use for creating a connection  |


      Any additional properties are implementation-defined.
      Specified by:
      [`getSupportedPropertyNames`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      `String[]` an array of property names supported by this implementation

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String name,
                                  java.lang.String value)
                           throws XQException

      Sets the named property to the specified value. If a property with the same name was already set, then this method will override the old value for that property with the new value.
      If the implementation does not support the given property or if it can determine that the value given for this property is invalid, then an exception is thrown. If an exception is thrown, then no previous value is overwritten.

      Specified by:
      [`setProperty`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `name` - the name of the property to set

      `value` - the value of the named property

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the given property is not recognized, (2) the value for the given property is determined to be invalid, or (3) the `name` parameter is `null`

    <!-- -->

    - #### getProperty

          public java.lang.String getProperty(java.lang.String name)
                                       throws XQException

      Returns the current value of the named property if set, else `null`. If the implementation does not support the given property then an exception is raised.
      Specified by:
      [`getProperty`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `name` - the name of the property whose value is needed

      Returns:
      `String` representing the value of the required property if set, else `null`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) a given property is not supported, or (2) the name parameter is `null`

    <!-- -->

    - #### setProperties

          public void setProperties(java.util.Properties props)
                             throws XQException

      Sets the data source properties from the specified `Properties` instance. Properties set before this call will still apply but those with the same name as any of these properties will be replaced. Properties set after this call also apply and may replace properties set during this call.
      If the implementation does not support one or more of the given property names, or if it can determine that the value given for a specific property is invalid, then an exception is thrown. If an exception is thrown, then no previous value is overwritten. is invalid, then an exception is raised.

      Specified by:
      [`setProperties`](../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `props` - the list of properties to set

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) a given property is not recognized, (2) the value for a given property is determined to be invalid, or (3) the `props` parameter is `null`

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

- **[Prev Class](OXQDataFactory.md)**
- **[Next Class](OXQDebugListener.md)**

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
