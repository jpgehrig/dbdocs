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

- **[Prev Class](XQMetaData.md)**
- **[Next Class](XQQueryException.md)**

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

## **Interface XQPreparedExpression**

- **All Superinterfaces:**
  **[XQDynamicContext](XQDynamicContext.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQPreparedExpression
      extends XQDynamicContext

  **This interface describes an expression that can be prepared for multiple subsequent executions. A prepared expression can be created from the connection.**
  **The preparation of the expression does the static analysis of the expression using the static context information.**

  **The dynamic context information, such as values for bind variables, can then be set using the setter methods. When setting values for bind variables, these variables should be present as external variables in the prolog of the prepared expression.**

  **The static type information of the query can also be retrieved if the XQuery implementation provides it using the `getStaticResultType` method.**

  **When the expression is executed using the `executeQuery` method, if the execution is successful, then an `XQResultSequence` object is returned. The `XQResultSequence` object is tied to the `XQPreparedExpression` from which it was prepared and is closed implicitly if that expression is either closed or if re-executed.**

  **The `XQPreparedExpression` object is dependent on the `XQConnection` object from which it was created and is only valid for the duration of that object. Thus, if the `XQConnection` object is closed then this `XQPreparedExpression` object will be implicitly closed and it can no longer be used.**

  **An XQJ driver is not required to provide finalizer methods for the connection and other objects. Hence it is strongly recommended that users call close method explicitly to free any resources. It is also recommended that they do so under a final block to ensure that the object is closed even when there are exceptions. Not closing this object implicitly or explicitly might result in serious memory leaks.**

  **When the `XQPreparedExpression` is closed any `XQResultSequence` object obtained from it is also implicitly closed.**

  **Example -**

        XQConnection conn = XQDataSource.getconnection();
        XQPreparedExpression expr = conn.prepareExpression
                ("for $i in (1) return 'abc' ");

        // get the sequence type out.. This would be something like xs:string *
        XQSequenceType type = expr.getStaticResultType();

        XQSequence result1 = expr.executeQuery();

        // process the result..
        result1.next();
        System.out.println(" First result1 "+ result1.getAtomicValue());

        XQResultSequence result2 = expr.executeQuery();

        // result1 is implicitly closed
        // recommended to close the result sequences explicitly.

        // process the result..
        while (result2.next())
           System.out.println(" result is "+ result2.getAtomicValue());

        result2.close();
        expr.close(); // closing expression implicitly closes all result sequence or
                      // items obtained from this expression.
        conn.close(); // closing connections will close expressions and results.


<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                                 |
    |-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                    | `cancel``()`<br>Attempts to cancel the execution if both the XQuery engine and XQJ driver support aborting the execution of an `XQPreparedExpression`. |
    | `void`                                    | `close``()`<br>Closes the expression object and release all resources associated with this prepared expression.                                        |
    | [`XQResultSequence`](XQResultSequence.md) | `executeQuery``()`<br>Executes the prepared query expression.                                                                                          |
    | `javax.xml.namespace.QName[]`             | `getAllExternalVariables``()`<br>Retrieves all the external variables defined in the prolog of the prepared expression.                                |
    | `javax.xml.namespace.QName[]`             | `getAllUnboundExternalVariables``()`<br>Retrieves the names of all unbound external variables.                                                         |
    | [`XQStaticContext`](XQStaticContext.md)   | `getStaticContext``()`<br>Gets an `XQStaticContext` representing the values for all expression properties.                                             |
    | [`XQSequenceType`](XQSequenceType.md)     | `getStaticResultType``()`<br>Gets the static type information of the result sequence.                                                                  |
    | [`XQSequenceType`](XQSequenceType.md)     | `getStaticVariableType``(javax.xml.namespace.QName name)`<br>Retrieves the static type of a given external variable.                                   |
    | `boolean`                                 | `isClosed``()`<br>Checks if the prepared expression in a closed state.                                                                                 |

    - ### Methods inherited from interface javax.xml.xquery.[XQDynamicContext](XQDynamicContext.md)

      [`bindAtomicValue`](XQDynamicContext.md)`, `[`bindBoolean`](XQDynamicContext.md)`, `[`bindByte`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDocument`](XQDynamicContext.md)`, `[`bindDouble`](XQDynamicContext.md)`, `[`bindFloat`](XQDynamicContext.md)`, `[`bindInt`](XQDynamicContext.md)`, `[`bindItem`](XQDynamicContext.md)`, `[`bindLong`](XQDynamicContext.md)`, `[`bindNode`](XQDynamicContext.md)`, `[`bindObject`](XQDynamicContext.md)`, `[`bindSequence`](XQDynamicContext.md)`, `[`bindShort`](XQDynamicContext.md)`, `[`bindString`](XQDynamicContext.md)`, `[`getImplicitTimeZone`](XQDynamicContext.md)`, `[`setImplicitTimeZone`](XQDynamicContext.md)

<!-- -->

- - ### Method Detail

    - #### cancel

          void cancel()
               throws XQException

      Attempts to cancel the execution if both the XQuery engine and XQJ driver support aborting the execution of an `XQPreparedExpression`. This method can be used by one thread to cancel an `XQPreparedExpression`, that is being executed in another thread. If cancellation is not supported or the attempt to cancel the execution was not successful, the method returns without any error. If the cancellation is successful, an `XQException` is thrown, to indicate that it has been aborted, by `executeQuery`, `executeCommand` or any method accessing the `XQResultSequence` returned by `executeQuery`. If applicable, any open `XQResultSequence` and `XQResultItem` objects will also be implicitly closed in this case.
      Throws:
      [`XQException`](XQException.md) - if the prepared expression is in a closed state

    <!-- -->

    - #### isClosed

          boolean isClosed()

      Checks if the prepared expression in a closed state.
      Returns:
      `true` if the prepared expression is in a closed state, `false` otherwise.

    <!-- -->

    - #### close

          void close()
              throws XQException

      Closes the expression object and release all resources associated with this prepared expression. This also closes any result sequences obtained from this expression. Once the expression is closed, all methods on this object other than the `close` or `isClosed` will raise exceptions. Calling close on an `XQExpression` object that is already closed has no effect.
      Throws:
      [`XQException`](XQException.md) - if there are errors when closing the expression

    <!-- -->

    - #### executeQuery

          XQResultSequence executeQuery()
                                 throws XQException

      Executes the prepared query expression. Calling this method implicitly closes any previous result sequence obtained from this expression.
      Returns:
      the xquery sequence object containing the result of the query execution

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors when executing the prepared expression, (2) the prepared expression is in a closed state, or (3) the query execution is cancelled

    <!-- -->

    - #### getAllExternalVariables

          javax.xml.namespace.QName[] getAllExternalVariables()
                                                       throws XQException

      Retrieves all the external variables defined in the prolog of the prepared expression.
      Returns:
      an array of `QName` objects for all the external variables defined in the prolog of a prepared expression. Empty array if there are no external variables present.

      Throws:
      [`XQException`](XQException.md) - if the prepared expression is in a closed state

    <!-- -->

    - #### getAllUnboundExternalVariables

          javax.xml.namespace.QName[] getAllUnboundExternalVariables()
                                                              throws XQException

      Retrieves the names of all unbound external variables.
      Returns:
      the `QName` for all the external variables defined in the prolog of a prepared expression that are yet to be bound with a value. If there are no such variables an empty array is returned

      Throws:
      [`XQException`](XQException.md) - if the prepared expression is in a closed state

    <!-- -->

    - #### getStaticResultType

          XQSequenceType getStaticResultType()
                                      throws XQException

      Gets the static type information of the result sequence. If an implementation does not do static typing of the query, then this method must return an `XQSequenceType` object corresponding to the XQuery sequence type `item()*`.
      Returns:
      `XQSequenceType` containing the static result information.

      Throws:
      [`XQException`](XQException.md) - if the prepared expression is in a closed state

    <!-- -->

    - #### getStaticVariableType

          XQSequenceType getStaticVariableType(javax.xml.namespace.QName name)
                                        throws XQException

      Retrieves the static type of a given external variable.
      Parameters:
      `name` - the name of the external variable

      Returns:
      the static type information of the variable as defined in the prolog of the prepared expression

      Throws:
      [`XQException`](XQException.md) - if (1) the variable does not exist in the static context of the expression, or (2) the sequence is in a closed state, or (3) the `name` parameter is `null`

    <!-- -->

    - #### getStaticContext

          XQStaticContext getStaticContext()
                                    throws XQException

      Gets an `XQStaticContext` representing the values for all expression properties. Note that these properties cannot be changed; in order to change, a new `XQPreparedExpression` needs to be created.
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

- **[Prev Class](XQMetaData.md)**
- **[Next Class](XQQueryException.md)**

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
