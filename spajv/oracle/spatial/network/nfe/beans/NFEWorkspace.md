Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEWithinCost.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.beans

## Class NFEWorkspace

- java.lang.Object

- - oracle.spatial.network.nfe.beans.NFEWorkspace

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEWorkspace
      extends java.lang.Object

  Describes a workspace used by the workspace manager for versioning. The workspaces are related to models. A minimum bounding rectangle (MBR) work area can be defined for a workspace and the work area can be locked to any other workspace. The locking is checked in memory during features manipulations (see functions NFEManipulator.isAllowedPoint and NFEManipulator.isAllowedRectangle).

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEWorkspace``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                   |
    |--------------------|----------------------------------------------------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object obj)`                                                                         |
    | `double`           | `getLowerX``()`<br>Returns the workspace work area lowest X.                                             |
    | `double`           | `getLowerY``()`<br>Returns the workspace work area lower Y.                                              |
    | `long`             | `getModelId``()`<br>Returns the model id to which the workspace is related.                              |
    | `double`           | `getUpperX``()`<br>Returns the workspace work area upper X.                                              |
    | `double`           | `getUpperY``()`<br>Returns the workspace work area upper Y.                                              |
    | `java.lang.String` | `getWorkspace``()`<br>Returns the workspace name.                                                        |
    | `int`              | `hashCode``()`                                                                                           |
    | `boolean`          | `isLockInd``()`<br>Returns true if the work area is locked, false otherwise.                             |
    | `boolean`          | `isMbrInd``()`<br>Returns true if a work area is defined for the workspace, false otherwise.             |
    | `void`             | `setLockInd``(boolean lockInd)`<br>Sets true if the work area is locked, false otherwise.                |
    | `void`             | `setLowerX``(double lowerX)`<br>Sets the workspace work area lowest X.                                   |
    | `void`             | `setLowerY``(double lowerY)`<br>Sets the workspace work area lower Y.                                    |
    | `void`             | `setMbrInd``(boolean mbrInd)`<br>Sets true if a work area is defined for the workspace, false otherwise. |
    | `void`             | `setModelId``(long modelId)`<br>Sets the model id to which the workspace is related.                     |
    | `void`             | `setUpperX``(double upperX)`<br>Sets the workspace work area upper X.                                    |
    | `void`             | `setUpperY``(double upperY)`<br>Sets the workspace work area upper Y.                                    |
    | `void`             | `setWorkspace``(java.lang.String workspace)`<br>Sets the workspace name.                                 |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEWorkspace

          public NFEWorkspace()

  <!-- -->

  - ### Method Detail

    - #### getModelId

          public long getModelId()

      Returns the model id to which the workspace is related.
      Returns:
      model id

    <!-- -->

    - #### setModelId

          public void setModelId(long modelId)

      Sets the model id to which the workspace is related.
      Parameters:
      `modelId` - model id

    <!-- -->

    - #### getWorkspace

          public java.lang.String getWorkspace()

      Returns the workspace name.
      Returns:
      workspace name

    <!-- -->

    - #### setWorkspace

          public void setWorkspace(java.lang.String workspace)

      Sets the workspace name.
      Parameters:
      `workspace` - workspace name

    <!-- -->

    - #### getLowerX

          public double getLowerX()

      Returns the workspace work area lowest X.
      Returns:
      workspace work area lowest X

    <!-- -->

    - #### setLowerX

          public void setLowerX(double lowerX)

      Sets the workspace work area lowest X.
      Parameters:
      `lowerX` - workspace work area lowest X

    <!-- -->

    - #### getUpperX

          public double getUpperX()

      Returns the workspace work area upper X.
      Returns:
      workspace work area upper X

    <!-- -->

    - #### setUpperX

          public void setUpperX(double upperX)

      Sets the workspace work area upper X.
      Parameters:
      `upperX` - workspace work area upper X

    <!-- -->

    - #### getLowerY

          public double getLowerY()

      Returns the workspace work area lower Y.
      Returns:
      workspace work area lower Y

    <!-- -->

    - #### setLowerY

          public void setLowerY(double lowerY)

      Sets the workspace work area lower Y.
      Parameters:
      `lowerY` - workspace work area lower Y

    <!-- -->

    - #### getUpperY

          public double getUpperY()

      Returns the workspace work area upper Y.
      Returns:
      workspace work area upper Y

    <!-- -->

    - #### setUpperY

          public void setUpperY(double upperY)

      Sets the workspace work area upper Y.
      Parameters:
      `upperY` - workspace work area upper Y

    <!-- -->

    - #### isMbrInd

          public boolean isMbrInd()

      Returns true if a work area is defined for the workspace, false otherwise.
      Returns:
      true if a work area is defined for the workspace, false otherwise

    <!-- -->

    - #### setMbrInd

          public void setMbrInd(boolean mbrInd)

      Sets true if a work area is defined for the workspace, false otherwise.
      Parameters:
      `mbrInd` - true if a work area is defined for the workspace, false otherwise

    <!-- -->

    - #### isLockInd

          public boolean isLockInd()

      Returns true if the work area is locked, false otherwise.
      Returns:
      true if the work area is locked, false otherwise

    <!-- -->

    - #### setLockInd

          public void setLockInd(boolean lockInd)

      Sets true if the work area is locked, false otherwise.
      Parameters:
      `lockInd` - true if the work area is locked, false otherwise

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEWithinCost.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
