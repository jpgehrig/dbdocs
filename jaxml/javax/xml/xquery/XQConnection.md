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

- **[Prev Class](XQCancelledException.md)**
- **[Next Class](XQConnectionEvent.md)**

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

## **Interface XQConnection**

- **All Superinterfaces:**
  **[XQDataFactory](XQDataFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQConnection
      extends XQDataFactory

  **A connection (session) with a specific XQuery engine. Connections are obtained through an `XQDataSource` object.**
  **XQuery expressions are executed and results are returned within the context of a connection. They are either executed through `XQExpression` or `XQPreparedExpression` objects.**

        XQDataSource ds;// obtain the XQuery datasource
        ...
        XQConnection conn = ds.getConnection();

        XQPreparedExpression expr = conn.prepareExpression("for $i in ...");
        XQResultSequence result = expr.executeQuery();
        // - or -
        XQExpression expr = conn.createExpression();
        XQSequence result = expr.executeQuery("for $i in..");

        // The sequence can now be iterated
        while (result.next())
        {
           String str  = result.getItemAsString();
           System.out.println(" output "+ str);
        }
        result.close();
        expr.close();
        conn.close();  // close the connection and free all resources..



  **A connection holds also default values for `XQExpression` and `XQPreparedExpression` properties. An application can override these defaults by passing an `XQStaticContext` object to the `setStaticContext()` method.**
  **By default a connection operates in auto-commit mode, which means that each xquery is executed and committed in an individual transaction. If auto-commit mode is disabled, a transaction must be ended explicitly by the application calling `commit()` or `rollback()`.**

  **An `XQConnection` object can be created on top of an existing JDBC connection. If an `XQConnection` is created on top of the JDBC connection, it inherits the transaction context from the JDBC connection. Also, in this case, if the auto-commit mode is changed, or a transaction is ended using commit or rollback, it also changes the underlying JDBC connection.**

  **An XQJ driver is not required to provide finalizer methods for the connection and other objects. Hence it is strongly recommended that users call close method explicitly to free any resources. It is also recommended that they do so under a final block to ensure that the object is closed even when there are exceptions. Not closing this object explicitly might result in serious memory leaks.**

  **When the `XQConnection` is closed any `XQExpression` and `XQPreparedExpression` objects obtained from it are also implicitly closed.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                              |
    |---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                            | `close``()`<br>Closes the connection.                                                                                                                                                               |
    | `void`                                            | `commit``()`<br>Makes all changes made in the current transaction permanent and releases any locks held by the datasource.                                                                          |
    | [`XQExpression`](XQExpression.md)                 | `createExpression``()`<br>Creates a new `XQExpression` object that can be used to perform execute immediate operations with XQuery expressions.                                                     |
    | [`XQExpression`](XQExpression.md)                 | `createExpression``(`[`XQStaticContext`](XQStaticContext.md)` properties)`<br>Creates a new `XQExpression` object that can be used to perform execute immediate operations with XQuery expressions. |
    | `boolean`                                         | `getAutoCommit``()`<br>Gets the auto-commit attribute of this connection                                                                                                                            |
    | [`XQMetaData`](XQMetaData.md)                     | `getMetaData``()`<br>Gets the metadata for this connection.                                                                                                                                         |
    | [`XQStaticContext`](XQStaticContext.md)           | `getStaticContext``()`<br>Gets an `XQStaticContext` representing the default values for all expression properties.                                                                                  |
    | `boolean`                                         | `isClosed``()`<br>Checks if the connection is closed.                                                                                                                                               |
    | [`XQPreparedExpression`](XQPreparedExpression.md) | `prepareExpression``(java.io.InputStream xquery)`<br>Prepares an expression for execution.                                                                                                          |
    | [`XQPreparedExpression`](XQPreparedExpression.md) | `prepareExpression``(java.io.InputStream xquery, `[`XQStaticContext`](XQStaticContext.md)` properties)`<br>Prepares an expression for execution.                                                    |
    | [`XQPreparedExpression`](XQPreparedExpression.md) | `prepareExpression``(java.io.Reader xquery)`<br>Prepares an expression for execution.                                                                                                               |
    | [`XQPreparedExpression`](XQPreparedExpression.md) | `prepareExpression``(java.io.Reader xquery, `[`XQStaticContext`](XQStaticContext.md)` properties)`<br>Prepares an expression for execution.                                                         |
    | [`XQPreparedExpression`](XQPreparedExpression.md) | `prepareExpression``(java.lang.String xquery)`<br>Prepares an expression for execution.                                                                                                             |
    | [`XQPreparedExpression`](XQPreparedExpression.md) | `prepareExpression``(java.lang.String xquery, `[`XQStaticContext`](XQStaticContext.md)` properties)`<br>Prepares an expression for execution.                                                       |
    | `void`                                            | `rollback``()`<br>Undoes all changes made in the current transaction and releases any locks held by the datasource.                                                                                 |
    | `void`                                            | `setAutoCommit``(boolean autoCommit)`<br>Sets the auto-commit attribute to the given state.                                                                                                         |
    | `void`                                            | `setStaticContext``(`[`XQStaticContext`](XQStaticContext.md)` properties)`<br>Sets the default values for all expression properties.                                                                |

    - ### Methods inherited from interface javax.xml.xquery.[XQDataFactory](XQDataFactory.md)

      [`createAtomicType`](XQDataFactory.md)`, `[`createAtomicType`](XQDataFactory.md)`, `[`createAttributeType`](XQDataFactory.md)`, `[`createAttributeType`](XQDataFactory.md)`, `[`createCommentType`](XQDataFactory.md)`, `[`createDocumentElementType`](XQDataFactory.md)`, `[`createDocumentSchemaElementType`](XQDataFactory.md)`, `[`createDocumentType`](XQDataFactory.md)`, `[`createElementType`](XQDataFactory.md)`, `[`createElementType`](XQDataFactory.md)`, `[`createItem`](XQDataFactory.md)`, `[`createItemFromAtomicValue`](XQDataFactory.md)`, `[`createItemFromBoolean`](XQDataFactory.md)`, `[`createItemFromByte`](XQDataFactory.md)`, `[`createItemFromDocument`](XQDataFactory.md)`, `[`createItemFromDocument`](XQDataFactory.md)`, `[`createItemFromDocument`](XQDataFactory.md)`, `[`createItemFromDocument`](XQDataFactory.md)`, `[`createItemFromDocument`](XQDataFactory.md)`, `[`createItemFromDouble`](XQDataFactory.md)`, `[`createItemFromFloat`](XQDataFactory.md)`, `[`createItemFromInt`](XQDataFactory.md)`, `[`createItemFromLong`](XQDataFactory.md)`, `[`createItemFromNode`](XQDataFactory.md)`, `[`createItemFromObject`](XQDataFactory.md)`, `[`createItemFromShort`](XQDataFactory.md)`, `[`createItemFromString`](XQDataFactory.md)`, `[`createItemType`](XQDataFactory.md)`, `[`createNodeType`](XQDataFactory.md)`, `[`createProcessingInstructionType`](XQDataFactory.md)`, `[`createSchemaAttributeType`](XQDataFactory.md)`, `[`createSchemaElementType`](XQDataFactory.md)`, `[`createSequence`](XQDataFactory.md)`, `[`createSequence`](XQDataFactory.md)`, `[`createSequenceType`](XQDataFactory.md)`, `[`createTextType`](XQDataFactory.md)

<!-- -->

- - ### Method Detail

    - #### close

          void close()
              throws XQException

      Closes the connection. This also closes any `XQExpression` and `XQPreparedExpression` obtained from this connection. Once the connection is closed, no method other than `close` or the `isClosed` method may be called on the connection object. Calling close on an `XQConnection` object that is already closed has no effect. Note that an XQJ driver is not required to provide finalizer methods for the connection and other objects. Hence it is strongly recommended that users call this method explicitly to free any resources. It is also recommended that they do so under a final block to ensure that the object is closed even when there are exceptions.
      Throws:
      [`XQException`](XQException.md) - if there is an error during closing the connection.

    <!-- -->

    - #### setAutoCommit

          void setAutoCommit(boolean autoCommit)
                      throws XQException

      Sets the auto-commit attribute to the given state. If a connection is in auto-commit mode, each xquery is executed and committed in an individual transaction. When auto-commit mode is disabled, xqueries are grouped in a transaction that must be ended explicitly by the application calling `commit()` or `rollback()`.
      By default, new connections are in auto-commit mode.
      If the value of auto-commit is changed in the middle of a transaction, the transaction is committed. If `setAutoCommit` is called and the auto-commit attribute is not changed from its current value, the request is treated as a no-op.
      Parameters:
      `autoCommit` - `true` to enable auto-commit mode; `false` to disable it

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, or (2) auto-commit is turned off but the implementation doesn't support transactions

    <!-- -->

    - #### getAutoCommit

          boolean getAutoCommit()
                         throws XQException

      Gets the auto-commit attribute of this connection
      Returns:
      the auto-commit attribute of this connection. `true` if the connection operates in auto-commit mode; otherwise `false`

      Throws:
      [`XQException`](XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### commit

          void commit()
               throws XQException

      Makes all changes made in the current transaction permanent and releases any locks held by the datasource. This method should be used only when auto-commit mode is disabled. Any `XQResultSequence`, or `XQResultItem` may be implicitly closed upon commit, if the holdability property of the sequence is set to `XQConstants.HOLDTYPE_CLOSE_CURSORS_AT_COMMIT`.
      Throws:
      [`XQException`](XQException.md) - if the connection is in a closed state or this connection is operating in auto-commit mode

    <!-- -->

    - #### createExpression

          XQExpression createExpression()
                                 throws XQException

      Creates a new `XQExpression` object that can be used to perform execute immediate operations with XQuery expressions. The properties of the connection's default `XQStaticContext` are copied to the returned `XQExpression`.
      Returns:
      `XQExpression` that can be used to execute multiple expressions

      Throws:
      [`XQException`](XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### createExpression

          XQExpression createExpression(XQStaticContext properties)
                                 throws XQException

      Creates a new `XQExpression` object that can be used to perform execute immediate operations with XQuery expressions. The properties of the specified `XQStaticContext` values are copied to the returned `XQExpression`.
      Parameters:
      `properties` - `XQStaticContext` containing values of expression properties

      Returns:
      `XQExpression` that can be used to execute multiple expressions

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, or (2) the specified argument is `null`

    <!-- -->

    - #### getMetaData

          XQMetaData getMetaData()
                          throws XQException

      Gets the metadata for this connection.
      Returns:
      `XQMetadata` representing the metadata of this connection

      Throws:
      [`XQException`](XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### isClosed

          boolean isClosed()

      Checks if the connection is closed.
      Returns:
      `true` if the connection is in a closed state, `false` otherwise

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(java.lang.String xquery)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the connection's default `XQStaticContext` are copied to the returned `XQPreparedExpression`.

      Parameters:
      `xquery` - the XQuery expression as a `String`. Cannot be `null`

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, (2) there are errors preparing the expression, or (3) the xquery parameter is `null`

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(java.lang.String xquery,
                                                 XQStaticContext properties)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the specified `XQStaticContext` values are copied to the returned `XQPreparedExpression`.

      Parameters:
      `xquery` - the XQuery expression as a `String`. Cannot be `null`

      `properties` - `XQStaticContext` containing values of expression properties.

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, or (2) the specified argument is `null`

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(java.io.Reader xquery)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the connection's default `XQStaticContext` are copied to the returned `XQPreparedExpression`.

      Parameters:
      `xquery` - the XQuery expression as a `Reader`. Cannot be `null`

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, (2) there are errors preparing the expression, or (3) the xquery parameter is `null`

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(java.io.Reader xquery,
                                                 XQStaticContext properties)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the specified `XQStaticContext` values are copied to the returned `XQPreparedExpression`.

      Parameters:
      `xquery` - the XQuery expression as a `Reader`. Cannot be `null`

      `properties` - `XQStaticContext` containing values of expression properties

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, or (2) the specified argument is `null`

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(java.io.InputStream xquery)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the connection's default `XQStaticContext` are copied to the returned `XQPreparedExpression`.

      Parameters:
      `xquery` - the XQuery expression as an `InputStream`. Cannot be `null`

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, (2) there are errors preparing the expression or (3) the xquery parameter is `null`

    <!-- -->

    - #### prepareExpression

          XQPreparedExpression prepareExpression(java.io.InputStream xquery,
                                                 XQStaticContext properties)
                                          throws XQException

      Prepares an expression for execution.
      The properties of the specified `XQStaticContext` values are copied to the returned `XQPreparedExpression`.

      Parameters:
      `xquery` - the XQuery expression as an `InputStream`. Cannot be `null`

      `properties` - `XQStaticContext` containing values of expression properties

      Returns:
      the prepared XQuery expression

      Throws:
      [`XQException`](XQException.md) - if (1) the connection is in a closed state, or (2) the specified argument is `null`

    <!-- -->

    - #### rollback

          void rollback()
                 throws XQException

      Undoes all changes made in the current transaction and releases any locks held by the datasource. This method should be used only when auto-commit mode is disabled.
      Throws:
      [`XQException`](XQException.md) - if the connection is in a closed state or this connection is operating in auto-commit mode

    <!-- -->

    - #### getStaticContext

          XQStaticContext getStaticContext()
                                    throws XQException

      Gets an `XQStaticContext` representing the default values for all expression properties. In order to modify the defaults, it is not sufficient to modify the values in the returned `XQStaticContext` object; in addition `setStaticContext` should be called to make those new values effective.
      Returns:
      `XQStaticContext` representing the default values for all expression properties

      Throws:
      [`XQException`](XQException.md) - if the connection is in a closed state

    <!-- -->

    - #### setStaticContext

          void setStaticContext(XQStaticContext properties)
                         throws XQException

      Sets the default values for all expression properties. The implementation will read out all expression properties from the specified `XQStaticContext` and update its private copy.
      Parameters:
      `properties` - `XQStaticContext` containing values of expression properties

      Throws:
      [`XQException`](XQException.md) - if the connection is in a closed state

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

- **[Prev Class](XQCancelledException.md)**
- **[Next Class](XQConnectionEvent.md)**

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
