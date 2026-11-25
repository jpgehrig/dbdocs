Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalPooledConnectionStatus.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalPooledConnection.md)
- Next Class

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

oracle.ucp

## Class UniversalPooledConnectionStatus

- java.lang.Object

- - oracle.ucp.UniversalPooledConnectionStatus

<!-- -->

-

  ------------------------------------------------------------------------



      public class UniversalPooledConnectionStatus
      extends java.lang.Object

  Describes the status of a pooled connection.
  The status of the pooled connection is looked at when the connection is returned by the borrower. If the status is `normal`, then the pooled connection is processed normally. If the status is `close on return`, then the pooled connection is automatically closed and it is not returned to the connection pool.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                        | Field and Description                                                                                                                                          |
    |------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static UniversalPooledConnectionStatus` | `STATUS_BAD`<br>The pooled connection's status is bad.                                                                                                         |
    | `static java.lang.String`                | `STATUS_BAD_DESC`                                                                                                                                              |
    | `static UniversalPooledConnectionStatus` | `STATUS_CLOSE_ON_RETURN`<br>The pooled connection should be closed and not put back into the pool when it is returned by the borrower.                         |
    | `static java.lang.String`                | `STATUS_CLOSE_ON_RETURN_DESC`                                                                                                                                  |
    | `static UniversalPooledConnectionStatus` | `STATUS_CLOSED`<br>The pooled connection's status is closed.                                                                                                   |
    | `static java.lang.String`                | `STATUS_CLOSED_DESC`                                                                                                                                           |
    | `static UniversalPooledConnectionStatus` | `STATUS_NORMAL`<br>The pooled connection's status is normal.                                                                                                   |
    | `static java.lang.String`                | `STATUS_NORMAL_DESC`                                                                                                                                           |
    | `static UniversalPooledConnectionStatus` | `STATUS_RECONNECTING`<br>The pooled connection's status is reconnecting.                                                                                       |
    | `static java.lang.String`                | `STATUS_RECONNECTING_DESC`                                                                                                                                     |
    | `static UniversalPooledConnectionStatus` | `STATUS_REPLACE_ON_RETURN`<br>The pooled connection should be closed and replaced with a brand new connection in the pool when it is returned by the borrower. |
    | `static java.lang.String`                | `STATUS_REPLACE_ON_RETURN_DESC`                                                                                                                                |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                      |
    |--------------------|-------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object status)`<br>Determines equality. |
    | `protected int`    | `getStatus``()`                                             |
    | `java.lang.String` | `toString``()`                                              |

    - ### Methods inherited from class java.lang.Object

      `clone, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### STATUS_NORMAL_DESC

          public static final java.lang.String STATUS_NORMAL_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### STATUS_CLOSED_DESC

          public static final java.lang.String STATUS_CLOSED_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### STATUS_BAD_DESC

          public static final java.lang.String STATUS_BAD_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### STATUS_CLOSE_ON_RETURN_DESC

          public static final java.lang.String STATUS_CLOSE_ON_RETURN_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### STATUS_REPLACE_ON_RETURN_DESC

          public static final java.lang.String STATUS_REPLACE_ON_RETURN_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### STATUS_RECONNECTING_DESC

          public static final java.lang.String STATUS_RECONNECTING_DESC

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### STATUS_NORMAL

          public static final UniversalPooledConnectionStatus STATUS_NORMAL

      The pooled connection's status is normal.

    <!-- -->

    - #### STATUS_CLOSE_ON_RETURN

          public static final UniversalPooledConnectionStatus STATUS_CLOSE_ON_RETURN

      The pooled connection should be closed and not put back into the pool when it is returned by the borrower.

    <!-- -->

    - #### STATUS_REPLACE_ON_RETURN

          public static final UniversalPooledConnectionStatus STATUS_REPLACE_ON_RETURN

      The pooled connection should be closed and replaced with a brand new connection in the pool when it is returned by the borrower.

    <!-- -->

    - #### STATUS_CLOSED

          public static final UniversalPooledConnectionStatus STATUS_CLOSED

      The pooled connection's status is closed.

    <!-- -->

    - #### STATUS_BAD

          public static final UniversalPooledConnectionStatus STATUS_BAD

      The pooled connection's status is bad.

    <!-- -->

    - #### STATUS_RECONNECTING

          public static final UniversalPooledConnectionStatus STATUS_RECONNECTING

      The pooled connection's status is reconnecting.

  <!-- -->

  - ### Method Detail

    - #### equals

          public boolean equals(java.lang.Object status)

      Determines equality.
      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `status` - The object to compare.

      Returns:
      `true` if this object is equal to the object passed in; otherwise, `false`.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getStatus

          protected int getStatus()

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalPooledConnectionStatus.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalPooledConnection.md)
- Next Class

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
