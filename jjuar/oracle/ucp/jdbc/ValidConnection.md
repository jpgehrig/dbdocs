Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ValidConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UCPXAConnectionBuilder.md)
- Next Class

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

oracle.ucp.jdbc

## Interface ValidConnection

-

  ------------------------------------------------------------------------



      public interface ValidConnection

  This interface allows JDBC applications to easily and quickly determine the usability of a `java.sql.Connection` object and to identify connection objects that should no longer be used for connection pooling.
  The `isValid()` method can be used for checking a connection or used in combination with a retry mechanism, such as one in response to Fast Connection Failover handling.

  The `setInvalid()` method is used to identify connections that are no longer suitable to be used in connection pooling. Once `setInvalid()` is called on a connection, the connection will not be returned to the pool instance upon `close()` but will instead be physically closed and removed from the pool instance.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                         |
    |-------------------|--------------------------------------------------------------------------------|
    | `boolean`         | `isValid``()`<br>Indicates whether this connection is usable.                  |
    | `void`            | `setInvalid``()`<br>Indicates that this connection is no longer valid for use. |

<!-- -->

- - ### Method Detail

    - #### isValid

          boolean isValid()
                   throws java.sql.SQLException

      Indicates whether this connection is usable.
      This can be used for general checking purpose on a connection, or used in combination with a retry mechanism, such as one in response to Fast Connection Failover handling.

      Returns:
      A boolean indicating whether this connection is usable. `true` if so; otherwise, `false`.

      Throws:
      `java.sql.SQLException` - If an error occurs.

    <!-- -->

    - #### setInvalid

          void setInvalid()
                   throws java.sql.SQLException

      Indicates that this connection is no longer valid for use.
      This method is used to identify connections that are no longer suitable to be used in connection pooling. Once it has been called on a connection, the connection is not returned to the pool instance upon `close()` but is instead physically closed and removed from the pool instance.

      Throws:
      `java.sql.SQLException` - If an error occurs.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ValidConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UCPXAConnectionBuilder.md)
- Next Class

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
