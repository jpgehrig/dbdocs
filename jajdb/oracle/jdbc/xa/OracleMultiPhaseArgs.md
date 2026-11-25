Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleMultiPhaseArgs.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](OracleXAConnection.md)

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

oracle.jdbc.xa

## Class OracleMultiPhaseArgs

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.xa.OracleMultiPhaseArgs

<!-- -->

-

  ------------------------------------------------------------------------



      public class OracleMultiPhaseArgs
      extends Object

  Utility class.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static boolean`  | `TRACE`               |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleMultiPhaseArgs``()`                                                                                                                                                                                                                                               |
    | `OracleMultiPhaseArgs``(byte[] inBytes)`                                                                                                                                                                                                                                 |
    | `OracleMultiPhaseArgs``(int _action, int _nsites, `[`Vector`](http://download.oracle.com/javase/8/docs/api/java/util/Vector.html?is-external=true)` _xids, `[`Vector`](http://download.oracle.com/javase/8/docs/api/java/util/Vector.html?is-external=true)` _dbLinks)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                           | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |-----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected void`                                                                                                            | `debug``(`[`Logger`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Logger.html?is-external=true)` logger, `[`Level`](http://download.oracle.com/javase/8/docs/api/java/util/logging/Level.html?is-external=true)` level, `[`Executable`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Executable.html?is-external=true)` method, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` msg)`  |
    | `int`                                                                                                                       | `getAction``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`Vector`](http://download.oracle.com/javase/8/docs/api/java/util/Vector.html?is-external=true)                             | `getdbLinks``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `int`                                                                                                                       | `getnsite``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`Vector`](http://download.oracle.com/javase/8/docs/api/java/util/Vector.html?is-external=true)                             | `getXids``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                                      | `printMPArgs``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `byte[]`                                                                                                                    | `toByteArray``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`ByteArrayOutputStream`](http://download.oracle.com/javase/8/docs/api/java/io/ByteArrayOutputStream.html?is-external=true) | `toByteArrayOS``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### TRACE

          public static final boolean TRACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OracleMultiPhaseArgs

          public OracleMultiPhaseArgs()

    <!-- -->

    - #### OracleMultiPhaseArgs

          public OracleMultiPhaseArgs(int _action,
                                      int _nsites,
                                      Vector _xids,
                                      Vector _dbLinks)

    <!-- -->

    - #### OracleMultiPhaseArgs

          public OracleMultiPhaseArgs(byte[] inBytes)

  <!-- -->

  - ### Method Detail

    - #### toByteArray

          public byte[] toByteArray()

    <!-- -->

    - #### toByteArrayOS

          public ByteArrayOutputStream toByteArrayOS()

    <!-- -->

    - #### getAction

          public int getAction()

    <!-- -->

    - #### getnsite

          public int getnsite()

    <!-- -->

    - #### getdbLinks

          public Vector getdbLinks()

    <!-- -->

    - #### getXids

          public Vector getXids()

    <!-- -->

    - #### printMPArgs

          public void printMPArgs()

    <!-- -->

    - #### debug

          protected void debug(Logger logger,
                               Level level,
                               Executable method,
                               String msg)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleMultiPhaseArgs.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](OracleXAConnection.md)

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
