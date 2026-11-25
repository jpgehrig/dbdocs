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

- **[Prev Class](XQException.md)**
- **[Next Class](XQItem.md)**

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

## **Interface XQExpression**

- **All Superinterfaces:**
  **[XQDynamicContext](XQDynamicContext.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQExpression
      extends XQDynamicContext

  **This interface describes the execute immediate functionality for expressions. This object can be created from the `XQConnection` and the execution can be done using the `executeQuery()` or `executeCommand()` method, passing in the XQuery expression.**
  **All external variables defined in the prolog of the expression to be executed must be set in the dynamic context of this expression using the bind methods. Also, variables bound in this expression but not defined as external in the prolog of the expression to be executed, are simply ignored. For example, if variables `$var1` and `$var2` are bound, but the query only defines `$var1` as external, no error will be reported for the binding of `$var2`. It will simply be ignored. When the expression is executed using the `executeQuery` method, if the execution is successful, then an `XQResultSequence` object is returned. The `XQResultSequence` object is tied to the `XQExpression` from which it was prepared and is closed implicitly if that `XQExpression` is either closed or re-executed.**

  **The `XQExpression` object is dependent on the `XQConnection` object from which it was created and is only valid for the duration of that object. Thus, if the `XQConnection` object is closed then this `XQExpression` object will be implicitly closed and it can no longer be used.**

  **An XQJ driver is not required to provide finalizer methods for the connection and other objects. Hence it is strongly recommended that users call close method explicitly to free any resources. It is also recommended that they do so under a final block to ensure that the object is closed even when there are exceptions. Not closing this object implicitly or explicitly might result in serious memory leaks.**

  **When the `XQExpression` is closed any `XQResultSequence` object obtained from it is also implicitly closed.**

  **Example -**

        XQConnection conn = XQDatasource.getConnection();
        XQExpression expr = conn.createExpression();

        expr.bindInt(new QName("x"), 21, null);

        XQSequence result = expr.executeQuery(
           "declare variable $x as xs:integer external;
           for $i in $x return $i");

        while (result.next())
        {
           // process results ...
        }

        // Execute some other expression on the same object
        XQSequence result = expr.executeQuery("for $i in doc('foo.xml') return $i");
        ...

        result.close(); // close the result
        expr.close();
        conn.close();


<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                         |
    |-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                    | `cancel``()`<br>Attempts to cancel the execution if both the XQuery engine and XQJ driver support aborting the execution of an `XQExpression`. |
    | `void`                                    | `close``()`<br>Closes the expression object and release associated resources.                                                                  |
    | `void`                                    | `executeCommand``(java.io.Reader cmd)`<br>Executes an implementation-defined command.                                                          |
    | `void`                                    | `executeCommand``(java.lang.String cmd)`<br>Executes an implementation-defined command.                                                        |
    | [`XQResultSequence`](XQResultSequence.md) | `executeQuery``(java.io.InputStream query)`<br>Executes a query expression.                                                                    |
    | [`XQResultSequence`](XQResultSequence.md) | `executeQuery``(java.io.Reader query)`<br>Executes a query expression.                                                                         |
    | [`XQResultSequence`](XQResultSequence.md) | `executeQuery``(java.lang.String query)`<br>Executes a query expression.                                                                       |
    | [`XQStaticContext`](XQStaticContext.md)   | `getStaticContext``()`<br>Gets an `XQStaticContext` representing the values for all expression properties.                                     |
    | `boolean`                                 | `isClosed``()`<br>Checks if the expression is in a closed state.                                                                               |

    - ### Methods inherited from interface javax.xml.xquery.[XQDynamicContext](XQDynamicContext.md)

      [`bindAtomicValue`](XQDynamicContext.md)`, `[`bindBoolean`](XQDynamicContext.md)`, `[`bindByte`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDouble`](XQDynamicContext.md)`, `[`bindFloat`](XQDynamicContext.md)`, `[`bindInt`](XQDynamicContext.md)`, `[`bindItem`](XQDynamicContext.md)`, `[`bindLong`](XQDynamicContext.md)`, `[`bindNode`](XQDynamicContext.md)`, `[`bindObject`](XQDynamicContext.md)`, `[`bindSequence`](XQDynamicContext.md)`, `[`bindShort`](XQDynamicContext.md)`, `[`bindString`](XQDynamicContext.md)`, `[`getImplicitTimeZone`](XQDynamicContext.md)`, `[`setImplicitTimeZone`](XQDynamicContext.md)

<!-- -->

- - ### Method Detail

    - #### cancel

          void cancel()
               throws XQException

      Attempts to cancel the execution if both the XQuery engine and XQJ driver support aborting the execution of an `XQExpression`. This method can be used by one thread to cancel an `XQExpression`, that is being executed in another thread. If cancellation is not supported or the attempt to cancel the execution was not successful, the method returns without any error. If the cancellation is successful, an `XQException` is thrown, to indicate that it has been aborted, by `executeQuery`, `executeCommand` or any method accessing the `XQResultSequence` returned by `executeQuery`. If applicable, any open `XQResultSequence` and `XQResultItem` objects will also be implicitly closed in this case.
      Throws:
      [`XQException`](XQException.md) - if the expression is in a closed state

    <!-- -->

    - #### isClosed

          boolean isClosed()

      Checks if the expression is in a closed state.
      Returns:
      `true` if the expression is in a closed state, `false` otherwise

    <!-- -->

    - #### close

          void close()
              throws XQException

      Closes the expression object and release associated resources. Once the expression is closed, all methods on this object other than the `close` or `isClosed` will raise exceptions. This also closes any result sequences obtained from this expression. Calling `close` on an `XQExpression` object that is already closed has no effect.
      Throws:
      [`XQException`](XQException.md) - if there are errors when closing the expression

    <!-- -->

    - #### executeCommand

          void executeCommand(java.lang.String cmd)
                       throws XQException

      Executes an implementation-defined command. Calling this method implicitly closes any previous result sequence obtained from this expression.
      Parameters:
      `cmd` - the input command as a string

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors when executing the command, or (2) the expression is in a closed state

    <!-- -->

    - #### executeCommand

          void executeCommand(java.io.Reader cmd)
                       throws XQException

      Executes an implementation-defined command. Calling this method implicitly closes any previous result sequence obtained from this expression.
      Parameters:
      `cmd` - the input command as a string reader

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors when executing the command, (2) the expression is in a closed state, or (3) the execution is cancelled

    <!-- -->

    - #### executeQuery

          XQResultSequence executeQuery(java.lang.String query)
                                 throws XQException

      Executes a query expression. This implicitly closes any previous result sequences obtained from this expression.
      Parameters:
      `query` - the input query expression string. Cannot be `null`

      Returns:
      an `XQResultSequence` object containing the result of the query execution

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors when executing the query, (2) the expression is in a closed state, (3) the execution is cancelled, (4) the query parameter is `null`

    <!-- -->

    - #### executeQuery

          XQResultSequence executeQuery(java.io.Reader query)
                                 throws XQException

      Executes a query expression. This implicitly closes any previous result sequences obtained from this expression.
      Parameters:
      `query` - the input query expression as a reader object. Cannot be `null`

      Returns:
      an `XQResultSequence` object containing the result of the query execution

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors when executing the query, (2) the expression is in a closed state, (3) the execution is cancelled, or (4) the query parameter is `null`

    <!-- -->

    - #### executeQuery

          XQResultSequence executeQuery(java.io.InputStream query)
                                 throws XQException

      Executes a query expression. This implicitly closes any previous result sequences obtained from this expression. If the query specifies a version declaration including an encoding, the XQJ implementation may try use this information to parse the query. In absence of the version declaration, the assumed encoding is implementation dependent.
      Parameters:
      `query` - the input query expression as a input stream object. Cannot be `null`

      Returns:
      an `XQResultSequence` containing the result of the query execution

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors when executing the query, (2) the expression is in a closed state, (3) the execution is cancelled, or (4) the xquery parameter is `null`

    <!-- -->

    - #### getStaticContext

          XQStaticContext getStaticContext()
                                    throws XQException

      Gets an `XQStaticContext` representing the values for all expression properties. Note that these properties cannot be changed; in order to change, a new `XQExpression` needs to be created.
      Returns:
      an `XQStaticContext` representing the values for all expression properties

      Throws:
      [`XQException`](XQException.md) - if the expression is in a closed state

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

- **[Prev Class](XQException.md)**
- **[Next Class](XQItem.md)**

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
