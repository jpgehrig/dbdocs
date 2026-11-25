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

- [Prev Class](SDODimArray.md)
- [Next Class](SystemConstraint.md)

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

oracle.spatial.network

## Interface SubPath

- All Superinterfaces:
  java.lang.Cloneable, java.lang.Comparable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface SubPath
      extends java.lang.Cloneable, java.io.Serializable, java.lang.Comparable

  This interface defines a sub path with the following properties: A reference path, a start percentage and a start link index in the reference path link list, an end percentage and an end link index in the reference path link list, The partial link cost is assumed to be linearly propotional to the given percentage. A subpath can be the same as the reference path.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                         |
    |-----------------------------------------|----------------------------------------------------------------|
    | `void`                                  | `computeGeometry``(double tolerance)`                          |
    | `double`                                | `getCost``()`                                                  |
    | `double`                                | `getDuration``()`                                              |
    | `int`                                   | `getEndLinkIndex``()`                                          |
    | `double`                                | `getEndPercentage``()`                                         |
    | [`JGeometry`](../geometry/JGeometry.md) | `getGeometry``()`                                              |
    | `int`                                   | `getID``()`                                                    |
    | `java.lang.String`                      | `getName``()`                                                  |
    | [`Path`](Path.md)                       | `getReferencePath``()`                                         |
    | `int`                                   | `getStartLinkIndex``()`                                        |
    | `double`                                | `getStartPercentage``()`                                       |
    | `java.lang.String`                      | `getType``()`                                                  |
    | `java.lang.Object`                      | `getUserData``()`                                              |
    | `java.lang.Object`                      | `getUserData``(java.lang.String name)`                         |
    | `boolean`                               | `isActive``()`                                                 |
    | `boolean`                               | `isFullPath``()`                                               |
    | `boolean`                               | `isTemporary``()`                                              |
    | `boolean`                               | `isValid``()`                                                  |
    | `void`                                  | `setEndLinkIndex``(int index)`                                 |
    | `void`                                  | `setEndPercentage``(double percentage)`                        |
    | `void`                                  | `setID``(int id)`                                              |
    | `void`                                  | `setName``(java.lang.String name)`                             |
    | `void`                                  | `setReferencePath``(`[`Path`](Path.md)` path)`                 |
    | `void`                                  | `setStartLinkIndex``(int index)`                               |
    | `void`                                  | `setStartPercentage``(double percentage)`                      |
    | `void`                                  | `setType``(java.lang.String type)`                             |
    | `void`                                  | `setUserData``(java.lang.Object userData)`                     |
    | `void`                                  | `setUserData``(java.lang.String name, java.lang.Object data)`  |

    - ### Methods inherited from interface java.lang.Comparable

      `compareTo`

<!-- -->

- - ### Method Detail

    - #### setReferencePath

          void setReferencePath(Path path)

    <!-- -->

    - #### getReferencePath

          Path getReferencePath()

    <!-- -->

    - #### setStartPercentage

          void setStartPercentage(double percentage)

    <!-- -->

    - #### setStartLinkIndex

          void setStartLinkIndex(int index)

    <!-- -->

    - #### getStartLinkIndex

          int getStartLinkIndex()

    <!-- -->

    - #### getStartPercentage

          double getStartPercentage()

    <!-- -->

    - #### setEndLinkIndex

          void setEndLinkIndex(int index)

    <!-- -->

    - #### getEndLinkIndex

          int getEndLinkIndex()

    <!-- -->

    - #### setEndPercentage

          void setEndPercentage(double percentage)

    <!-- -->

    - #### getEndPercentage

          double getEndPercentage()

    <!-- -->

    - #### getCost

          double getCost()

    <!-- -->

    - #### getDuration

          double getDuration()

    <!-- -->

    - #### computeGeometry

          void computeGeometry(double tolerance)
                        throws NetworkDataException

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getGeometry

          JGeometry getGeometry()

    <!-- -->

    - #### isFullPath

          boolean isFullPath()

    <!-- -->

    - #### isValid

          boolean isValid()

    <!-- -->

    - #### getID

          int getID()

    <!-- -->

    - #### getName

          java.lang.String getName()

    <!-- -->

    - #### getType

          java.lang.String getType()

    <!-- -->

    - #### setID

          void setID(int id)

    <!-- -->

    - #### setName

          void setName(java.lang.String name)

    <!-- -->

    - #### setType

          void setType(java.lang.String type)

    <!-- -->

    - #### isActive

          boolean isActive()

    <!-- -->

    - #### isTemporary

          boolean isTemporary()

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData()

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.Object userData)

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.String name,
                           java.lang.Object data)

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData(java.lang.String name)

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

- [Prev Class](SDODimArray.md)
- [Next Class](SystemConstraint.md)

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
