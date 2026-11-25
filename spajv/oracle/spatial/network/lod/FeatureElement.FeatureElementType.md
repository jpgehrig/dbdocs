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

- [Prev Class](FeatureElement.md)
- [Next Class](FeatureElementImpl.md)

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

## Enum FeatureElement.FeatureElementType

- java.lang.Object

- - java.lang.Enum\<FeatureElement.FeatureElementType\>

  - - oracle.spatial.network.lod.FeatureElement.FeatureElementType

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<FeatureElement.FeatureElementType\>

  <!-- -->

  Enclosing interface:
  [FeatureElement](FeatureElement.md)

  ------------------------------------------------------------------------



      public static enum FeatureElement.FeatureElementType
      extends java.lang.Enum<FeatureElement.FeatureElementType>

  A list of valid feature element types.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description         |
    |---------------------------------------|
    | `LINE`<br>Link or partial link        |
    | `POINT_ON_LINK`<br>Point along a link |
    | `POINT_ON_NODE`<br>Point on node      |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                       |
    |----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static FeatureElement.FeatureElementType`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static FeatureElement.FeatureElementType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### POINT_ON_NODE

          public static final FeatureElement.FeatureElementType POINT_ON_NODE

      Point on node

    <!-- -->

    - #### POINT_ON_LINK

          public static final FeatureElement.FeatureElementType POINT_ON_LINK

      Point along a link

    <!-- -->

    - #### LINE

          public static final FeatureElement.FeatureElementType LINE

      Link or partial link

  <!-- -->

  - ### Method Detail

    - #### values

          public static FeatureElement.FeatureElementType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (FeatureElement.FeatureElementType c : FeatureElement.FeatureElementType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static FeatureElement.FeatureElementType valueOf(java.lang.String name)

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

- [Prev Class](FeatureElement.md)
- [Next Class](FeatureElementImpl.md)

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
