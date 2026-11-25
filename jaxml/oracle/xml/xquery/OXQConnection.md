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

- **[Prev Class](OXQCompositeResolverFactory.md)**
- **[Next Class](OXQConstants.md)**

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

## **Interface OXQConnection**

- **All Superinterfaces:**
  **[OXQDataFactory](OXQDataFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQConnection
      extends OXQDataFactory

  **Extensions to [`javax.xml.xquery.XQConnection`](../../../javax/xml/xquery/XQConnection.md).**
  **Use method [`OXQView.getConnection(XQConnection)`](OXQView.md) to access these extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       OXQConnection ocon = OXQView.getConnection(con);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                               |
    |-------------------|-------------------------------------------------------------------------------------|
    | `static int`      | `SCOPE_CONNECTION`<br>Identifies components associated with the connection instance |
    | `static int`      | `SCOPE_EXPRESSION`<br>Identifies components associated with the expression instance |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                | Method and Description                                                                                                                                                                                 |
    |----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                                  | `convertXQueryToXQueryX``(`[`OXQEntity`](OXQEntity.md)` query)`<br>Converts XQuery to XQueryX.                                                                                                         |
    | `void`                                                                           | `convertXQueryXToXQuery``(`[`OXQEntity`](OXQEntity.md)` query, java.io.OutputStream out, java.lang.String outEncoding)`<br>Converts XQueryX to XQuery.                                                 |
    | [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md)      | `copyExpression``(`[`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md)` prepExpr)`<br>Returns a copy of an `XQPreparedExpression` instance.                                    |
    | [`OXQAnnotation`](OXQAnnotation.md)                                              | `createAnnotation``(javax.xml.namespace.QName name, `[`XQSequence`](../../../javax/xml/xquery/XQSequence.md)` value)`<br>Creates an annotation.                                                        |
    | [`OXQDecimalFormat`](OXQDecimalFormat.md)                                        | `createDecimalFormat``()`<br>Creates an instance of [`OXQDecimalFormat`](OXQDecimalFormat.md).                                                                                                         |
    | `<T extends `[`OXQEntityResolverFactory`](OXQEntityResolverFactory.md)`>`<br>`T` | `createEntityResolverFactory``(java.lang.Class<T> factoryType)`<br>Returns a factory for creating instances of OXQEntityResolver.                                                                      |
    | [`OXQOptions`](OXQOptions.md)                                                    | `createOptions``()`<br>Creates an empty instance of [`OXQOptions`](OXQOptions.md).                                                                                                                     |
    | [`OXQSerializationParameters`](OXQSerializationParameters.md)                    | `createSerializationParameters``()`<br>Creates an instance of [`OXQSerializationParameters`](OXQSerializationParameters.md).                                                                           |
    | [`OXQEntityLoader`](OXQEntityLoader.md)                                          | `getEntityLoader``(int scope)`<br>Returns an OXQEntityLoader instance that controls the schema/module loading process.                                                                                 |
    | [`OXQEntityResolver`](OXQEntityResolver.md)                                      | `getEntityResolver``()`<br>Gets the entity resolver.                                                                                                                                                   |
    | [`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)                | `getModuleStaticContext``()`<br>Gets an `XQStaticContext` instance representing the default values for all properties of library modules loaded by this connection.                                    |
    | [`XQConnection`](../../../javax/xml/xquery/XQConnection.md)                      | `getXQView``()`<br>Returns the [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) instance corresponding to this instance.                                                                    |
    | [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md)      | `prepareExpression``(`[`OXQEntity`](OXQEntity.md)` xquery)`<br>Prepares an expression for execution.                                                                                                   |
    | [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md)      | `prepareExpression``(`[`OXQEntity`](OXQEntity.md)` xquery, `[`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)` properties)`<br>Prepares an expression for execution.                   |
    | `void`                                                                           | `setEntityResolver``(`[`OXQEntityResolver`](OXQEntityResolver.md)` entityResolver)`<br>Assigns a new entity resolver to the connection, replacing the existing one.                                    |
    | `void`                                                                           | `setModuleStaticContext``(`[`XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md)` properties)`<br>Sets the default values for all properties of library modules loaded by this connection. |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQDataFactory](OXQDataFactory.md)

      [`createItemFromBigDecimal`](OXQDataFactory.md)`, `[`createItemFromBigInteger`](OXQDataFactory.md)`, `[`createItemFromBinary`](OXQDataFactory.md)`, `[`createItemFromCalendar`](OXQDataFactory.md)`, `[`createItemFromDocument`](OXQDataFactory.md)`, `[`createItemFromDuration`](OXQDataFactory.md)`, `[`createItemFromQName`](OXQDataFactory.md)`, `[`createSequence`](OXQDataFactory.md)`, `[`createSequenceFromDocument`](OXQDataFactory.md)`, `[`createSequenceFromDocument`](OXQDataFactory.md)`, `[`createSequenceFromDocument`](OXQDataFactory.md)`, `[`createSequenceFromDocument`](OXQDataFactory.md)`, `[`createSequenceTypeFromJavaType`](OXQDataFactory.md)

