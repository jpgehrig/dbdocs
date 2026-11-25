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

- [Prev Class](RTreeInterface.md)
- [Next Class](UnitSphere.md)

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

## Class Union

- java.lang.Object

- - oracle.spatial.geometry.Union

<!-- -->

-

  ------------------------------------------------------------------------



      public class Union
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------|
    | `Union``(int K)`<br>Constructor: Initialize an empty Union data struct with K Sets/Components indexed 0 to K-1. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                            |
    |-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`             | `areSitesConnected``(int s, int r)`<br>This method determines whether the Set/Component containing Site/Element "s" is the same as the Set/Component containing Site/Element "r". |
    | `int`                 | `countElements``()`<br>Returns the number of Sites/Elements (i.e., size of id Array).                                                                                             |
    | `int`                 | `countSets``()`<br>Returns the number of Sets/Components.                                                                                                                         |
    | `int`                 | `findSetIdentifier``(int item)`<br>Returns the Set/Component Identifier in id Array for the Set/Component containing the Site/Element "s".                                        |
    | `java.util.ArrayList` | `getAllSetIdentifiersforParents``()`<br>This method returns the Set/Component Identifiers for Parent Sites/Elements.                                                              |
    | `static void`         | `main``(java.lang.String[] args)`                                                                                                                                                 |
    | `void`                | `unionSets``(int s, int r)`<br>This method merges the Set/Component containing Site/Element "s" with the Set/Component containing the Site/Element "r".                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Union

          public Union(int K)

      Constructor: Initialize an empty Union data struct with K Sets/Components indexed 0 to K-1. Each Set/Component has exactly 1 Site/Element initially.
      Parameters:
      `K` - the number of objects (such as Geometries represented by a label).

  <!-- -->

  - ### Method Detail

    - #### findSetIdentifier

          public int findSetIdentifier(int item)

      Returns the Set/Component Identifier in id Array for the Set/Component containing the Site/Element "s".
      Parameters:
      `item` - the integer which represents the Site/Element

      Returns:
      the Set/Component Identifier in id Array for the Set/Component containing the Site/Element "s".

    <!-- -->

    - #### countSets

          public int countSets()

      Returns the number of Sets/Components.
      Returns:
      the number of Sets/Components.

    <!-- -->

    - #### countElements

          public int countElements()

      Returns the number of Sites/Elements (i.e., size of id Array).
      Returns:
      the number of Sites/Elements.

    <!-- -->

    - #### unionSets

          public void unionSets(int s,
                                int r)

      This method merges the Set/Component containing Site/Element "s" with the Set/Component containing the Site/Element "r".
      Parameters:
      `s` - the integer value for first Site/Element

      `r` - the integer value for second Site/Element

    <!-- -->

    - #### areSitesConnected

          public boolean areSitesConnected(int s,
                                           int r)

      This method determines whether the Set/Component containing Site/Element "s" is the same as the Set/Component containing Site/Element "r". In other words, it tells whether both Sites/Elements are in the same Set/Component.
      Parameters:
      `s` - the integer value for first Site/Element

      `r` - the integer value for second Site/Element

    <!-- -->

    - #### getAllSetIdentifiersforParents

          public java.util.ArrayList getAllSetIdentifiersforParents()

      This method returns the Set/Component Identifiers for Parent Sites/Elements. As an application: For a valid Simple Solid Geometry: there should be exactly 1 element in the returned ArrayList.
      Returns:
      an ArrayList containing the Set/Component Identifiers for Parent Sites/Elements.

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)

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

- [Prev Class](RTreeInterface.md)
- [Next Class](UnitSphere.md)

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
