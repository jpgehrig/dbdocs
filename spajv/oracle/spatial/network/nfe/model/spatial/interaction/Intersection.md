Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](BinaryInteraction.md)
- [Next Class](IntersectionLocation.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.spatial.interaction

## Class Intersection\<V\>

- java.lang.Object

- - oracle.spatial.network.nfe.model.spatial.interaction.Intersection\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of elements in the intersection

  <!-- -->

  All Implemented Interfaces:
  java.lang.Cloneable

  ------------------------------------------------------------------------



      public class Intersection<V>
      extends java.lang.Object
      implements java.lang.Cloneable

  Represents an intersection between two or more elements.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                          |
    |------------------------------------------------------------------------------------------------------|
    | `Intersection``(java.awt.geom.Point2D interPoint, double tolerance)`<br>Allocates a new intersection |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                          | Method and Description                                                                                                                                    |
    |----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                     | `addMember``(`[`IntersectionMember`](IntersectionMember.md)`<V> member)`<br>Adds a member to the intersection                                             |
    | `java.lang.Object`                                                         | `clone``()`                                                                                                                                               |
    | `boolean`                                                                  | `containsMember``(`[`IntersectionMember`](IntersectionMember.md)`<V> member)`<br>Tells whether an intersection member belongs to the current intersection |
    | `long`                                                                     | `getId``()`<br>Gets the intersection ID                                                                                                                   |
    | `java.awt.geom.Point2D`                                                    | `getIntersectionPoint``()`<br>Gets the spatial point where the intersection occurred                                                                      |
    | [`IntersectionMember`](IntersectionMember.md)`<V>`                         | `getMember``(long memId)`<br>Gets a member identified by the given ID                                                                                     |
    | `java.util.Collection<`[`IntersectionMember`](IntersectionMember.md)`<V>>` | `getMembers``()`<br>Gets all the members of the intersection                                                                                              |
    | `java.util.Collection<`[`IntersectionMember`](IntersectionMember.md)`<V>>` | `getMembers``(int geomType)`<br>Gets all the members with the given geometry type                                                                         |
    | `int`                                                                      | `getMembersCount``()`<br>Gets the number of elements participating in the intersection                                                                    |
    | [`IntersectionMember`](IntersectionMember.md)`<V>`                         | `getOwner``()`<br>Gets the member marked as intersection owner (if any)                                                                                   |
    | `double`                                                                   | `getTolerance``()`<br>Gets the tolerance used to detect the intersection                                                                                  |
    | `boolean`                                                                  | `isOwner``(`[`IntersectionMember`](IntersectionMember.md)`<V> member)`<br>Tells whether the given member is owner of the intersection.                    |
    | `void`                                                                     | `markAsOwner``(`[`IntersectionMember`](IntersectionMember.md)`<V> member)`<br>Sets the given member as the owner of the intersection.                     |
    | [`IntersectionMember`](IntersectionMember.md)`<V>`                         | `pickFirstMember``(int geomType)`<br>Gets the first member found with the given geometry type                                                             |
    | `void`                                                                     | `removeMember``(`[`IntersectionMember`](IntersectionMember.md)`<V> member)`<br>Removes an intersection member                                             |
    | `void`                                                                     | `setIntersectionPoint``(java.awt.geom.Point2D interPoint)`<br>Sets the spatial point where the intersection occurred                                      |
    | `void`                                                                     | `setTolerance``(double tolerance)`<br>Sets the tolerance used to detect the intersection                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Intersection

          public Intersection(java.awt.geom.Point2D interPoint,
                              double tolerance)

      Allocates a new intersection
      Parameters:
      `interPoint` - the spatial point where the intersection happened

      `tolerance` - tolerance used to detect all the elements involved in the interaction

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Gets the intersection ID
      Returns:
      the intersection ID

    <!-- -->

    - #### getMembersCount

          public int getMembersCount()

      Gets the number of elements participating in the intersection
      Returns:
      the number of elements in the intersection

    <!-- -->

    - #### addMember

          public void addMember(IntersectionMember<V> member)

      Adds a member to the intersection
      Parameters:
      `member` - an intersection member

    <!-- -->

    - #### removeMember

          public void removeMember(IntersectionMember<V> member)

      Removes an intersection member
      Parameters:
      `member` - an intersection member

    <!-- -->

    - #### containsMember

          public boolean containsMember(IntersectionMember<V> member)

      Tells whether an intersection member belongs to the current intersection
      Parameters:
      `member` - an intersection member

      Returns:
      true if it is a member of the intersection

    <!-- -->

    - #### getMembers

          public java.util.Collection<IntersectionMember<V>> getMembers()

      Gets all the members of the intersection
      Returns:
      a collection of intersection members

    <!-- -->

    - #### markAsOwner

          public void markAsOwner(IntersectionMember<V> member)

      Sets the given member as the owner of the intersection. An intersection may not have an owner. An owner can be the element that creates the interaction, for example, an element that was added or that was moved.
      Parameters:
      `member` - a member of the intersection

    <!-- -->

    - #### isOwner

          public boolean isOwner(IntersectionMember<V> member)

      Tells whether the given member is owner of the intersection.
      Parameters:
      `member` - a member of the intersection

      Returns:
      true if the element is the owner

    <!-- -->

    - #### getOwner

          public IntersectionMember<V> getOwner()

      Gets the member marked as intersection owner (if any)
      Returns:
      an intersection member or null if the intersection has not owner member

    <!-- -->

    - #### getIntersectionPoint

          public java.awt.geom.Point2D getIntersectionPoint()

      Gets the spatial point where the intersection occurred
      Returns:
      a java point

    <!-- -->

    - #### setIntersectionPoint

          public void setIntersectionPoint(java.awt.geom.Point2D interPoint)

      Sets the spatial point where the intersection occurred
      Parameters:
      `interPoint` - a java point

    <!-- -->

    - #### pickFirstMember

          public IntersectionMember<V> pickFirstMember(int geomType)

      Gets the first member found with the given geometry type
      Parameters:
      `geomType` - a geometry type

      Returns:
      the first member found or null if no members were found

    <!-- -->

    - #### getMembers

          public java.util.Collection<IntersectionMember<V>> getMembers(int geomType)

      Gets all the members with the given geometry type
      Parameters:
      `geomType` - a geometry type

      Returns:
      a collection of intersection members

    <!-- -->

    - #### getMember

          public IntersectionMember<V> getMember(long memId)

      Gets a member identified by the given ID
      Parameters:
      `memId` - an intersection member ID

      Returns:
      an intersection member of null if the member was not found

    <!-- -->

    - #### getTolerance

          public double getTolerance()

      Gets the tolerance used to detect the intersection
      Returns:
      a tolerance value

    <!-- -->

    - #### setTolerance

          public void setTolerance(double tolerance)

      Sets the tolerance used to detect the intersection
      Parameters:
      `tolerance` - a tolerance value

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Overrides:
      `clone` in class `java.lang.Object`

      Throws:
      `java.lang.CloneNotSupportedException`

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](BinaryInteraction.md)
- [Next Class](IntersectionLocation.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
