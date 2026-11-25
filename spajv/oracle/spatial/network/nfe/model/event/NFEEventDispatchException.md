Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEEventDispatcher.md)
- [Next Class](NFEEventSupport.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.event

## Class NFEEventDispatchException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.spatial.network.nfe.model.event.NFEEventDispatchException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class NFEEventDispatchException
      extends java.lang.Exception

  Represents an error when dispatching events and contains one or more EventListeners which failed to be notified for certain event.
  See Also:
  [Serialized Form](../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------|
    | `NFEEventDispatchException``(java.lang.Object[] failedDispatches)`                                                       |
    | `NFEEventDispatchException``(java.lang.Object[] failedDispatches, java.lang.String message)`                             |
    | `NFEEventDispatchException``(java.lang.Object[] failedDispatches, java.lang.String message, java.lang.Throwable cause)`  |
    | `NFEEventDispatchException``(java.lang.Object[] failedDispatches, java.lang.Throwable cause)`                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                    |
    |----------------------|-------------------------------------------------------------------------------------------|
    | `java.lang.Object[]` | `getFailedDispatches``()`<br>Gets the objects for which the event could not be dispatched |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEEventDispatchException

          public NFEEventDispatchException(java.lang.Object[] failedDispatches)

    <!-- -->

    - #### NFEEventDispatchException

          public NFEEventDispatchException(java.lang.Object[] failedDispatches,
                                           java.lang.String message)

    <!-- -->

    - #### NFEEventDispatchException

          public NFEEventDispatchException(java.lang.Object[] failedDispatches,
                                           java.lang.Throwable cause)

    <!-- -->

    - #### NFEEventDispatchException

          public NFEEventDispatchException(java.lang.Object[] failedDispatches,
                                           java.lang.String message,
                                           java.lang.Throwable cause)

  <!-- -->

  - ### Method Detail

    - #### getFailedDispatches

          public java.lang.Object[] getFailedDispatches()

      Gets the objects for which the event could not be dispatched
      Returns:

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEEventDispatcher.md)
- [Next Class](NFEEventSupport.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
