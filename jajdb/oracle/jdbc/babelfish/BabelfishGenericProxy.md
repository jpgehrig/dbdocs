Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishGenericProxy.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishConnection.md)
- [Next Class](BabelfishPreparedStatement.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc.babelfish

## Class BabelfishGenericProxy

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.babelfish.BabelfishGenericProxy

<!-- -->

- Direct Known Subclasses:
  [BabelfishConnection](BabelfishConnection.md), [BabelfishStatement](BabelfishStatement.md)

  ------------------------------------------------------------------------



      public abstract class BabelfishGenericProxy
      extends Object

  Defines the common behavior needed by all the babelfish proxies to support auto translation of queries or errors. All the proxies are children of this class and thus get the common behavior via inheritance.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `BabelfishGenericProxy``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                 |
    |----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getCreator``()`                                                                                                                                                                                                                                                       |
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getDelegate``()`                                                                                                                                                                                                                                                      |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `post_Methods``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` result)`<br>Post method interceptor.    |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `translateError``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` ex)`<br>Error interceptor. |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### BabelfishGenericProxy

          public BabelfishGenericProxy()

  <!-- -->

  - ### Method Detail

    - #### getCreator

          protected abstract Object getCreator()

      Returns:

    <!-- -->

    - #### getDelegate

          protected abstract Object getDelegate()

      Returns:

    <!-- -->

    - #### translateError

          protected Object translateError(Method m,
                                          SQLException ex)
                                   throws SQLException

      Error interceptor. Handles the translation of error.
      Parameters:
      `m` -

      `ex` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### post_Methods

          protected Object post_Methods(Method m,
                                        Object result)

      Post method interceptor. Sets the translator in the returning object if the returning object is a child of BabelfishGenericProxy
      Parameters:

      `m` -

      `result` -

      Returns:

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishGenericProxy.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishConnection.md)
- [Next Class](BabelfishPreparedStatement.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
