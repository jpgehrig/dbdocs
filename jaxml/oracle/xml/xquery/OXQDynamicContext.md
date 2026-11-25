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

- **[Prev Class](OXQDecimalFormat.md)**
- **[Next Class](OXQEntity.md)**

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

## **Interface OXQDynamicContext**

- **All Known Subinterfaces:**
  **[OXQExpression](OXQExpression.md), [OXQPreparedExpression](OXQPreparedExpression.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQDynamicContext

  **Extensions to [`javax.xml.xquery.XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md).**
  **Use method [`OXQView.getDynamicContext(XQDynamicContext)`](OXQView.md) to obtain access to these extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       XQPreparedExpression expr = con.prepareExpression(query);
       OXQDynamicContext octx = OXQView.getDynamicContext(expr);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                   | Method and Description                                                                                                                                                                                                                  |
    |---------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                              | `bindBigDecimal``(javax.xml.namespace.QName varName, java.math.BigDecimal value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                  |
    | `void`                                                              | `bindBigInteger``(javax.xml.namespace.QName varName, java.math.BigInteger value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                  |
    | `void`                                                              | `bindBinary``(javax.xml.namespace.QName varName, byte[] value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                    |
    | `void`                                                              | `bindCalendar``(javax.xml.namespace.QName varName, javax.xml.datatype.XMLGregorianCalendar value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item. |
    | `void`                                                              | `bindDocument``(javax.xml.namespace.QName varName, `[`OXQEntity`](OXQEntity.md)` value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.           |
    | `void`                                                              | `bindDuration``(javax.xml.namespace.QName varName, javax.xml.datatype.Duration value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.             |
    | `void`                                                              | `bindQName``(javax.xml.namespace.QName varName, javax.xml.namespace.QName value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                  |
    | [`XQConnection`](../../../javax/xml/xquery/XQConnection.md)         | `getConnection``()`<br>Gets the XQuery connection associated with this dynamic context.                                                                                                                                                 |
    | [`OXQDebugListener`](OXQDebugListener.md)                           | `getDebugListener``()`<br>Gets the debug listener.                                                                                                                                                                                      |
    | `java.lang.String`                                                  | `getDefaultCollection``()`<br>Gets the default collection that will be used when `fn:collection` is invoked with no arguments.                                                                                                          |
    | `java.lang.String`                                                  | `getDefaultResourceCollection``()`<br>Gets the default resource collection that will be used when `fn:uri-collection` is invoked with no arguments.                                                                                     |
    | [`PageManager`](../scalable/PageManager.md)                         | `getPageManager``()`<br>Gets the `PageManager`.                                                                                                                                                                                         |
    | `int`                                                               | `getUpdateMode``()`<br>Gets the default update mode.                                                                                                                                                                                    |
    | `java.lang.Object`                                                  | `getUserExtension``()`<br>Returns the user extension.                                                                                                                                                                                   |
    | [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md) | `getXQView``()`<br>Returns the [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md) instance corresponding to this instance.                                                                                             |
    | `void`                                                              | `setDebugListener``(`[`OXQDebugListener`](OXQDebugListener.md)` listener)`<br>Sets the debug listener.                                                                                                                                  |
    | `void`                                                              | `setDefaultCollection``(java.lang.String uri)`<br>Sets the default collection that will be used when `fn:collection` is invoked with no arguments.                                                                                      |
    | `void`                                                              | `setDefaultResourceCollection``(java.lang.String uri)`<br>Sets the default resource collection that will be used when `fn:uri-collection` is invoked with no arguments.                                                                 |
    | `void`                                                              | `setPageManager``(`[`PageManager`](../scalable/PageManager.md)` pageManager)`<br>Sets the `PageManager`.                                                                                                                                |
    | `void`                                                              | `setUpdateMode``(int mode)`<br>Sets the update mode.                                                                                                                                                                                    |
    | `void`                                                              | `setUserExtension``(java.lang.Object extension)`<br>Sets the user extension.                                                                                                                                                            |
    | `void`                                                              | `unbindAllExternalVariablesAndContextItem``()`<br>Unbinds all external variables and context item.                                                                                                                                      |

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQDynamicContext getXQView()

      Returns the [`XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md) instance corresponding to this instance.
      Returns:
      the dynamic context

    <!-- -->

    - #### getConnection

          XQConnection getConnection()
                              throws XQException

      Gets the XQuery connection associated with this dynamic context.
      Returns:
      the connection associated with this dynamic context

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the context is in a closed state

    <!-- -->

    - #### setDefaultCollection

          void setDefaultCollection(java.lang.String uri)
                             throws XQException

      Sets the default collection that will be used when `fn:collection` is invoked with no arguments.
      Parameters:
      `uri` - the absolute URI of the default collection

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the URI is not absolute or if the context is in a closed state

    <!-- -->

    - #### setDefaultResourceCollection

          void setDefaultResourceCollection(java.lang.String uri)
                                     throws XQException

      Sets the default resource collection that will be used when `fn:uri-collection` is invoked with no arguments.
      Parameters:
      `uri` - the URI of the default resource collection

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

    <!-- -->

    - #### getDefaultCollection

          java.lang.String getDefaultCollection()
                                         throws XQException

      Gets the default collection that will be used when `fn:collection` is invoked with no arguments.
      Returns:
      the URI of the default collection

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

    <!-- -->

    - #### getDefaultResourceCollection

          java.lang.String getDefaultResourceCollection()
                                                 throws XQException

      Gets the default resource collection that will be used when `fn:uri-collection` is invoked with no arguments.
      Returns:
      the URI of the default resource collection

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

    <!-- -->

    - #### setUserExtension

          void setUserExtension(java.lang.Object extension)
                         throws XQException

      Sets the user extension. Allows custom data to be stored in the dynamic context and serves as a way to provide state to external function implementations. This data can be retrieved by an implementation of [`OXQFunctionEvaluator`](OXQFunctionEvaluator.md).
      Parameters:
      `extension` - the user extension

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

    <!-- -->

    - #### getUserExtension

          java.lang.Object getUserExtension()
                                     throws XQException

      Returns the user extension.
      Returns:
      the user extension

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

    <!-- -->

    - #### bindDocument

          void bindDocument(javax.xml.namespace.QName varName,
                            OXQEntity value,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item.
      If the value represents a well-formed XML document, it results in a document node. The kind of the input type must be `null`, [`XQItemType.XQITEMKIND_DOCUMENT_ELEMENT`](../../../javax/xml/xquery/XQItemType.md) or [`XQItemType.XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`](../../../javax/xml/xquery/XQItemType.md).

      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`. The entity must conform to the [`OXQEntity`](OXQEntity.md) contract for `DOCUMENT` entities.

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

      See Also:
      [`OXQEntity`](OXQEntity.md)

    <!-- -->

    - #### bindBigDecimal

          void bindBigDecimal(javax.xml.namespace.QName varName,
                              java.math.BigDecimal value,
                              XQItemType type)
                       throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an exception is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindBigInteger

          void bindBigInteger(javax.xml.namespace.QName varName,
                              java.math.BigInteger value,
                              XQItemType type)
                       throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an exception is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindBinary

          void bindBinary(javax.xml.namespace.QName varName,
                          byte[] value,
                          XQItemType type)
                   throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an exception is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindCalendar

          void bindCalendar(javax.xml.namespace.QName varName,
                            javax.xml.datatype.XMLGregorianCalendar value,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an exception is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindDuration

          void bindDuration(javax.xml.namespace.QName varName,
                            javax.xml.datatype.Duration value,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an exception is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindQName

          void bindQName(javax.xml.namespace.QName varName,
                         javax.xml.namespace.QName value,
                         XQItemType type)
                  throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an exception is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### setDebugListener

          void setDebugListener(OXQDebugListener listener)
                         throws XQException

      Sets the debug listener.
      Parameters:
      `listener` - the debug listener

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the [`OXQDataSource`](OXQDataSource.md) property [`OXQDataSource.DEBUG_MODE`](OXQDataSource.md) is false

      See Also:
      [`OXQDataSource.DEBUG_MODE`](OXQDataSource.md), [`OXQDebugListener`](OXQDebugListener.md)

    <!-- -->

    - #### getDebugListener

          OXQDebugListener getDebugListener()
                                     throws XQException

      Gets the debug listener.
      Returns:
      listener the debug listener

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the [`OXQDataSource`](OXQDataSource.md) property [`OXQDataSource.DEBUG_MODE`](OXQDataSource.md) is false

      See Also:
      [`OXQDataSource.DEBUG_MODE`](OXQDataSource.md), [`OXQDebugListener`](OXQDebugListener.md)

    <!-- -->

    - #### setPageManager

          void setPageManager(PageManager pageManager)
                       throws XQException

      Sets the `PageManager`.
      Parameters:
      `pageManager` - the page manager

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the [`OXQDataSource.USE_EXTERNAL_STORAGE`](OXQDataSource.md) property is false

      See Also:
      [`OXQDataSource.USE_EXTERNAL_STORAGE`](OXQDataSource.md)

    <!-- -->

    - #### getPageManager

          PageManager getPageManager()
                              throws XQException

      Gets the `PageManager`.
      Returns:
      the page manager

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md)

      See Also:
      [`OXQDataSource.USE_EXTERNAL_STORAGE`](OXQDataSource.md)

    <!-- -->

    - #### setUpdateMode

          void setUpdateMode(int mode)
                      throws XQException

      Sets the update mode. Setting the mode to [`OXQConstants.UPDATE_MODE_ENABLED`](OXQConstants.md) will enable XQuery Update Facility extensions to update XML. Setting the mode to [`OXQConstants.UPDATE_MODE_DISABLED`](OXQConstants.md) will prevent XQuery Update Facility extension from updating XML. Note, the transform expression is always enabled regardless of the update mode setting.
      The update mode may only be set when the binding mode is [`XQConstants.BINDING_MODE_DEFERRED`](../../../javax/xml/xquery/XQConstants.md).

      Parameters:
      `mode` - The update mode, either [`OXQConstants.UPDATE_MODE_DISABLED`](OXQConstants.md) or [`OXQConstants.UPDATE_MODE_ENABLED`](OXQConstants.md).

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) if mode is not [`OXQConstants.UPDATE_MODE_DISABLED`](OXQConstants.md) or [`OXQConstants.UPDATE_MODE_ENABLED`](OXQConstants.md) (2) if the binding mode is not [`XQConstants.BINDING_MODE_DEFERRED`](../../../javax/xml/xquery/XQConstants.md)

      See Also:
      `getUpdateMode()`

    <!-- -->

    - #### getUpdateMode

          int getUpdateMode()

      Gets the default update mode.
      Returns:
      either [`OXQConstants.UPDATE_MODE_DISABLED`](OXQConstants.md) or [`OXQConstants.UPDATE_MODE_ENABLED`](OXQConstants.md)

      See Also:
      `setUpdateMode(int)`

    <!-- -->

    - #### unbindAllExternalVariablesAndContextItem

          void unbindAllExternalVariablesAndContextItem()
                                                 throws XQException

      Unbinds all external variables and context item.
      This method will unbind all external variables and the context item bound via the `bindXXX` methods.

      The method is intented to be used for releasing memory associated with bound values in case of an error during a `bindXXX` method invocation.

      This method should not be used to release memory associated with bound variables and the context item after [`XQPreparedExpression.executeQuery()`](../../../javax/xml/xquery/XQPreparedExpression.md) or one of the `executeQuery(...)` methods of [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) is called. Assuming deferred binding mode, the memory associated with the bindings is released automatically (note, however, that the application must call close() on the [`XQResultSequence`](../../../javax/xml/xquery/XQResultSequence.md) to release the memory).

      For example, assume the application creates an [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) for a query that declares two external variables: `$a` and `$b`. Assume the application binds `$a` successfully, but the `bindXXX` method invoked to bind `$b` throws an exception. Now suppose the application needs to hold on to the [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) for future use, when new values for `$a` and `$b` will be bound. This method provides the ability to unbind all external variables, and, consequently, release the reference to the `$a` bound value from the [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md).

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the binding mode is not set to deferred

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

- **[Prev Class](OXQDecimalFormat.md)**
- **[Next Class](OXQEntity.md)**

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
