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

- [Prev Class](UserDataImpl.md)
- [Next Class](VRP.md)

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

## Class VisitedNode

- java.lang.Object

- - oracle.spatial.network.lod.VisitedNode

<!-- -->

- All Implemented Interfaces:
  java.lang.Comparable, [Identifiable](Identifiable.md)

  ------------------------------------------------------------------------



      public abstract class VisitedNode
      extends java.lang.Object
      implements Identifiable, java.lang.Comparable

  This class represents a node visited while exploring a network.
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `VisitedNode``()`           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type   | Method and Description                                                                                                                  |
    |---------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
    | `int`               | `compareTo``(java.lang.Object o)`                                                                                                       |
    | `boolean`           | `equals``(java.lang.Object o)`                                                                                                          |
    | `abstract double[]` | `getCosts``()`<br>Return the costs from the start points to the node.                                                                   |
    | `abstract double[]` | `getCostsAtPrevNode``()`<br>Returns the costs to pass through the previous node.                                                        |
    | `int`               | `getDepth``()`<br>Returns the depth of the current node, which is equal to the number of links from the start node to the current node. |
    | `long`              | `getId``()`<br>Returns the ID of the node.                                                                                              |
    | `int`               | `getLinkLevel``()`<br>Returns the link level the node is to be expanded on.                                                             |
    | `int`               | `getPartitionId``()`<br>Returns the ID of the partition that the node is assigned to.                                                   |
    | `long`              | `getPrevLink``()`<br>Returns the ID of the previous link.                                                                               |
    | `VisitedNode`       | `getPrevNode``()`<br>Returns the previous node.                                                                                         |
    | `java.lang.Object`  | `getUserObject``()`<br>Returns the user object associated to this node.                                                                 |
    | `int`               | `hashCode``()`                                                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### VisitedNode

          public VisitedNode()

  <!-- -->

  - ### Method Detail

    - #### compareTo

          public int compareTo(java.lang.Object o)

      Specified by:
      `compareTo` in interface `java.lang.Comparable`

    <!-- -->

    - #### getId

          public long getId()

      Returns the ID of the node.
      Specified by:

      [`getId`](Identifiable.md) in interface [`Identifiable`](Identifiable.md)

      Returns:

    <!-- -->

    - #### getPartitionId

          public int getPartitionId()

      Returns the ID of the partition that the node is assigned to.
      Returns:

    <!-- -->

    - #### getCosts

          public abstract double[] getCosts()

      Return the costs from the start points to the node.
      Returns:

    <!-- -->

    - #### getCostsAtPrevNode

          public abstract double[] getCostsAtPrevNode()

      Returns the costs to pass through the previous node.
      Returns:

    <!-- -->

    - #### getPrevLink

          public long getPrevLink()

      Returns the ID of the previous link.
      Returns:

    <!-- -->

    - #### getPrevNode

          public VisitedNode getPrevNode()

      Returns the previous node.
      Returns:

    <!-- -->

    - #### getDepth

          public int getDepth()

      Returns the depth of the current node, which is equal to the number of links from the start node to the current node. The depth of the start node is 0.
      Returns:

    <!-- -->

    - #### getLinkLevel

          public int getLinkLevel()

      Returns the link level the node is to be expanded on.
      Returns:

    <!-- -->

    - #### getUserObject

          public java.lang.Object getUserObject()

      Returns the user object associated to this node.
      Returns:

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object o)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

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

- [Prev Class](UserDataImpl.md)
- [Next Class](VRP.md)

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
