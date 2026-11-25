Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAHeteroCloseCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSource.md)
- [Next Class](OracleXAHeteroConnection.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.jdbc.xa.client

## Class OracleXAHeteroCloseCallback

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.xa.client.OracleXAHeteroCloseCallback

<!-- -->

- All Implemented Interfaces:
  oracle.jdbc.driver.OracleCloseCallback

  ------------------------------------------------------------------------



      public class OracleXAHeteroCloseCallback
      extends Object
      implements oracle.jdbc.driver.OracleCloseCallback

  This class implements the OracleCloseCallback interface that is defined in oracle.jdbc.driver. It is used to close a physical connection to an RM instance, and unregister this RM instance from C-XA's current thread of control. An instance of this class should be registered with an OracleXAConnection/OraclePooledConnection, using the registerCloseCallback() method in the OraclePooledConnection class to function, like: ((OracleXAConnection) xaconn).registerCloseCallback( new OracleXAHeteroCloseCallback(), new SomeUserObject());

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description        |
    |------------------------------------|
    | `OracleXAHeteroCloseCallback``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                            | `afterClose``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` privData)`                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                            | `beforeClose``(oracle.jdbc.internal.OracleConnection conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`                                                                                                                                                                                                                                                                                                           |
    | `protected void`                                  | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`  |
    | `protected oracle.jdbc.internal.OracleConnection` | `getConnectionDuringExceptionHandling``()`                                                                                                                                                                                                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleXAHeteroCloseCallback

          public OracleXAHeteroCloseCallback()

  <!-- -->

  - ### Method Detail

    - #### beforeClose

          public void beforeClose(oracle.jdbc.internal.OracleConnection conn,
                                  Object obj)

      Specified by:
      `beforeClose` in interface `oracle.jdbc.driver.OracleCloseCallback`

    <!-- -->

    - #### afterClose

          public void afterClose(Object privData)

      Specified by:
      `afterClose` in interface `oracle.jdbc.driver.OracleCloseCallback`

    <!-- -->

    - #### getConnectionDuringExceptionHandling

          protected oracle.jdbc.internal.OracleConnection getConnectionDuringExceptionHandling()

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAHeteroCloseCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSource.md)
- [Next Class](OracleXAHeteroConnection.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
