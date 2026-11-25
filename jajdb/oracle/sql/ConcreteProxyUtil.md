Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConcreteProxyUtil.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CLOB.md)
- [Next Class](ConverterArchive.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.sql

## Class ConcreteProxyUtil

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.ConcreteProxyUtil

<!-- -->

-

  ------------------------------------------------------------------------



      public class ConcreteProxyUtil
      extends Object

  This class has helper methods for all concrete class needs proxification.
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ConcreteProxyUtil``()`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                                                                                                                                               |
    |----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `checkAndGetACProxyConnection``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn)`<br>Check whether connection object from proxified or not.                                                                                                                                                                 |
    | `static <T> T`                                                                                           | `getProxyObject``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn, T delegate, `[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` proxyBaseClass, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` creator)`  |
    | `static `[`OracleConnection`](../jdbc/OracleConnection.md)                                               | `getThinDriverReplayableConnectionDelegate``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn)`                                                                                                                                                                                                              |
    | `static oracle.jdbc.replay.driver.TxnReplayableBase`                                                     | `getTxnReplayableBaseOfConnection``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn)`                                                                                                                                                                                                                       |
    | `static boolean`                                                                                         | `isThinDriverConnection``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` conn)`<br>Check for connection is from Thin driver or not.                                                                                                                               |
    | `static boolean`                                                                                         | `isThinDriverReplayableConnection``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn)`                                                                                                                                                                                                                       |
    | `static `[`OracleConnection`](../jdbc/OracleConnection.md)                                               | `unwrapConnectionProxy``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn)`                                                                                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### ConcreteProxyUtil

          public ConcreteProxyUtil()

  <!-- -->

  - ### Method Detail

    - #### isThinDriverConnection

          public static boolean isThinDriverConnection(Object conn)

      Check for connection is from Thin driver or not.
      Parameters:
      `conn` -

      Returns:
      true if Thin connection false otherwise.

    <!-- -->

    - #### getTxnReplayableBaseOfConnection

          public static oracle.jdbc.replay.driver.TxnReplayableBase getTxnReplayableBaseOfConnection(OracleConnection conn)

    <!-- -->

    - #### isThinDriverReplayableConnection

          public static boolean isThinDriverReplayableConnection(OracleConnection conn)

    <!-- -->

    - #### getThinDriverReplayableConnectionDelegate

          public static OracleConnection getThinDriverReplayableConnectionDelegate(OracleConnection conn)

    <!-- -->

    - #### checkAndGetACProxyConnection

          public static Object checkAndGetACProxyConnection(OracleConnection conn)

      Check whether connection object from proxified or not.
      Parameters:
      `conn` -

      Returns:
      Proxified connection object

    <!-- -->

    - #### getProxyObject

          public static <T> T getProxyObject(OracleConnection conn,
                                             T delegate,
                                             Class proxyBaseClass,
                                             Object creator)

    <!-- -->

    - #### unwrapConnectionProxy

          public static OracleConnection unwrapConnectionProxy(OracleConnection conn)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConcreteProxyUtil.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CLOB.md)
- [Next Class](ConverterArchive.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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
