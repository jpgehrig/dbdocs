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

- [Prev Class](TspPathFeature.md)
- [Next Class](UserData.md)

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

## Class TspTimeWindowConstraint

- java.lang.Object

- - oracle.spatial.network.lod.TspTimeWindowConstraint

<!-- -->

- All Implemented Interfaces:
  [Constraint](Constraint.md)\<[TspAnalysisInfo](TspAnalysisInfo.md)\>, [TspConstraint](TspConstraint.md)

  ------------------------------------------------------------------------



      public class TspTimeWindowConstraint
      extends java.lang.Object
      implements TspConstraint

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                    |
    |------------------------------------------------------------------------------------------------|
    | `TspTimeWindowConstraint``(`[`TimeWindow`](TimeWindow.md)`[] timeWindows, int timeCostIndex)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                                                                                                                                 |
    |-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                             | `getTimeCostIndex``()`                                                                                                                                                                                                                                                                                                 |
    | [`TimeWindow`](TimeWindow.md)`[]` | `getTimeWindows``()`                                                                                                                                                                                                                                                                                                   |
    | `int[]`                           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                                                                                                                              |
    | `boolean`                         | `isSatisfied``(`[`TspAnalysisInfo`](TspAnalysisInfo.md)` context)`<br>Checks if the constraint is satisfied.                                                                                                                                                                                                           |
    | `void`                            | `reset``()`<br>This method allows a stateful network constraint object to be reset to its original state and reused by network analysis functions.                                                                                                                                                                     |
    | `void`                            | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this constraint, so that the constraint can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |
    | `void`                            | `setTimeCostIndex``(int timeCostIndex)`                                                                                                                                                                                                                                                                                |
    | `void`                            | `setTimeWindows``(`[`TimeWindow`](TimeWindow.md)`[] timeWindows)`                                                                                                                                                                                                                                                      |
    | `java.lang.String`                | `toString``()`                                                                                                                                                                                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TspTimeWindowConstraint

          public TspTimeWindowConstraint(TimeWindow[] timeWindows,
                                         int timeCostIndex)

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

    <!-- -->

    - #### setTimeWindows

          public void setTimeWindows(TimeWindow[] timeWindows)

    <!-- -->

    - #### getTimeWindows

          public TimeWindow[] getTimeWindows()

    <!-- -->

    - #### setTimeCostIndex

          public void setTimeCostIndex(int timeCostIndex)

    <!-- -->

    - #### getTimeCostIndex

          public int getTimeCostIndex()

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](TspPathFeature.md)
- [Next Class](UserData.md)

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
