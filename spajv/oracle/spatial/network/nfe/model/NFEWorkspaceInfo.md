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

- [Prev Class](NFEModelObjectFactory.md)
- [Next Class](SDODimElement.md)

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

oracle.spatial.network.nfe.model

## Class NFEWorkspaceInfo

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEWorkspaceInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEWorkspaceInfo
      extends java.lang.Object

  Contains information related to the workspace. The manipulator uses this information to allow or deny features edition. This information has to be set by the client and will not be set at model loading time.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEWorkspaceInfo``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                         |
    |----------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | `void`               | `addLockedArea``(`[`JGeometry`](../../../geometry/JGeometry.md)` geometry)`<br>Adds the specified geometry in the locked area. |
    | `java.awt.geom.Area` | `getLockedArea``()`<br>Returns the locked area.                                                                                |
    | `java.lang.String`   | `getWorkspaceName``()`<br>Returns the workspace name.                                                                          |
    | `void`               | `removeLockedArea``(`[`JGeometry`](../../../geometry/JGeometry.md)` geometry)`<br>Removes the geometry from the locked area.   |
    | `void`               | `resetLockedAreas``()`<br>This function will empty the locked area.                                                            |
    | `void`               | `setLockedArea``(java.awt.geom.Area lockedArea)`<br>Sets the locked area.                                                      |
    | `void`               | `setWorkspaceName``(java.lang.String workspaceName)`<br>Sets the workspace name                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEWorkspaceInfo

          public NFEWorkspaceInfo()

  <!-- -->

  - ### Method Detail

    - #### getWorkspaceName

          public java.lang.String getWorkspaceName()

      Returns the workspace name.
      Returns:
      workspace name

    <!-- -->

    - #### setWorkspaceName

          public void setWorkspaceName(java.lang.String workspaceName)

      Sets the workspace name
      Parameters:
      `workspaceName` - workspace name

    <!-- -->

    - #### addLockedArea

          public void addLockedArea(JGeometry geometry)

      Adds the specified geometry in the locked area.
      Parameters:
      `geometry` - geometry to add in the locked area

    <!-- -->

    - #### removeLockedArea

          public void removeLockedArea(JGeometry geometry)

      Removes the geometry from the locked area.
      Parameters:
      `geometry` - geometry to remove from the locked area

    <!-- -->

    - #### resetLockedAreas

          public void resetLockedAreas()

      This function will empty the locked area.

    <!-- -->

    - #### getLockedArea

          public java.awt.geom.Area getLockedArea()

      Returns the locked area.
      Returns:
      locked area

    <!-- -->

    - #### setLockedArea

          public void setLockedArea(java.awt.geom.Area lockedArea)

      Sets the locked area.
      Parameters:
      `lockedArea` - locked area

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

- [Prev Class](NFEModelObjectFactory.md)
- [Next Class](SDODimElement.md)

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
