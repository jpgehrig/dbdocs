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

- [Prev Class](OpsJGeometry.md)
- [Next Class](RNode.md)

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

## Class Pair\<P,Q\>

- java.lang.Object

- - oracle.spatial.geometry.Pair\<P,Q\>

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [AbstractRTree.PairDebug](AbstractRTree.PairDebug.md)

  ------------------------------------------------------------------------



      public class Pair<P,Q>
      extends java.lang.Object
      implements java.io.Serializable

  A simple utility class for holding a pair of elements.
  Since:
  release specific (what release of product did this appear in)

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------|
    | `Pair``(Pair<? extends P,? extends Q> orig)`<br>Creates an entry representing the same mapping as the specified entry. |
    | `Pair``(P p, Q q)`                                                                                                     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                        |
    |--------------------|-----------------------------------------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object o)`<br>Compares the specified object with this entry for equality. |
    | `P`                | `getP``()`                                                                                    |
    | `Q`                | `getQ``()`                                                                                    |
    | `int`              | `hashCode``()`                                                                                |
    | `void`             | `setP``(P p)`                                                                                 |
    | `void`             | `setQ``(Q q)`                                                                                 |
    | `java.lang.String` | `toString``()`<br>Returns a String representation of this map entry.                          |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Pair

          public Pair(P p,
                      Q q)

    <!-- -->

    - #### Pair

          public Pair(Pair<? extends P,? extends Q> orig)

      Creates an entry representing the same mapping as the specified entry.
      Parameters:
      `orig` - the entry to copy

  <!-- -->

  - ### Method Detail

    - #### setP

          public void setP(P p)

    <!-- -->

    - #### getP

          public P getP()

    <!-- -->

    - #### setQ

          public void setQ(Q q)

    <!-- -->

    - #### getQ

          public Q getQ()

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object o)

      Compares the specified object with this entry for equality. Returns `true` if the given object is also a Pair and the two entries represent the same Pair.
      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `o` - object to be compared for equality with this map entry

      Returns:
      `true` if the specified object is equal to this map entry

      See Also:
      `hashCode()`

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Returns a String representation of this map entry. This implementation returns the string representation of this entry's key followed by the equals character ("`=`") followed by the string representation of this entry's value.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      a String representation of this map entry

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

- [Prev Class](OpsJGeometry.md)
- [Next Class](RNode.md)

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
