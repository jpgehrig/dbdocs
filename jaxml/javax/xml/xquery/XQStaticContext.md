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

- **[Prev Class](XQStackTraceVariable.md)**
- **Next Class**

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

## **Interface XQStaticContext**

-

  ------------------------------------------------------------------------

  **
  **

      public interface XQStaticContext

  **An `XQStaticContext` represents default values for various [*XQuery Static Context Components*](http://www.w3.org/TR/xquery/#id_xq_static_context_components). Further it includes the static XQJ properties for an `XQExpression` or `XQPreparedExpression` object.**
  **The following XQuery Static Context Components are supported through the `XQStaticContext` interface:**

  - **Statically known namespaces**
  - **Default element/type namespace**
  - **Default function namespace**
  - **Context item static type**
  - **Default collation**
  - **Construction mode**
  - **Ordering mode**
  - **Default order for empty sequences**
  - **Boundary-space policy**
  - **Copy-namespaces mode**
  - **Base URI**

  **As described in the XQuery specification, each of these default values can be overridden or augmented in the query prolog.
  **
  **In addition `XQStaticContext` includes the static XQJ properties for an `XQExpression` or `XQPreparedExpression` object:**

  - **Binding mode**
  - **Holdability of the result sequences**
  - **Scrollability of the result sequences**
  - **Query language**
  - **Query timeout**

  **Note that `XQStaticContext` is a value object, changing attributes in such object doesn't affect any existing `XQExpression` or `XQPreparedExpression` object.
  In order to take effect, the application needs to explicitly change the `XQConnection` default values, or specify an `XQStaticContext` object when creating an `XQExpression` or `XQPreparedExpression`.**

        XQConnection conn = XQDatasource.getConnection();
        // get the default values from the implementation
        XQStaticContext cntxt = conn.getStaticContext();
        // change the base uri
        cntxt.setBaseURI("http://www.foo.com/xml/");
        // change the implementation defaults
         conn.setStaticContext(cntxt);

        // create an XQExpression using the new defaults
        XQExpression expr1 = conn.createExpression();

        // creat an XQExpression, using BaseURI "file:///root/user/john/"
        cntxt.setBaseURI("file:///root/user/john/");
        XQExpression expr2 = conn.createExpression(cntxt);
        ...


<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                                                            |
    |-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                        | `declareNamespace``(java.lang.String prefix, java.lang.String uri)`<br>Declares a namespace prefix and associates it with a namespace URI.                        |
    | `java.lang.String`            | `getBaseURI``()`<br>Gets the Base URI, if set in the static context, else the empty string.                                                                       |
    | `int`                         | `getBindingMode``()`<br>Gets the value of the binding mode property.                                                                                              |
    | `int`                         | `getBoundarySpacePolicy``()`<br>Gets the boundary-space policy defined in the static context.                                                                     |
    | `int`                         | `getConstructionMode``()`<br>Gets the construction mode defined in the static context.                                                                            |
    | [`XQItemType`](XQItemType.md) | `getContextItemStaticType``()`<br>Gets the static type of the context item.                                                                                       |
    | `int`                         | `getCopyNamespacesModeInherit``()`<br>Gets the inherit part of the copy-namespaces mode defined in the static context.                                            |
    | `int`                         | `getCopyNamespacesModePreserve``()`<br>Gets the preserve part of the copy-namespaces mode defined in the static context.                                          |
    | `java.lang.String`            | `getDefaultCollation``()`<br>Gets the URI of the default collation.                                                                                               |
    | `java.lang.String`            | `getDefaultElementTypeNamespace``()`<br>Gets the URI of the default element/type namespace, the empty string if not set.                                          |
    | `java.lang.String`            | `getDefaultFunctionNamespace``()`<br>Gets the URI of the default function namespace, the empty string if not set.                                                 |
    | `int`                         | `getDefaultOrderForEmptySequences``()`<br>Gets the default order for empty sequences defined in the static context.                                               |
    | `int`                         | `getHoldability``()`<br>Gets the value of the holdability property.                                                                                               |
    | `java.lang.String[]`          | `getNamespacePrefixes``()`<br>Returns the prefixes of all the statically known namespaces.                                                                        |
    | `java.lang.String`            | `getNamespaceURI``(java.lang.String prefix)`<br>Retrieves the namespace URI associated with a prefix.                                                             |
    | `int`                         | `getOrderingMode``()`<br>Gets the ordering mode defined in the static context.                                                                                    |
    | `int`                         | `getQueryLanguageTypeAndVersion``()`<br>Gets the value of the language type and version property.                                                                 |
    | `int`                         | `getQueryTimeout``()`<br>Retrieves the number of seconds an implementation will wait for a query to execute.                                                      |
    | `int`                         | `getScrollability``()`<br>Gets the value of the scrollability property.                                                                                           |
    | `void`                        | `setBaseURI``(java.lang.String baseUri)`<br>Sets the Base URI in the static context, specify the empty string to make it undefined.                               |
    | `void`                        | `setBindingMode``(int bindingMode)`<br>Sets the binding mode property.                                                                                            |
    | `void`                        | `setBoundarySpacePolicy``(int policy)`<br>Sets the boundary-space policy in the static context.                                                                   |
    | `void`                        | `setConstructionMode``(int mode)`<br>Sets the construction mode in the static context.                                                                            |
    | `void`                        | `setContextItemStaticType``(`[`XQItemType`](XQItemType.md)` contextItemType)`<br>Sets the static type of the context item, specify `null` to make it unspecified. |
    | `void`                        | `setCopyNamespacesModeInherit``(int mode)`<br>Sets the inherit part of the copy-namespaces mode in the static context.                                            |
    | `void`                        | `setCopyNamespacesModePreserve``(int mode)`<br>Sets the preserve part of the copy-namespaces mode in the static context.                                          |
    | `void`                        | `setDefaultCollation``(java.lang.String uri)`<br>Sets the URI of the default collation.                                                                           |
    | `void`                        | `setDefaultElementTypeNamespace``(java.lang.String uri)`<br>Sets the URI of the default element/type namespace, the empty string to make it unspecified.          |
    | `void`                        | `setDefaultFunctionNamespace``(java.lang.String uri)`<br>Sets the URI of the default function namespace, the empty string to make it unspecified.                 |
    | `void`                        | `setDefaultOrderForEmptySequences``(int order)`<br>Sets the default order for empty sequences in the static context.                                              |
    | `void`                        | `setHoldability``(int holdability)`<br>Sets the holdability property.                                                                                             |
    | `void`                        | `setOrderingMode``(int mode)`<br>Sets the ordering mode in the static context.                                                                                    |
    | `void`                        | `setQueryLanguageTypeAndVersion``(int langType)`<br>Sets the input query language type and version.                                                               |
    | `void`                        | `setQueryTimeout``(int seconds)`<br>Sets the number of seconds an implementation will wait for a query to execute.                                                |
    | `void`                        | `setScrollability``(int scrollability)`<br>Sets the scrollability of the result sequence.                                                                         |

<!-- -->

- - ### Method Detail

    - #### getNamespacePrefixes

          java.lang.String[] getNamespacePrefixes()

      Returns the prefixes of all the statically known namespaces. Use the `getNamespaceURI` method to look up the namespace URI corresponding to a specific prefix.
      Returns:
      `String` array containing the namespace prefixes. Cannot be `null`

    <!-- -->

    - #### getNamespaceURI

          java.lang.String getNamespaceURI(java.lang.String prefix)
                                    throws XQException

      Retrieves the namespace URI associated with a prefix. An `XQException` is thrown if an unknown prefix is specified, i.e. a prefix not returned by the `getInScopeNamespacePrefixes` method.
      Parameters:
      `prefix` - the prefix for which the namespace URI is sought. Cannot be `null`

      Returns:
      the namespace URI. Cannot be `null`

      Throws:
      [`XQException`](XQException.md) - if a `null` prefix is specified or if the prefix is unknown

    <!-- -->

    - #### declareNamespace

          void declareNamespace(java.lang.String prefix,
                                java.lang.String uri)
                         throws XQException

      Declares a namespace prefix and associates it with a namespace URI. If the namespace URI is the empty string, the prefix is removed from the in-scope namespace definitions.
      Parameters:
      `prefix` - the prefix for the namespace URI

      `uri` - the namespace URI. An empty string undeclares the specific prefix. Cannot be `null`

      Throws:
      [`XQException`](XQException.md) - if (1) a `null` prefix, or (2) a `null` namespace URI is specified

    <!-- -->

    - #### getDefaultElementTypeNamespace

          java.lang.String getDefaultElementTypeNamespace()

      Gets the URI of the default element/type namespace, the empty string if not set.
      Returns:
      the URI of the default element/type namespace, if set, else the empty string. Cannot be `null`

    <!-- -->

    - #### setDefaultElementTypeNamespace

          void setDefaultElementTypeNamespace(java.lang.String uri)
                                       throws XQException

      Sets the URI of the default element/type namespace, the empty string to make it unspecified.
      Parameters:
      `uri` - the namespace URI of the default element/type namespace, the empty string to make it unspecified. Cannot be `null`.

      Throws:
      [`XQException`](XQException.md) - if a `null` uri is specified

    <!-- -->

    - #### getDefaultFunctionNamespace

          java.lang.String getDefaultFunctionNamespace()

      Gets the URI of the default function namespace, the empty string if not set.
      Returns:
      the URI of the default function namespace, if set, else the empty string. Cannot be `null`

    <!-- -->

    - #### setDefaultFunctionNamespace

          void setDefaultFunctionNamespace(java.lang.String uri)
                                    throws XQException

      Sets the URI of the default function namespace, the empty string to make it unspecified.
      Parameters:
      `uri` - the namespace URI of the default function namespace, the empty string to make it unspecified. Cannot be `null`.

      Throws:
      [`XQException`](XQException.md) - if a `null` URI is specified

    <!-- -->

    - #### getContextItemStaticType

          XQItemType getContextItemStaticType()

      Gets the static type of the context item. `null` if unspecified.
      Returns:
      the static type of the context item, if set, else `null`

    <!-- -->

    - #### setContextItemStaticType

          void setContextItemStaticType(XQItemType contextItemType)
                                 throws XQException

      Sets the static type of the context item, specify `null` to make it unspecified.
      Parameters:
      `contextItemType` - the static type of the context item; `null` if unspecified.

      Throws:
      [`XQException`](XQException.md) - if the `contextItemType` is not a valid `XQItemType`

    <!-- -->

    - #### getDefaultCollation

          java.lang.String getDefaultCollation()

      Gets the URI of the default collation.
      Returns:
      the URI of the default collation. Cannot be `null`.

    <!-- -->

    - #### setDefaultCollation

          void setDefaultCollation(java.lang.String uri)
                            throws XQException

      Sets the URI of the default collation.
      Parameters:
      `uri` - the namespace URI of the default collation. Cannot be `null`.

      Throws:
      [`XQException`](XQException.md) - if a `null` URI is specified

    <!-- -->

    - #### getConstructionMode

          int getConstructionMode()

      Gets the construction mode defined in the static context.
      Returns:
      construction mode value. One of: `XQConstants.CONSTRUCTION_MODE_PRESERVE`, `XQConstants.CONSTRUCTION_MODE_STRIP`

    <!-- -->

    - #### setConstructionMode

          void setConstructionMode(int mode)
                            throws XQException

      Sets the construction mode in the static context.
      Parameters:
      `mode` - construction mode value. One of: `XQConstants.CONSTRUCTION_MODE_PRESERVE`, `XQConstants.CONSTRUCTION_MODE_STRIP`.

      Throws:
      [`XQException`](XQException.md) - the specified mode is different from `XQConstants.CONSTRUCTION_MODE_PRESERVE`, `XQConstants.CONSTRUCTION_MODE_STRIP`

    <!-- -->

    - #### getOrderingMode

          int getOrderingMode()

      Gets the ordering mode defined in the static context.
      Returns:
      ordering mode value. One of: `XQConstants.ORDERING_MODE_ORDERED`, `XQConstants.ORDERING_MODE_UNORDERED`.

    <!-- -->

    - #### setOrderingMode

          void setOrderingMode(int mode)
                        throws XQException

      Sets the ordering mode in the static context.
      Parameters:
      `mode` - ordering mode value. One of: `XQConstants.ORDERING_MODE_ORDERED`, `XQConstants.ORDERING_MODE_UNORDERED`.

      Throws:
      [`XQException`](XQException.md) - the specified mode is different from `XQConstants.ORDERING_MODE_ORDERED`, `XQConstants.ORDERING_MODE_UNORDERED`

    <!-- -->

    - #### getDefaultOrderForEmptySequences

          int getDefaultOrderForEmptySequences()

      Gets the default order for empty sequences defined in the static context.
      Returns:
      default order for empty sequences value. One of: `XQConstants.DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_GREATEST`, `XQConstants.DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_LEAST`.

    <!-- -->

    - #### setDefaultOrderForEmptySequences

          void setDefaultOrderForEmptySequences(int order)
                                         throws XQException

      Sets the default order for empty sequences in the static context.
      Parameters:
      `order` - the default order for empty sequences. One of: `XQConstants.DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_GREATEST`, `XQConstants.DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_LEAST`.

      Throws:
      [`XQException`](XQException.md) - the specified order for empty sequences is different from `XQConstants.DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_GREATEST`, `XQConstants.DEFAULT_ORDER_FOR_EMPTY_SEQUENCES_LEAST`

    <!-- -->

    - #### getBoundarySpacePolicy

          int getBoundarySpacePolicy()

      Gets the boundary-space policy defined in the static context.
      Returns:
      the boundary-space policy value. One of: `XQConstants.BOUNDARY_SPACE_PRESERVE`, `XQConstants.BOUNDARY_SPACE_STRIP`.

    <!-- -->

    - #### setBoundarySpacePolicy

          void setBoundarySpacePolicy(int policy)
                               throws XQException

      Sets the boundary-space policy in the static context.
      Parameters:
      `policy` - boundary space policy. One of: `XQConstants.BOUNDARY_SPACE_PRESERVE`, `XQConstants.BOUNDARY_SPACE_STRIP`.

      Throws:
      [`XQException`](XQException.md) - the specified mode is different from `XQConstants.BOUNDARY_SPACE_PRESERVE`, `XQConstants.BOUNDARY_SPACE_STRIP`

    <!-- -->

    - #### getCopyNamespacesModePreserve

          int getCopyNamespacesModePreserve()

      Gets the preserve part of the copy-namespaces mode defined in the static context.
      Returns:
      construction mode value. One of: `XQConstants.COPY_NAMESPACES_MODE_PRESERVE`, `XQConstants.COPY_NAMESPACES_MODE_NO_PRESERVE`.

    <!-- -->

    - #### setCopyNamespacesModePreserve

          void setCopyNamespacesModePreserve(int mode)
                                      throws XQException

      Sets the preserve part of the copy-namespaces mode in the static context.
      Parameters:
      `mode` - ordering mode value. One of: `XQConstants.COPY_NAMESPACES_MODE_PRESERVE`, `XQConstants.COPY_NAMESPACES_MODE_NO_PRESERVE`.

      Throws:
      [`XQException`](XQException.md) - the specified mode is different from `XQConstants.COPY_NAMESPACES_MODE_PRESERVE`, `XQConstants.COPY_NAMESPACES_MODE_NO_PRESERVE`

    <!-- -->

    - #### getCopyNamespacesModeInherit

          int getCopyNamespacesModeInherit()

      Gets the inherit part of the copy-namespaces mode defined in the static context.
      Returns:
      construction mode value. One of: `XQConstants.COPY_NAMESPACES_MODE_INHERIT`, `XQConstants.COPY_NAMESPACES_MODE_NO_INHERIT`.

    <!-- -->

    - #### setCopyNamespacesModeInherit

          void setCopyNamespacesModeInherit(int mode)
                                     throws XQException

      Sets the inherit part of the copy-namespaces mode in the static context.
      Parameters:
      `mode` - ordering mode value. One of: `XQConstants.COPY_NAMESPACES_MODE_INHERIT`, `XQConstants.COPY_NAMESPACES_MODE_NO_INHERIT`.

      Throws:
      [`XQException`](XQException.md) - the specified mode is different from `XQConstants.COPY_NAMESPACES_MODE_INHERIT`, `XQConstants.COPY_NAMESPACES_MODE_NO_INHERIT`

    <!-- -->

    - #### getBaseURI

          java.lang.String getBaseURI()

      Gets the Base URI, if set in the static context, else the empty string.
      Returns:
      the base URI, if set, else the empty string. Cannot be `null`..

    <!-- -->

    - #### setBaseURI

          void setBaseURI(java.lang.String baseUri)
                   throws XQException

      Sets the Base URI in the static context, specify the empty string to make it undefined.
      Parameters:
      `baseUri` - the new baseUri, or empty string to make it undefined. Cannot be `null`.

      Throws:
      [`XQException`](XQException.md) - if a `null` base uri is specified

    <!-- -->

    - #### getBindingMode

          int getBindingMode()

      Gets the value of the binding mode property. By default an XQJ implementation operates in immediate binding mode.
      Returns:
      the binding mode. One of `XQConstants.BINDING_MODE_IMMEDIATE`, or`XQConstants.BINDING_MODE_DEFERRED`.

    <!-- -->

    - #### setBindingMode

          void setBindingMode(int bindingMode)
                       throws XQException

      Sets the binding mode property. By default an XQJ implementation operates in immediate binding mode.
      Parameters:
      `bindingMode` - the binding mode. One of: `XQConstants.BINDING_MODE_IMMEDIATE`, or`XQConstants.BINDING_MODE_DEFERRED`.

      Throws:
      [`XQException`](XQException.md) - the specified mode is different from `XQConstants.BINDING_MODE_IMMEDIATE`, `XQConstants.BINDING_MODE_DEFERRED`

    <!-- -->

    - #### getHoldability

          int getHoldability()

      Gets the value of the holdability property.
      Returns:
      the type of a result's holdability. One of: `XQConstants.HOLDTYPE_HOLD_CURSORS_OVER_COMMIT`, or `XQConstants.HOLDTYPE_CLOSE_CURSORS_AT_COMMIT`.

    <!-- -->

    - #### setHoldability

          void setHoldability(int holdability)
                       throws XQException

      Sets the holdability property.
      Parameters:
      `holdability` - the holdability of the result. One of: `XQConstants.HOLDTYPE_HOLD_CURSORS_OVER_COMMIT`, or `XQConstants.HOLDTYPE_CLOSE_CURSORS_AT_COMMIT`.

      Throws:
      [`XQException`](XQException.md) - the specified holdability is different from `XQConstants.HOLDTYPE_HOLD_CURSORS_OVER_COMMIT`, `XQConstants.HOLDTYPE_CLOSE_CURSORS_AT_COMMIT`

    <!-- -->

    - #### getQueryLanguageTypeAndVersion

          int getQueryLanguageTypeAndVersion()

      Gets the value of the language type and version property. By default an XQJ implementation's default is `XQConstants.LANGTYPE_XQUERY`.
      Returns:
      the language type and version. One of: `XQConstants.LANGTYPE_XQUERY`, or `XQConstants.LANGTYPE_XQUERYX` or a negative value indicating a vendor specific query language type and version.

    <!-- -->

    - #### setQueryLanguageTypeAndVersion

          void setQueryLanguageTypeAndVersion(int langType)
                                       throws XQException

      Sets the input query language type and version. When this is set to a particular language type and version, then the query is assumed to be in that language and version.
      Parameters:
      `langType` - the query language type and version of the inputs. One of: `XQConstants.LANGTYPE_XQUERY` (default), or `XQConstants.LANGTYPE_XQUERYX`. A negative number indicates a vendor specific query language type and version.

      Throws:
      [`XQException`](XQException.md) - the specified langtype is different from `XQConstants.LANGTYPE_XQUERY`, `XQConstants.LANGTYPE_XQUERYX` and is not negative

    <!-- -->

    - #### getScrollability

          int getScrollability()

      Gets the value of the scrollability property. By default query results are forward only.
      Returns:
      the type of a result's scrollability. One of: `XQConstants.SCROLLTYPE_FORWARD_ONLY`, or `XQConstants.SCROLLTYPE_SCROLLABLE`.

    <!-- -->

    - #### setScrollability

          void setScrollability(int scrollability)
                         throws XQException

      Sets the scrollability of the result sequence. By default query results are forward only.
      Parameters:
      `scrollability` - the scrollability of the result. One of: `XQConstants.SCROLLTYPE_FORWARD_ONLY`, or `XQConstants.SCROLLTYPE_SCROLLABLE`.

      Throws:
      [`XQException`](XQException.md) - the specified crollability type is different from `XQConstants.SCROLLTYPE_FORWARD_ONLY`, `XQConstants.SCROLLTYPE_SCROLLABLE`

    <!-- -->

    - #### getQueryTimeout

          int getQueryTimeout()

      Retrieves the number of seconds an implementation will wait for a query to execute.
      Returns:
      the query execution timeout value in seconds. A value of 0 indicates no limit.

    <!-- -->

    - #### setQueryTimeout

          void setQueryTimeout(int seconds)
                        throws XQException

      Sets the number of seconds an implementation will wait for a query to execute. If the implementation does not support query timeout it can ignore the specified timeout value. It the limit is exceeded, the behavor of the query is the same as an execution of a cancel by another thread.
      Parameters:
      `seconds` - the query execution timeout value in seconds. A value of 0 indicates no limit

      Throws:
      [`XQException`](XQException.md) - if the passed in value is negative

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

- **[Prev Class](XQStackTraceVariable.md)**
- **Next Class**

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
