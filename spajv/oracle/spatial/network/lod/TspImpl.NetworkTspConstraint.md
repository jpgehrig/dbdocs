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

- [Prev Class](TspImpl.md)
- [Next Class](TspNearestNeighbor.md)

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

## Class TspImpl.NetworkTspConstraint

- java.lang.Object

- - oracle.spatial.network.lod.TspImpl.NetworkTspConstraint

<!-- -->

- All Implemented Interfaces:
  [Constraint](Constraint.md)\<[TspAnalysisInfo](TspAnalysisInfo.md)\>, [TspConstraint](TspConstraint.md)

  <!-- -->

  Enclosing class:
  [TspImpl](TspImpl.md)

  ------------------------------------------------------------------------



      public static class TspImpl.NetworkTspConstraint
      extends java.lang.Object
      implements TspConstraint

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                      |
    |--------------------------------------------------------------------------------------------------|
    | `NetworkTspConstraint``(`[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                 |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                                                                                                                              |
    | `boolean`         | `isSatisfied``(`[`TspAnalysisInfo`](TspAnalysisInfo.md)` context)`<br>Checks if the constraint is satisfied.                                                                                                                                                                                                           |
    | `void`            | `reset``()`<br>This method allows a stateful network constraint object to be reset to its original state and reused by network analysis functions.                                                                                                                                                                     |
    | `void`            | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this constraint, so that the constraint can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NetworkTspConstraint

          public NetworkTspConstraint(LODNetworkConstraint networkConstraint)

  <!-- -->

  - ### Method Detail

    - #### getUserDataCategories

          public int[] getUserDataCategories()

      Description copied from interface: [`TspConstraint`](TspConstraint.md)
      Returns the required user data categories.
      Specified by:

      [`getUserDataCategories`](TspConstraint.md) in interface [`TspConstraint`](TspConstraint.md)

      Returns:

    <!-- -->

    - #### reset

          public void reset()

      Description copied from interface: [`TspConstraint`](TspConstraint.md)
      This method allows a stateful network constraint object to be reset to its original state and reused by network analysis functions.
      Specified by:
      [`reset`](TspConstraint.md) in interface [`TspConstraint`](TspConstraint.md)

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`TspConstraint`](TspConstraint.md)
      This method allows caller to pass the network analyst object to this constraint, so that the constraint can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the constraint, the link level selector can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](TspConstraint.md) in interface [`TspConstraint`](TspConstraint.md)

    <!-- -->

    - #### isSatisfied

          public boolean isSatisfied(TspAnalysisInfo context)

      Description copied from interface: [`Constraint`](Constraint.md)
      Checks if the constraint is satisfied.
      Specified by:
      [`isSatisfied`](Constraint.md) in interface [`Constraint`](Constraint.md)`<`[`TspAnalysisInfo`](TspAnalysisInfo.md)`>`

      Parameters:
      `context` - the analysis context

      See Also:
      [`LODAnalysisInfo`](LODAnalysisInfo.md)

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

- [Prev Class](TspImpl.md)
- [Next Class](TspNearestNeighbor.md)

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
