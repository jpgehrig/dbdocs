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

- [Prev Class](FeatureLayerMetadata.md)
- [Next Class](FeatureMetadata.md)

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

## Enum FeatureLayerMetadata.FeatureLayerType

- java.lang.Object

- - java.lang.Enum\<FeatureLayerMetadata.FeatureLayerType\>

  - - oracle.spatial.network.lod.FeatureLayerMetadata.FeatureLayerType

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<FeatureLayerMetadata.FeatureLayerType\>

  <!-- -->

  Enclosing class:
  [FeatureLayerMetadata](FeatureLayerMetadata.md)

  ------------------------------------------------------------------------



      public static enum FeatureLayerMetadata.FeatureLayerType
      extends java.lang.Enum<FeatureLayerMetadata.FeatureLayerType>

  A list of valid feature layer types.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `COLLECTION`<br>This is the most generic feature layer type.                                                                                                     |
    | `LINE`<br>If all features in this feature layer are of type LINE.                                                                                                |
    | `MULTI_LINE`<br>If all features in this feature layer are of type LINE or MULTI_LINE.                                                                            |
    | `MULTI_POINT`<br>If all features in this feature layer are of type POINT_ON_NODE, POINT_ON_LINK, POINT MULTI_POINT_ON_NODE, MULTI_POINT_ON_LINK, or MULTI_POINT. |
    | `MULTI_POINT_ON_LINK`<br>If all features in this feature layer are of type POINT_ON_LINK or MULTI_POINT_ON_LINK.                                                 |
    | `MULTI_POINT_ON_NODE`<br>If all features in this feature layer are of type POINT_ON_NODE or MULTI_POINT_ON_NODE.                                                 |
    | `POINT`<br>If all features in this feature layer are of type POINT_ON_NODE, POINT_ON_LINK, or POINT.                                                             |
    | `POINT_ON_LINK`<br>If all features in this feature layer are of type POINT_ON_LINK.                                                                              |
    | `POINT_ON_NODE`<br>If all features in this feature layer are of type POINT_ON_NODE.                                                                              |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                       |
    |--------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static FeatureLayerMetadata.FeatureLayerType`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static FeatureLayerMetadata.FeatureLayerType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### POINT_ON_NODE

          public static final FeatureLayerMetadata.FeatureLayerType POINT_ON_NODE

      If all features in this feature layer are of type POINT_ON_NODE.

    <!-- -->

    - #### POINT_ON_LINK

          public static final FeatureLayerMetadata.FeatureLayerType POINT_ON_LINK

      If all features in this feature layer are of type POINT_ON_LINK.

    <!-- -->

    - #### POINT

          public static final FeatureLayerMetadata.FeatureLayerType POINT

      If all features in this feature layer are of type POINT_ON_NODE, POINT_ON_LINK, or POINT.

    <!-- -->

    - #### LINE

          public static final FeatureLayerMetadata.FeatureLayerType LINE

      If all features in this feature layer are of type LINE.

    <!-- -->

    - #### MULTI_POINT_ON_NODE

          public static final FeatureLayerMetadata.FeatureLayerType MULTI_POINT_ON_NODE

      If all features in this feature layer are of type POINT_ON_NODE or MULTI_POINT_ON_NODE.

    <!-- -->

    - #### MULTI_POINT_ON_LINK

          public static final FeatureLayerMetadata.FeatureLayerType MULTI_POINT_ON_LINK

      If all features in this feature layer are of type POINT_ON_LINK or MULTI_POINT_ON_LINK.

    <!-- -->

    - #### MULTI_POINT

          public static final FeatureLayerMetadata.FeatureLayerType MULTI_POINT

      If all features in this feature layer are of type POINT_ON_NODE, POINT_ON_LINK, POINT MULTI_POINT_ON_NODE, MULTI_POINT_ON_LINK, or MULTI_POINT.

    <!-- -->

    - #### MULTI_LINE

          public static final FeatureLayerMetadata.FeatureLayerType MULTI_LINE

      If all features in this feature layer are of type LINE or MULTI_LINE.

    <!-- -->

    - #### COLLECTION

          public static final FeatureLayerMetadata.FeatureLayerType COLLECTION

      This is the most generic feature layer type. It can be used to represent feature layers containing any feature types.

  <!-- -->

  - ### Method Detail

    - #### values

          public static FeatureLayerMetadata.FeatureLayerType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (FeatureLayerMetadata.FeatureLayerType c : FeatureLayerMetadata.FeatureLayerType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static FeatureLayerMetadata.FeatureLayerType valueOf(java.lang.String name)

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

- [Prev Class](FeatureLayerMetadata.md)
- [Next Class](FeatureMetadata.md)

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
