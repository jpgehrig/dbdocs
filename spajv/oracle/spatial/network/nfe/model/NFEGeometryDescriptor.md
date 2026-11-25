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

- [Prev Class](NFEEditionMode.md)
- [Next Class](NFEIdGenerator.md)

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

## Class NFEGeometryDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEGeometryDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEGeometryDescriptor
      extends java.lang.Object

  This class contains the geometry metadata of an NFE model.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                            |
    |--------------------------------------------------------------------------------------------------------|
    | `NFEGeometryDescriptor``(int srid, java.util.List<`[`SDODimElement`](SDODimElement.md)`> dimensions)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                            |
    |---------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
    | `NFEGeometryDescriptor`                                 | `createCopy``()`<br>Returns a copy of the object.                                                                 |
    | `boolean`                                               | `equals``(java.lang.Object obj)`                                                                                  |
    | `java.util.List<`[`SDODimElement`](SDODimElement.md)`>` | `getDimensions``()`<br>Returns the model dimensions.                                                              |
    | `int`                                                   | `getSrid``()`<br>Returns SRID.                                                                                    |
    | `SRS`                                                   | `getSrs``()`<br>Returns SRS.                                                                                      |
    | `double`                                                | `getTolerance``()`<br>Returns the tolerance.                                                                      |
    | `void`                                                  | `setDimensions``(java.util.List<`[`SDODimElement`](SDODimElement.md)`> dimensions)`<br>Sets the model dimensions. |
    | `void`                                                  | `setSrid``(int srid)`<br>Sets SRID.                                                                               |
    | `void`                                                  | `setSrs``(SRS srs)`<br>Sets SRS                                                                                   |
    | `java.lang.String`                                      | `toString``()`                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEGeometryDescriptor

          public NFEGeometryDescriptor(int srid,
                                       java.util.List<SDODimElement> dimensions)

  <!-- -->

  - ### Method Detail

    - #### getSrid

          public int getSrid()

      Returns SRID.
      Returns:
      SRID

    <!-- -->

    - #### setSrid

          public void setSrid(int srid)

      Sets SRID.
      Parameters:
      `srid` - SRID

    <!-- -->

    - #### getDimensions

          public java.util.List<SDODimElement> getDimensions()

      Returns the model dimensions.
      Returns:
      model dimensions

    <!-- -->

    - #### setDimensions

          public void setDimensions(java.util.List<SDODimElement> dimensions)

      Sets the model dimensions.
      Parameters:
      `dimensions` - model dimensions

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getSrs

          public SRS getSrs()

      Returns SRS.
      Returns:
      SRS

    <!-- -->

    - #### setSrs

          public void setSrs(SRS srs)

      Sets SRS
      Parameters:
      `srs` - SRS

    <!-- -->

    - #### createCopy

          public NFEGeometryDescriptor createCopy()

      Returns a copy of the object.
      Returns:
      copy of the object

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### getTolerance

          public double getTolerance()

      Returns the tolerance.
      Returns:
      tolerance

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

- [Prev Class](NFEEditionMode.md)
- [Next Class](NFEIdGenerator.md)

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
