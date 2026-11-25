Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleOCIFailover.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleNClob.md)
- [Next Class](OracleOpaque.md)

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

oracle.jdbc

## Interface OracleOCIFailover

-

  ------------------------------------------------------------------------



      public interface OracleOCIFailover

  An interface for Transparent Application failover.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `FO_ABORT`            |
    | `static int`      | `FO_BEGIN`            |
    | `static int`      | `FO_END`              |
    | `static int`      | `FO_ERROR`            |
    | `static int`      | `FO_EVENT_UNKNOWN`    |
    | `static int`      | `FO_NONE`             |
    | `static int`      | `FO_REAUTH`           |
    | `static int`      | `FO_RETRY`            |
    | `static int`      | `FO_SELECT`           |
    | `static int`      | `FO_SESSION`          |
    | `static int`      | `FO_TYPE_UNKNOWN`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                      |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `callbackFn``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` ctxt, int type, int event)`  |

<!-- -->

- - ### Field Detail

    - #### FO_SESSION

          static final int FO_SESSION

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_SELECT

          static final int FO_SELECT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_NONE

          static final int FO_NONE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_TYPE_UNKNOWN

          static final int FO_TYPE_UNKNOWN

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_BEGIN

          static final int FO_BEGIN

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_END

          static final int FO_END

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_ABORT

          static final int FO_ABORT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_REAUTH

          static final int FO_REAUTH

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_ERROR

          static final int FO_ERROR

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_RETRY

          static final int FO_RETRY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FO_EVENT_UNKNOWN

          static final int FO_EVENT_UNKNOWN

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### callbackFn

          int callbackFn(Connection conn,
                         Object ctxt,
                         int type,
                         int event)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleOCIFailover.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleNClob.md)
- [Next Class](OracleOpaque.md)

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
