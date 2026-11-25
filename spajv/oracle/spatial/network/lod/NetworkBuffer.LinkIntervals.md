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

- [Prev Class](NetworkBuffer.LinkInterval.md)
- [Next Class](NetworkExplorer.md)

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

## Class NetworkBuffer.LinkIntervals

- java.lang.Object

- - oracle.spatial.network.lod.NetworkBuffer.LinkIntervals

<!-- -->

- Enclosing class:
  [NetworkBuffer](NetworkBuffer.md)

  ------------------------------------------------------------------------



      public static class NetworkBuffer.LinkIntervals
      extends java.lang.Object

  An instance of this class contains a LogicalLink object and a list of intervals associated with the link object.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LinkIntervals``(`[`LogicalLink`](LogicalLink.md)` link, long[] prevLinkIds, `[`NetworkBuffer.DoubleInterval`](NetworkBuffer.DoubleInterval.md)`[] intervals)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                     | Method and Description                                                                                                                                                |
    |-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                | `addIntervals``(`[`NetworkBuffer.LinkInterval`](NetworkBuffer.LinkInterval.md)`[] intervals)`<br>Adds intervals.                                                      |
    | [`NetworkBuffer.DoubleInterval`](NetworkBuffer.DoubleInterval.md)`[]` | `getIntervals``()`                                                                                                                                                    |
    | [`LogicalLink`](LogicalLink.md)                                       | `getLink``()`<br>Returns the link object.                                                                                                                             |
    | [`NetworkBuffer.LinkInterval`](NetworkBuffer.LinkInterval.md)`[]`     | `getLinkIntervalArray``()`<br>Returns the intervals associated with the link.                                                                                         |
    | `boolean`                                                             | `hasInterval``(`[`NetworkBuffer.DoubleInterval`](NetworkBuffer.DoubleInterval.md)` interval)`<br>Checks whether the link interval object contains the input interval. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LinkIntervals

          public LinkIntervals(LogicalLink link,
                               long[] prevLinkIds,
                               NetworkBuffer.DoubleInterval[] intervals)

  <!-- -->

  - ### Method Detail

    - #### getLink

          public LogicalLink getLink()

      Returns the link object.
      Returns:

    <!-- -->

    - #### getLinkIntervalArray

          public NetworkBuffer.LinkInterval[] getLinkIntervalArray()

      Returns the intervals associated with the link.
      Returns:

    <!-- -->

    - #### getIntervals

          public NetworkBuffer.DoubleInterval[] getIntervals()

    <!-- -->

    - #### addIntervals

          public void addIntervals(NetworkBuffer.LinkInterval[] intervals)

      Adds intervals.
      Parameters:
      `intervals` -

    <!-- -->

    - #### hasInterval

          public boolean hasInterval(NetworkBuffer.DoubleInterval interval)

      Checks whether the link interval object contains the input interval.
      Parameters:

      `interval` -

      Returns:

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

- [Prev Class](NetworkBuffer.LinkInterval.md)
- [Next Class](NetworkExplorer.md)

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