<!-- -->

- - ### Field Detail

    - #### SCOPE_CONNECTION

          static final int SCOPE_CONNECTION

      Identifies components associated with the connection instance
      See Also:
      `getEntityLoader(int)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SCOPE_EXPRESSION

          static final int SCOPE_EXPRESSION

      Identifies components associated with the expression instance
      See Also:
      `getEntityLoader(int)`, [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getXQView

          XQConnection getXQView()

      Returns the [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) instance corresponding to this instance.
      Specified by:
      [`getXQView`](OXQDataFactory.md) in interface [`OXQDataFactory`](OXQDataFactory.md)

      Returns:
      the connection

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(OXQEntity xquery)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the connection's default `XQStaticContext` instance are copied to the returned expression.

      Parameters:
      `xquery` - the XQuery expression as an [`OXQEntity`](OXQEntity.md). The permitted entity `data` is the same as what is permitted for [`MODULE`](OXQEntityKind.md) entities except that collections are not allowed. Cannot be `null`.

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the connection is in a closed state, (2) there are errors preparing the expression, or (3) the xquery parameter is `null`

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(OXQEntity xquery,
                                                 XQStaticContext properties)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the specified `XQStaticContext` instance are copied to the returned expression.

      Parameters:
      `xquery` - the XQuery expression as an [`OXQEntity`](OXQEntity.md). The permitted entity `data` is the same as what is permitted for [`MODULE`](OXQEntityKind.md) entities except that collections are not allowed. Cannot be `null`.

      `properties` - `XQStaticContext` containing values of expression properties.

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the connection is in a closed state, or (2) the specified argument is `null`

    <!-- -->

    - #### copyExpression

          XQPreparedExpression copyExpression(XQPreparedExpression prepExpr)
                                       throws XQException

      Returns a copy of an `XQPreparedExpression` instance. Users can create an initial prepared expression using the `XQConnection` interface, and then make multiple copies using this method. The copying is done without plan recompilation, and each copy can then be executed concurrently in a separate thread. The copies do not support all the methods of `OXQPreparedExpression`. The copies are primarily intended for binding variables and execution.
      Parameters:
      `prepExpr` - The input prepared expression

      Returns:
      a new copy of the input prepared expression

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the input prepared expression is closed, (2) the input prepared expression has already been executed or has bound variables (3) the input prepared expression was generated by some other XQJ implementation (4) the input prepared expression was created with a different connection (5) the input prepared expression cannot be copied or (6) there was an internal engine error while copying the input prepared expression

    <!-- -->

    - #### getModuleStaticContext

          XQStaticContext getModuleStaticContext()
                                          throws XQException

      Gets an `XQStaticContext` instance representing the default values for all properties of library modules loaded by this connection. In order to modify the defaults, it is not sufficient to modify the values in the returned `XQStaticContext` instance; in addition method `setModuleStaticContext(XQStaticContext)` should be called to make the new values effective.
      Returns:
      a `XQStaticContext` instance representing the default values for all properties of library modules

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### setModuleStaticContext

          void setModuleStaticContext(XQStaticContext properties)
                               throws XQException

      Sets the default values for all properties of library modules loaded by this connection. The implementation will read out all properties from the specified `XQStaticContext` instance and update its private copy. The `OXQEntityResolver` implementation can override these defaults by providing `OXQStaticContext` instance along with the returned library module content. See [`OXQEntity.PROPERTY_MODULE_STATIC_CONTEXT`](OXQEntity.md) for more information.
      Parameters:
      `properties` - a `XQStaticContext` instance containing values of library module properties

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### createEntityResolverFactory

          <T extends OXQEntityResolverFactory> T createEntityResolverFactory(java.lang.Class<T> factoryType)
                                                                      throws XQException

      Returns a factory for creating instances of OXQEntityResolver.
      Parameters:
      `factoryType` - The [`OXQEntityResolverFactory`](OXQEntityResolverFactory.md) implementation class to construct

      Returns:
      factory object

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the connection is in a closed state, (2) factory cannot be create for given factoryType

      See Also:
      [`OXQEntityResolverFactory`](OXQEntityResolverFactory.md)

    <!-- -->

    - #### setEntityResolver

          void setEntityResolver(OXQEntityResolver entityResolver)
                          throws XQException

      Assigns a new entity resolver to the connection, replacing the existing one.
      Parameters:
      `entityResolver` - the entity resolver

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### getEntityResolver

          OXQEntityResolver getEntityResolver()
                                       throws XQException

      Gets the entity resolver.
      Returns:
      the entity resolver

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### getEntityLoader

          OXQEntityLoader getEntityLoader(int scope)
                                   throws XQException

      Returns an OXQEntityLoader instance that controls the schema/module loading process.
      The following entity loader instances are provided by each XQConnection:

      1.  Connection-scoped - always available
      2.  Expression-scoped - only available in [`OXQDataSource.IMPORT_SHARING`](OXQDataSource.md) mode

      See [`OXQEntityLoader`](OXQEntityLoader.md) documentation for more information.
      Parameters:
      `scope` - `SCOPE_CONNECTION` or `SCOPE_EXPRESSION`

      Returns:
      the entity loader

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### convertXQueryToXQueryX

          XQItem convertXQueryToXQueryX(OXQEntity query)
                                 throws XQException

      Converts XQuery to XQueryX.
      Parameters:
      `query` - an `OXQEntity` instance representing the query

      Returns:
      the XQueryX as an `XQItem` instance.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the connection is closed, (2) a java IO exception was thrown while reading the query (attached as cause), or (3) the conversion failed

      See Also:
      [`OXQEntity.MEDIA_TYPE_XQUERY`](OXQEntity.md), [`OXQEntityKind.MODULE`](OXQEntityKind.md)

    <!-- -->

    - #### convertXQueryXToXQuery

          void convertXQueryXToXQuery(OXQEntity query,
                                      java.io.OutputStream out,
                                      java.lang.String outEncoding)
                               throws XQException

      Converts XQueryX to XQuery.
      Parameters:
      `query` - an `OXQEntity` instance representing the query in XQueryX

      `out` - the output stream to which the resulting XQuery is written

      `outEncoding` - a query encoding (UTF-8 if `null`)

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the connection is closed, (2) a java IO exception was thrown while reading the query (attached as cause), or (3) the conversion failed

      See Also:
      [`OXQEntity.MEDIA_TYPE_XQUERYX`](OXQEntity.md), [`OXQEntityKind.MODULE`](OXQEntityKind.md)

    <!-- -->

    - #### createSerializationParameters

          OXQSerializationParameters createSerializationParameters()
                                                            throws XQException

      Creates an instance of [`OXQSerializationParameters`](OXQSerializationParameters.md).
      Returns:
      the serialization parameters

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### createDecimalFormat

          OXQDecimalFormat createDecimalFormat()
                                        throws XQException

      Creates an instance of [`OXQDecimalFormat`](OXQDecimalFormat.md).
      Returns:
      the decimal format

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### createOptions

          OXQOptions createOptions()
                            throws XQException

      Creates an empty instance of [`OXQOptions`](OXQOptions.md).
      Returns:
      the options

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### createAnnotation

          OXQAnnotation createAnnotation(javax.xml.namespace.QName name,
                                         XQSequence value)
                                  throws XQException

      Creates an annotation.
      Parameters:
      `name` - the annotation name. Cannot be `null`

      `value` - the annotation value. Passing `null` will set the value to the empty sequence

      Returns:
      the annotation

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the connection is closed, (2) the name parameter is null, or (3) consuming the value sequence raises an error

      See Also:
      [`OXQStaticContext.declareFunction(QName, javax.xml.xquery.XQSequenceType[], javax.xml.xquery.XQSequenceType, OXQOptions, OXQAnnotation[])`](OXQStaticContext.md)

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

- **[Prev Class](OXQCompositeResolverFactory.md)**
- **[Next Class](OXQConstants.md)**

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
