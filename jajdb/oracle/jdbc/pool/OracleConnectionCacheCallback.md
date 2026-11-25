Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionCacheCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionCache.md)
- [Next Class](OracleConnectionCacheManager.md)

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

oracle.jdbc.pool

## Interface OracleConnectionCacheCallback

-

  ------------------------------------------------------------------------

  Deprecated. 
  Use Oracle Universal Connection Pool instead. Callback functionality for the Implicit Connection Cache


      public interface OracleConnectionCacheCallback

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                            |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleAbandonedConnection``(`[`OracleConnection`](../OracleConnection.md)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` userObject)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. |
    | `void`            | `releaseConnection``(`[`OracleConnection`](../OracleConnection.md)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` userObject)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.         |

<!-- -->

- - ### Method Detail

    - #### handleAbandonedConnection

          boolean handleAbandonedConnection(OracleConnection conn,
                                            Object userObject)

      Deprecated. Use Oracle Universal Connection Pool instead.

    <!-- -->

    - #### releaseConnection

          void releaseConnection(OracleConnection conn,
                                 Object userObject)

      Deprecated. Use Oracle Universal Connection Pool instead.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionCacheCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionCache.md)
- [Next Class](OracleConnectionCacheManager.md)

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
