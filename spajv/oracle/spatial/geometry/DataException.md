Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](CoordSysInfo.md)
- [Next Class](ElementExtractor.md)

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

oracle.spatial.geometry

## Class DataException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.spatial.geometry.DataException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class DataException
      extends java.lang.Exception

  Reports SDOVIS exception related with map data access. This exception will be thrown when the renderer encounters error when accessing theme or map data. In most cases it nests an SQL exception.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type     | Field and Description |
    |-----------------------|-----------------------|
    | `java.lang.String`    | `description`         |
    | `java.lang.Throwable` | `detail`              |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                          |
    |----------------------------------------------------------------------|
    | `DataException``()`                                                  |
    | `DataException``(java.lang.String message)`                          |
    | `DataException``(java.lang.String message, java.lang.Throwable ex)`  |
    | `DataException``(java.lang.Throwable ex)`                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                       |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `printStackTrace``()`<br>Prints the composite message to `System.err`.                                                                       |
    | `void`             | `printStackTrace``(java.io.PrintStream ps)`<br>Prints the composite message and the embedded stack trace to the specified stream `ps`.       |
    | `void`             | `printStackTrace``(java.io.PrintWriter pw)`<br>Prints the composite message and the embedded stack trace to the specified print writer `pw`. |
    | `java.lang.String` | `toString``()`                                                                                                                               |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### description

          public java.lang.String description

    <!-- -->

    - #### detail

          public java.lang.Throwable detail

  <!-- -->

  - ### Constructor Detail

    - #### DataException

          public DataException()

    <!-- -->

    - #### DataException

          public DataException(java.lang.Throwable ex)

    <!-- -->

    - #### DataException

          public DataException(java.lang.String message)

    <!-- -->

    - #### DataException

          public DataException(java.lang.String message,
                               java.lang.Throwable ex)

  <!-- -->

  - ### Method Detail

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Throwable`

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintStream ps)

      Prints the composite message and the embedded stack trace to the specified stream `ps`.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

      Parameters:
      `ps` - the print stream

    <!-- -->

    - #### printStackTrace

          public void printStackTrace()

      Prints the composite message to `System.err`.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintWriter pw)

      Prints the composite message and the embedded stack trace to the specified print writer `pw`.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

      Parameters:
      `pw` - the print writer

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](CoordSysInfo.md)
- [Next Class](ElementExtractor.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
