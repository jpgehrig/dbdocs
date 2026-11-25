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

- [Prev Class](Feature.md)
- [Next Class](FeatureData.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

oracle.spatial.network.lod

## Enum Feature.FeatureType

- java.lang.Object

- - java.lang.Enum\<Feature.FeatureType\>

  - - oracle.spatial.network.lod.Feature.FeatureType

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<Feature.FeatureType\>

  <!-- -->

  Enclosing interface:
  [Feature](Feature.md)

  ------------------------------------------------------------------------



      public static enum Feature.FeatureType
      extends java.lang.Enum<Feature.FeatureType>

  A list of valid feature types.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                     |
    |-----------------------------------------------------------------------------------|
    | `COLLECTION`<br>For features that consist of one or more points or lines.         |
    | `LINE`<br>For features that consist of a single line (link or partial link).      |
    | `MULTI_LINE`<br>For features that consist of one or more lines.                   |
    | `MULTI_POINT`<br>For features that consist of one or more points.                 |
    | `MULTI_POINT_ON_LINK`<br>For features that consist of one or more points on link. |
    | `MULTI_POINT_ON_NODE`<br>For features that consist of one or more points on node. |
    | `POINT`<br>For features that consist of a single point.                           |
    | `POINT_ON_LINK`<br>For features that consist of a single point on link.           |
    | `POINT_ON_NODE`<br>For features that consist of a single point on node.           |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type              | Method and Description                                                                                       |
    |--------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static Feature.FeatureType`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static Feature.FeatureType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### POINT_ON_NODE

          public static final Feature.FeatureType POINT_ON_NODE

      For features that consist of a single point on node.

    <!-- -->

    - #### POINT_ON_LINK

          public static final Feature.FeatureType POINT_ON_LINK

      For features that consist of a single point on link.

    <!-- -->

    - #### POINT

          public static final Feature.FeatureType POINT

      For features that consist of a single point.

    <!-- -->

    - #### LINE

          public static final Feature.FeatureType LINE

      For features that consist of a single line (link or partial link).

    <!-- -->

    - #### MULTI_POINT_ON_NODE

          public static final Feature.FeatureType MULTI_POINT_ON_NODE

      For features that consist of one or more points on node.

    <!-- -->

    - #### MULTI_POINT_ON_LINK

          public static final Feature.FeatureType MULTI_POINT_ON_LINK

      For features that consist of one or more points on link.

    <!-- -->

    - #### MULTI_POINT

          public static final Feature.FeatureType MULTI_POINT

      For features that consist of one or more points.

    <!-- -->

    - #### MULTI_LINE

          public static final Feature.FeatureType MULTI_LINE

      For features that consist of one or more lines.

    <!-- -->

    - #### COLLECTION

          public static final Feature.FeatureType COLLECTION

      For features that consist of one or more points or lines.

  <!-- -->

  - ### Method Detail

    - #### values

          public static Feature.FeatureType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (Feature.FeatureType c : Feature.FeatureType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static Feature.FeatureType valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

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

- [Prev Class](Feature.md)
- [Next Class](FeatureData.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
