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

- **[Prev Class](XQDataSource.md)**
- **[Next Class](XQException.md)**

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

## **Interface XQDynamicContext**

- **All Known Subinterfaces:**
  **[XQExpression](XQExpression.md), [XQPreparedExpression](XQPreparedExpression.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQDynamicContext

  **`XQDynamicContext` provides access to the dynamic context as defined in [*2.1.2 Dynamic Context, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#eval_context). The following components can be accessed:**
  - **The context item can be set**
  - **The variable values can be bound**
  - **The implicit time zone can be retrieved or specified**

  **Where the prolog of the expression specifies the static type of external variables, this interface allows the dynamic type and value of the variable to be specified. Note that in case of an `XQPreparedExpression`, values may only be bound to those variables that are defined in the prolog of the expression.**
  **Example -**

        XQConnection conn = XQDataSource.getConnection();

        // create an XQPreparedExpression with external variable
        XQPreparedExpression e1 = conn.prepareExpression("declare variable $i as xs:int external;
                                                          $i + 10");

        // bind an int to the external variable
        e1.bindInt(new QName("i"), 200, null);

        // this will fail as the expression has no external variable $foo
        e1.bindInt(new QName("foo"), 200, null);

        // this will fail as xs:double is not compatible with an external
        variable declared as xs:int
        e1.bindDouble(new QName("i"), 2e2, null);

        // create an XQExpression with external variable

        XQExpression e2 = conn.createExpression();

        // bind a value to $i and $foo
        e2.bindInt(new QName("i"), 200, null);
        e2.bindInt(new QName("foo"), 200, null);

        // the value bound to $foo is ignored as the expression doesn't
        // declare $foo as external variable

        e2.executeQuery("declare variable $i as xs:int external; $i + 10");



  **

  Binding a value to the context item is achieved in the same way as binding a value to an external variable. However, instead of specifying the variable's name as first argument of the `bindXXX()` method, use [`XQConstants.CONTEXT_ITEM`](XQConstants.md) as the first argument.

  Binding mode**
  The default binding mode is immediate. In other words, the external variable value specified by the application is consumed during the `bindXXX()` method.

  An application has the ability to set the binding mode to deferred. In deferred mode an application cannot assume that the bound value will be consumed during the invocation of the `bindXXX` method. In such scenario the order in which the bindings are evaluated is implementation-dependent, and an implementation doesn't necessarily need to consume a binding if it can evaluate the query without requiring the external variable. The XQJ implementation is also free to read the bound value either at bind time or during the subsequent evaluation and processing of the query results.

  Also note that in deferred binding mode, bindings are only active for a single execution cycle. The application is required to explicitly re-bind values to every external variable before each execution. Failing to do so will result in an `XQException`, as the implementation will assume during the next execution that none of the external variables are bound.

  Finally, note that in deferred binding mode, any error condition specified to throw an exception during the `bindXXX()` methods, may as well be thrown later during the query's evaluation.

  Example - in case of an immediate binding mode, bindings stay active over executions

        // BINDING_MODE_IMMEDIATE is the default, no need to change it
        QName v = new QName(v);

        XQPreparedExpression e = c.prepareExpression("declare variable $v
                                                      external; $v");
        e.bindInt(v, 1)

        // successful execution
        e.executeQuery();

        // successful execution
        e.executeQuery();




  Example - in case of a deferred binding mode, bindings are only valid for a single execution
        // BINDING_MODE_IMMEDIATE is the default, change it to
        // BINDING_MODE_DEFERRED
        XQStaticContext cntxt = c.getStaticContext();
        cntxt.setBindingMode(XQConstants.BINDING_MODE_DEFERRED);
        c.setStaticContext(cntxt);

        QName v = new QName(v);

        XQPreparedExpression e = c.prepareExpression("declare variable $v
                                                      external; $v");
        e.bindInt(v, 1)

        // successful execution
        XQSequence s = e.executeQuery();

        while (s.next())
          System.out.println(s.getInt());

        // an error is reported during the next query
        // evaluation as not all external variables are bound
        s = e.executeQuery();

        while (s.next())
          System.out.println(s.getInt());


<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type    | Method and Description                                                                                                                                                                                                             |
    |----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`               | `bindAtomicValue``(javax.xml.namespace.QName varName, java.lang.String value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                          |
    | `void`               | `bindBoolean``(javax.xml.namespace.QName varName, boolean value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                                       |
    | `void`               | `bindByte``(javax.xml.namespace.QName varName, byte value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                                             |
    | `void`               | `bindDocument``(javax.xml.namespace.QName varName, java.io.InputStream value, java.lang.String baseURI, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                |
    | `void`               | `bindDocument``(javax.xml.namespace.QName varName, java.io.Reader value, java.lang.String baseURI, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                     |
    | `void`               | `bindDocument``(javax.xml.namespace.QName varName, `[`Source`](../transform/Source.md)` value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item from the given `Source`. |
    | `void`               | `bindDocument``(javax.xml.namespace.QName varName, java.lang.String value, java.lang.String baseURI, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                   |
    | `void`               | `bindDocument``(javax.xml.namespace.QName varName, javax.xml.stream.XMLStreamReader value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                             |
    | `void`               | `bindDouble``(javax.xml.namespace.QName varName, double value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                                         |
    | `void`               | `bindFloat``(javax.xml.namespace.QName varName, float value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                                           |
    | `void`               | `bindInt``(javax.xml.namespace.QName varName, int value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                                               |
    | `void`               | `bindItem``(javax.xml.namespace.QName varName, `[`XQItem`](XQItem.md)` value)`<br>Binds a value to the given external variable.                                                                                                    |
    | `void`               | `bindLong``(javax.xml.namespace.QName varName, long value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                                             |
    | `void`               | `bindNode``(javax.xml.namespace.QName varName, `[`Node`](../../../org/w3c/dom/Node.md)` value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                         |
    | `void`               | `bindObject``(javax.xml.namespace.QName varName, java.lang.Object value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                               |
    | `void`               | `bindSequence``(javax.xml.namespace.QName varName, `[`XQSequence`](XQSequence.md)` value)`<br>Binds a value to the given external variable or the context item.                                                                    |
    | `void`               | `bindShort``(javax.xml.namespace.QName varName, short value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                                           |
    | `void`               | `bindString``(javax.xml.namespace.QName varName, java.lang.String value, `[`XQItemType`](XQItemType.md)` type)`<br>Binds a value to the given external variable or the context item.                                               |
    | `java.util.TimeZone` | `getImplicitTimeZone``()`<br>Gets the implicit timezone                                                                                                                                                                            |
    | `void`               | `setImplicitTimeZone``(java.util.TimeZone implicitTimeZone)`<br>Sets the implicit timezone                                                                                                                                         |

<!-- -->

- - ### Method Detail

    - #### getImplicitTimeZone

          java.util.TimeZone getImplicitTimeZone()
                                          throws XQException

      Gets the implicit timezone
      Returns:
      the implicit timezone. This may have been set by an application using the `setImplicitTimeZone` method or provided by the implementation

      Throws:
      [`XQException`](XQException.md) - if the expression is in a closed state

    <!-- -->

    - #### bindAtomicValue

          void bindAtomicValue(javax.xml.namespace.QName varName,
                               java.lang.String value,
                               XQItemType type)
                        throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the casting from `xs:string` rules outlined in [*17.1.1 Casting from xs:string and xs:untypedAtomic, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#casting_from_strings). If the cast fails, or if there is a mismatch between the static and dynamic types, an `XQException` is thrown either by this method or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to

      `value` - the lexical string value of the type

      `type` - the item type of the bind

      Throws:
      [`XQException`](XQException.md) - if (1) any of the arguments are `null`, (2) given type is not an atomic type, (3) the conversion of the value to an XDM instance failed, (4) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (5) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (6) the expression is in a closed state

    <!-- -->

    - #### bindString

          void bindString(javax.xml.namespace.QName varName,
                          java.lang.String value,
                          XQItemType type)
                   throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type, which must represent an `xs:string` or a type derived by restriction from `xs:string`. If the specified type is `null`, it defaults to `xs:string`.
      Subsequently the value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0,*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value to be bound to the external variable. The default type, `xs:string`, is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindDocument

          void bindDocument(javax.xml.namespace.QName varName,
                            java.lang.String value,
                            java.lang.String baseURI,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item.

      If the value represents a well-formed XML document, it will be parsed and results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation. If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `baseURI` - an optional base URI, can be `null`. It can be used, for example, to resolve relative URIs and to include in error messages.

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindDocument

          void bindDocument(javax.xml.namespace.QName varName,
                            java.io.Reader value,
                            java.lang.String baseURI,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item.

      If the value represents a well-formed XML document, it will be parsed and results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation. If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `baseURI` - an optional base URI, can be `null`. It can be used, for example, to resolve relative URIs and to include in error messages.

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindDocument

          void bindDocument(javax.xml.namespace.QName varName,
                            java.io.InputStream value,
                            java.lang.String baseURI,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item.

      If the value represents a well-formed XML document, it will be parsed and results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation. If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `baseURI` - an optional base URI, can be `null`. It can be used, for example, to resolve relative URIs and to include in error messages.

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindDocument

          void bindDocument(javax.xml.namespace.QName varName,
                            javax.xml.stream.XMLStreamReader value,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item.

      If the value represents a well-formed XML document, it results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT` or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindDocument

          void bindDocument(javax.xml.namespace.QName varName,
                            Source value,
                            XQItemType type)
                     throws XQException

      Binds a value to the given external variable or the context item from the given `Source`. An XQJ implementation must at least support the following implementations:
      - `javax.xml.transform.dom.DOMSource`
      - `javax.xml.transform.sax.SAXSource`
      - `javax.xml.transform.stream.StreamSource`



      If the value represents a well-formed XML document, it will result in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### setImplicitTimeZone

          void setImplicitTimeZone(java.util.TimeZone implicitTimeZone)
                            throws XQException

      Sets the implicit timezone
      Parameters:
      `implicitTimeZone` - time zone to be set

      Throws:
      [`XQException`](XQException.md) - if the expression is in a closed state

    <!-- -->

    - #### bindItem

          void bindItem(javax.xml.namespace.QName varName,
                        XQItem value)
                 throws XQException

      Binds a value to the given external variable. The dynamic type of the value is derived from the `XQItem`. In case of a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be bound, cannot be `null`

      Throws:
      [`XQException`](XQException.md) - if (1) any of the arguments are `null`, (2) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (3) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, (4) the expression is in a closed state, or (5) the specified item is closed

    <!-- -->

    - #### bindSequence

          void bindSequence(javax.xml.namespace.QName varName,
                            XQSequence value)
                     throws XQException

      Binds a value to the given external variable or the context item. The input sequence is consumed from its current position to the end, after which the input sequence's position will be set to point after the last item. The dynamic type of the value is derived from the items in the sequence. In case of a mismatch between the static and dynamic types, an `XQException` is be raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be bound, cannot be `null`

      Throws:
      [`XQException`](XQException.md) - if (1) any of the arguments are `null`, (2) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (3) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, (4) the expression is in a closed state, or (5) the specified sequence is closed

    <!-- -->

    - #### bindObject

          void bindObject(javax.xml.namespace.QName varName,
                          java.lang.Object value,
                          XQItemType type)
                   throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindBoolean

          void bindBoolean(javax.xml.namespace.QName varName,
                           boolean value,
                           XQItemType type)
                    throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindByte

          void bindByte(javax.xml.namespace.QName varName,
                        byte value,
                        XQItemType type)
                 throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindDouble

          void bindDouble(javax.xml.namespace.QName varName,
                          double value,
                          XQItemType type)
                   throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluations.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindFloat

          void bindFloat(javax.xml.namespace.QName varName,
                         float value,
                         XQItemType type)
                  throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluations.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindInt

          void bindInt(javax.xml.namespace.QName varName,
                       int value,
                       XQItemType type)
                throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluations.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindLong

          void bindLong(javax.xml.namespace.QName varName,
                        long value,
                        XQItemType type)
                 throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindNode

          void bindNode(javax.xml.namespace.QName varName,
                        Node value,
                        XQItemType type)
                 throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` or `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

    <!-- -->

    - #### bindShort

          void bindShort(javax.xml.namespace.QName varName,
                         short value,
                         XQItemType type)
                  throws XQException

      Binds a value to the given external variable or the context item. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, or if there is a mismatch between the static and dynamic types, an `XQException` is raised either by this method, or during query evaluation.
      Parameters:
      `varName` - the name of the external variable to bind to, cannot be `null`

      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Throws:
      [`XQException`](XQException.md) - if (1) the `varName` argument is `null`, (2) the conversion of the value to an XDM instance failed, (3) in case of an `XQPreparedExpression`, the dynamic type of the bound value is not compatible with the static type of the variable, (4) in case of an `XQPreparedExpression`, the variable is not defined in the prolog of the expression, or (5) if the expression is in a closed state

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

- **[Prev Class](XQDataSource.md)**
- **[Next Class](XQException.md)**

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
