Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODNetworkConstraint.md)
- [Next Class](LODNetworkFactory.md)

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

oracle.spatial.network.lod

## Class LODNetworkException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.spatial.network.lod.LODNetworkException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [LinkNotFoundException](LinkNotFoundException.md), [LODConfigException](config/LODConfigException.md), [MethodNotSupportedException](MethodNotSupportedException.md), [NodeNotFoundException](NodeNotFoundException.md)

  ------------------------------------------------------------------------



      public class LODNetworkException
      extends java.lang.Exception

  Base exception class for Load-On-Demand network analysis.
  Since:
  Oracle Database 11g Release 1 (11.1)

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description       |
    |-------------------|-----------------------------|
    | `static int`      | `ERROR_CODE_TOOMANYPOINTS`  |
    | `static int`      | `ERROR_CODE_UNKNOWN`        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                       |
    |-------------------------------------------------------------------|
    | `LODNetworkException``(java.lang.Exception ex)`                   |
    | `LODNetworkException``(java.lang.String message)`                 |
    | `LODNetworkException``(java.lang.String message, int errorCode)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description |
    |-------------------|------------------------|
    | `int`             | `getErrorCode``()`     |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ERROR_CODE_UNKNOWN

          public static final int ERROR_CODE_UNKNOWN

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ERROR_CODE_TOOMANYPOINTS

          public static final int ERROR_CODE_TOOMANYPOINTS

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### LODNetworkException

          public LODNetworkException(java.lang.String message)

    <!-- -->

    - #### LODNetworkException

          public LODNetworkException(java.lang.String message,
                                     int errorCode)

    <!-- -->

    - #### LODNetworkException

          public LODNetworkException(java.lang.Exception ex)

  <!-- -->

  - ### Method Detail

    - #### getErrorCode

          public int getErrorCode()

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODNetworkConstraint.md)
- [Next Class](LODNetworkFactory.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
