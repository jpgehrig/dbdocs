Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../xmldbaccess/package-summary.md)**
- **[Next Package](xqjdb/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package oracle.xml.xquery**

**Contains extensions to the *XQuery API for Java* (JSR 225) and [`OXQDataSource`](OXQDataSource.md), the Oracle implementation of [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md).**

**See: Description**

- **Interface Summary**

  | Interface                                                     | Description                                                                                                                                                   |
  |---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OXQAnnotation](OXQAnnotation.md)                             | Models an [XQuery function annotation](http://www.w3.org/TR/xquery-30/#id_annotations).                                                                       |
  | [OXQCloseable](OXQCloseable.md)                               | Extension methods for closeable objects.                                                                                                                      |
  | [OXQCompositeResolverFactory](OXQCompositeResolverFactory.md) | The factory interface for creating composite entity resolvers.                                                                                                |
  | [OXQConnection](OXQConnection.md)                             | Extensions to [`javax.xml.xquery.XQConnection`](../../../javax/xml/xquery/XQConnection.md).                                                                   |
  | [OXQDataFactory](OXQDataFactory.md)                           | Extensions to [`javax.xml.xquery.XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md).                                                                 |
  | [OXQDecimalFormat](OXQDecimalFormat.md)                       | The implementation of this interface should store the decimal format properties that fn:format-number will use to format a number.                            |
  | [OXQDynamicContext](OXQDynamicContext.md)                     | Extensions to [`javax.xml.xquery.XQDynamicContext`](../../../javax/xml/xquery/XQDynamicContext.md).                                                           |
  | [OXQEntityLoader](OXQEntityLoader.md)                         | Manages the lifecycle of schemas and modules in the static context.                                                                                           |
  | [OXQEntityResolverFactory](OXQEntityResolverFactory.md)       | A factory for creating instances of [`OXQEntityResolver`](OXQEntityResolver.md).                                                                              |
  | [OXQExpression](OXQExpression.md)                             | Extensions to [`javax.xml.xquery.XQExpression`](../../../javax/xml/xquery/XQExpression.md).                                                                   |
  | [OXQFileResolverFactory](OXQFileResolverFactory.md)           | The factory interface that creates resolvers for Java's 'file:' URIs.                                                                                         |
  | [OXQFunctionContext](OXQFunctionContext.md)                   | The runtime context provided to extensions of [`OXQFunctionEvaluator`](OXQFunctionEvaluator.md).                                                              |
  | [OXQFunctionMetaData](OXQFunctionMetaData.md)                 | Function metadata used when [`resolving`](OXQEntityResolver.md) an external function.                                                                         |
  | [OXQHttpResolverFactory](OXQHttpResolverFactory.md)           | The factory interface for creating entity resolvers for the HTTP protocol.                                                                                    |
  | [OXQItem](OXQItem.md)                                         | Extensions to [`javax.xml.xquery.XQItem`](../../../javax/xml/xquery/XQItem.md).                                                                               |
  | [OXQItemAccessor](OXQItemAccessor.md)                         | Extensions to [`javax.xml.xquery.XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md).                                                               |
  | [OXQJavaResolverFactory](OXQJavaResolverFactory.md)           | The factory interface for creating entity resolvers for external functions implemented in Java.                                                               |
  | [OXQOptions](OXQOptions.md)                                   | Exposes the contents of zero or more [XQuery option declarations](http://www.w3.org/TR/xquery/#id_option_declaration).                                        |
  | [OXQPreparedExpression](OXQPreparedExpression.md)             | Extensions to [`javax.xml.xquery.XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md).                                                   |
  | [OXQSequence](OXQSequence.md)                                 | Extensions to [`javax.xml.xquery.XQSequence`](../../../javax/xml/xquery/XQSequence.md).                                                                       |
  | [OXQSerializationParameters](OXQSerializationParameters.md)   | Models the supported [serialization parameters](http://www.w3.org/TR/xslt-xquery-serialization-30/#serparam).                                                 |
  | [OXQStackTraceElement](OXQStackTraceElement.md)               | Provides contextual information about query processing to an XQuery debugger client.                                                                          |
  | [OXQStackTraceVariable](OXQStackTraceVariable.md)             | Provides information about a variable binding in addition to what is provided by [`XQStackTraceVariable`](../../../javax/xml/xquery/XQStackTraceVariable.md). |
  | [OXQStaticContext](OXQStaticContext.md)                       | Extensions to [`javax.xml.xquery.XQStaticContext`](../../../javax/xml/xquery/XQStaticContext.md).                                                             |
  | [OXQView.OXQViewAccessor](OXQView.OXQViewAccessor.md)         | Generic interface implemented by all XQJ objects which are capable of providing an OXQJ view.                                                                 |

- **Class Summary**

  | Class                                                                 | Description                                                                                                                              |
  |-----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
  | [OXQConstants](OXQConstants.md)                                       | Constant values.                                                                                                                         |
  | [OXQDataSource](OXQDataSource.md)                                     | Implements [`javax.xml.xquery.XQDataSource`](../../../javax/xml/xquery/XQDataSource.md).                                                 |
  | [OXQDebugListener](OXQDebugListener.md)                               | An event listener for implementing an XQuery debugger client.                                                                            |
  | [OXQEntity](OXQEntity.md)                                             | The entity returned by an [`OXQEntityResolver`](OXQEntityResolver.md).                                                                   |
  | [OXQEntityLocator](OXQEntityLocator.md)                               | The location of an entity to be [`resolved`](OXQEntityResolver.md).                                                                      |
  | [OXQEntityResolver](OXQEntityResolver.md)                             | Used by the XQuery processor to obtain different kinds of resource entities.                                                             |
  | [OXQEntityResolverRequestOptions](OXQEntityResolverRequestOptions.md) | Additional options for use when [`resolving an entity`](OXQEntityResolver.md).                                                           |
  | [OXQFunctionEvaluator](OXQFunctionEvaluator.md)                       | Extensions of this can be used to implement XQuery external functions.                                                                   |
  | [OXQView](OXQView.md)                                                 | This class provides methods to access Oracle's XQJ extensions (OXQJ) and extensions to other classes returned by the XQJ implementation. |

- **Enum Summary**

  | Enum                              | Description                                                  |
  |-----------------------------------|--------------------------------------------------------------|
  | [OXQEntityKind](OXQEntityKind.md) | The kind of entity to be [`resolved`](OXQEntityResolver.md). |

## **Package oracle.xml.xquery Description**

**Contains extensions to the *XQuery API for Java* (JSR 225) and [`OXQDataSource`](OXQDataSource.md), the Oracle implementation of [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md).**

**This is the documentation for Oracle's standalone [XQuery 1.0](http://www.w3.org/TR/xquery/) processor. It is implemented purely in Java and runs in the same JVM as the application. This processor supports the *XQuery API for Java* (XQJ) as well as some non-standard extensions. Specifically, this package contains:**

- **[`OXQDataSource`](OXQDataSource.md), an implementation of [`XQDataSource`](../../../javax/xml/xquery/XQDataSource.md), which is usually the starting point for XQJ users.**
- **Extensions to some of the standard XQJ interfaces in package `javax.xml.xquery` (for example, [`OXQStaticContext`](OXQStaticContext.md)).**
- **An [`entity resolver`](OXQEntityResolver.md) framework which allows users to control how external entities are obtained by the query processor. This includes but is not limited to modules, schemas, collections, collations, documents, XML entities, and external functions.**
- **A [`resource closing framework`](OXQCloseable.md) which allows users to control how external resources are associated with XQJ objects and closed together with those XQJ objects.**

### **Thread-safety**

**The Oracle implementation of XQJ is not thread-safe. For example, an instance of [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) must be accessed by only one thread. However, a restricted form of thread safety is supported for managing instances of [`XQConnection`](../../../javax/xml/xquery/XQConnection.md).**

- **An instance of [`XQConnection`](../../../javax/xml/xquery/XQConnection.md) serves as a factory for creating instances of [`XQExpression`](../../../javax/xml/xquery/XQExpression.md), [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md), [`XQItem`](../../../javax/xml/xquery/XQItem.md), [`XQSequence`](../../../javax/xml/xquery/XQSequence.md), [`XQItemType`](../../../javax/xml/xquery/XQItemType.md), and [`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md). One thread can manage the creation of these objects for use by other threads. For example, [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) instances created in one thread by the same connection can be used in other threads. Each [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) instance, however, must be executed by only one thread. Any user-defined implementations of [`OXQEntityResolver`](OXQEntityResolver.md) that are specified must be thread-safe when expressions from the same connection are evaluated concurrently.**
- **The [`XQConnection.close()`](../../../javax/xml/xquery/XQConnection.md) method closes all [`XQExpression`](../../../javax/xml/xquery/XQExpression.md) and [`XQPreparedExpression`](../../../javax/xml/xquery/XQPreparedExpression.md) instances that were obtained from the connection. Closing those instances closes all [`XQResultSequence`](../../../javax/xml/xquery/XQResultSequence.md) and [`XQResultItem`](../../../javax/xml/xquery/XQResultItem.md) instances obtained from the expressions. The [`XQConnection.close()`](../../../javax/xml/xquery/XQConnection.md) method can be called while expressions obtained from the connection are being processed in other threads. In this case, all registered resources held by the expressions (such as `java.io.InputStream` and `java.io.Reader`) are closed. This contract assumes that all registered resources support a thread-safe close method. For example, many JDK implementations of `java.io.Closeable` satisfy this requirement. But, many implementations of `javax.xml.stream.XMLStreamReader` do not provide a thread-safe close method. Implementations without this support can give unpredictable results if they are closed while a second thread is still reading. See [`OXQCloseable`](OXQCloseable.md) for more information.**

**Since:**
**12.1**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../xmldbaccess/package-summary.md)**
- **[Next Package](xqjdb/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
