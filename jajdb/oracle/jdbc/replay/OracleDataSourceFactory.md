Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataSourceFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataSource.md)
- [Next Class](OracleDataSourceImpl.md)

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

oracle.jdbc.replay

## Class OracleDataSourceFactory

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.replay.OracleDataSourceFactory

<!-- -->

-

  ------------------------------------------------------------------------



      public class OracleDataSourceFactory
      extends Object

  Data source factory for creating instances of `OracleDataSource`, `OracleConnectionPoolDataSource`, and `OracleXADataSource` that provide transparent failover replay support.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description    |
    |--------------------------------|
    | `OracleDataSourceFactory``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                           |
    |--------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
    | `static `[`OracleConnectionPoolDataSource`](OracleConnectionPoolDataSource.md) | `getOracleConnectionPoolDataSource``()`<br>Obtains an `OracleConnectionPoolDataSource` instance. |
    | `static `[`OracleDataSource`](OracleDataSource.md)                             | `getOracleDataSource``()`<br>Obtains an `OracleDataSource` instance.                             |
    | `static `[`OracleXADataSource`](OracleXADataSource.md)                         | `getOracleXADataSource``()`<br>Obtains an `OracleXADataSource` instance.                         |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### OracleDataSourceFactory

          public OracleDataSourceFactory()

  <!-- -->

  - ### Method Detail

    - #### getOracleDataSource

          public static OracleDataSource getOracleDataSource()

      Obtains an `OracleDataSource` instance.
      Returns:
      An `OracleDataSource` instance.

    <!-- -->

    - #### getOracleConnectionPoolDataSource

          public static OracleConnectionPoolDataSource getOracleConnectionPoolDataSource()

      Obtains an `OracleConnectionPoolDataSource` instance.
      Returns:
      An `OracleConnectionPoolDataSource` instance.

    <!-- -->

    - #### getOracleXADataSource

          public static OracleXADataSource getOracleXADataSource()

      Obtains an `OracleXADataSource` instance.
      Returns:
      An `OracleXADataSource` instance.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataSourceFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDataSource.md)
- [Next Class](OracleDataSourceImpl.md)

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
