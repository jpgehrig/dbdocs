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

- **[Prev Class](OXQAnnotation.md)**
- **[Next Class](OXQCompositeResolverFactory.md)**

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

## **Interface OXQCloseable**

- **All Known Subinterfaces:**
  **[OXQSequence](OXQSequence.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[OXQEntity](OXQEntity.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQCloseable

  **Extension methods for closeable objects.**
  **The XQJ user is responsible for explicitly calling `close()` on streaming resources bound to external variables and on sequences that are returned as a streaming resource. This is inconvenient in a streaming execution pipeline scenario where it may be difficult to keep track of what needs to be closed at each step in the pipeline. For example, suppose we need to bind an instance of `XMLStreamReader` to an expression, execute this expression and obtain the result sequence, and then return the result sequence as an instance of `XMLStreamReader`. In order to properly close all resources after we are done processing the output, we have to explicitly invoke `close()` on the output `XMLStreamReader` instance, the result sequence, and the input `XMLStreamReader` instance. If the pipeline is long and the objects are passed around between multiple methods, the user may not have access to all the resources that must be closed at the end of the pipeline. The `enlistCloseable` methods provide a way to declare that when a resource is closed, one or more other resources should be closed as well. Thus the closing of streaming resources is declaratively specified as they are used, with the user only having to explicitly call `close()` on the final streaming resource at the end of the pipeline.**

  The precise semantics are as follows: during this object's `close()` invocation, `close()` will be invoked for all `closeable` objects that were registered using the `enlistCloseable()` methods in the order they were registered.

  Example:

       XQConnection conn = ...;
       XQPreparedExpression xqExpression1 = conn.prepareExpression("(1, 2, 3)");
       XQSequence xqSequence1 = xqExpression1.executeQuery();
       XQPreparedExpression xqExpression2 = conn.prepareExpression("declare variable $x9 as item()* external;
                                            declare variable $x10 as item() external; ($x9, $x10)");
       //Bind XQSequnce
       xqExpression2.bindSequence(new QName("x9"), xqSequence1);

       //Bind an InputStream
       String data = "<num>33</num>";
       InputStream inputStream = new ByteArrayInputStream(data.getBytes());
       xqExpression2.bindDocument(new QName("x10"), inputStream, null, null);

       //Get the result sequence
       XQSequence xqFinalSequence = xqExpression2.executeQuery();

       XMLStreamReader strmReader = xqFinalSequence.getSequenceAsStream();

       //Declare that input sequence should be closed when the final sequence is closed
       OXQView.getCloseable(xqFinalSequence).enlistCloseable(xqSequence1);

       //Declare that the input stream should be closed when the final sequence is closed
       OXQView.getCloseable(xqFinalSequence).enlistCloseable(inputStream);

       //Declare that the final sequence should be closed when the stream reader is closed
       OXQView.getCloseable(strmReader).enlistCloseable(xqFinalSequence);

       while (strmReader.hasNext()) {
         ...
       }

       //This will close the stream reader and all of the dependent resources, ie
       //the final sequence, the input sequence, and the input stream.
       strmReader.close()


  If exceptions occur during invocation of `close()` on any of the `closeable` objects, a single exception will be thrown by this object's `close()`. The first of the exceptions thrown by the `closeable` objects will be the cause of that exception.

  Thread-safety semantics of registered resources
  The XQuery processor assumes that each registered resource, while not necessarily generally thread-safe, has a thread-safe implementation of the "close" method that can be invoked in parallel with any "read" method, in order to stop reading activity and close gracefully. Many of the JDK implementations of `java.io.Closeable` satisfy this requirement. The Oracle implementation of [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) satisfies this requirement as well, in the case where it, in turn, relies only on resources that are thread-safe with respect to closing. Registration of resources not following this assumption might result in unpredictable behavior in a multi-threaded environment.

  Since:
  12.1

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                      |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `enlistCloseable``(java.io.Closeable closeable)`<br>Declares a `closeable` object that will be closed when this object is closed.                                           |
    | `void`            | `enlistCloseable``(javax.xml.stream.XMLStreamReader closeable)`<br>Declares an `XMLStreamReader` object that will be closed when this object is closed.                     |
    | `void`            | `enlistCloseable``(`[`XQSequence`](../../../javax/xml/xquery/XQSequence.md)` closeable)`<br>Declares an `XQSequence` object that will be closed when this object is closed. |

<!-- -->

- - ### Method Detail

    - #### enlistCloseable

          void enlistCloseable(XQSequence closeable)
                        throws XQException

      Declares an `XQSequence` object that will be closed when this object is closed.
      Parameters:
      `closeable` - object that `close()` must be invoked on after `close()` is invoked on this object.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) `closeable` is `null`, (2) this object is in a closed state, or (3) provided closeable object is not supported for this main object.

      See Also:
      `Detailed description`

    <!-- -->

    - #### enlistCloseable

          void enlistCloseable(java.io.Closeable closeable)
                        throws XQException

      Declares a `closeable` object that will be closed when this object is closed.
      Parameters:
      `closeable` - input streaming object that `close()` must be invoked on after `close()` is invoked on this object.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) `closeable` is `null`, (2) this object is in a closed state, or (3) provided closeable object is not supported for this main object.

      See Also:
      `Detailed description`

    <!-- -->

    - #### enlistCloseable

          void enlistCloseable(javax.xml.stream.XMLStreamReader closeable)
                        throws XQException

      Declares an `XMLStreamReader` object that will be closed when this object is closed.
      Note: `XMLStreamReader` implementations don't usually conform to the thread-safety semantics defined above, so their use as resources is not recommended in multi-threaded environments.

      Parameters:
      `closeable` - object that `close()` must be invoked on after `close()` is invoked on this object.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) `closeable` is `null`, (2) this object is in a closed state, or (3) provided closeable object is not supported for this main object.

      See Also:
      `Detailed description`

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

- **[Prev Class](OXQAnnotation.md)**
- **[Next Class](OXQCompositeResolverFactory.md)**

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
