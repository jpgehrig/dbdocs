Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEFeatureLayerMetadata.md)
- [Next Class](NFEPredefinedConnectedPoint.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.feature

## Enum NFEFeatureShape

- java.lang.Object

- - java.lang.Enum\<NFEFeatureShape\>

  - - oracle.spatial.network.nfe.model.feature.NFEFeatureShape

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<NFEFeatureShape\>

  ------------------------------------------------------------------------



      public enum NFEFeatureShape
      extends java.lang.Enum<NFEFeatureShape>

  Defines the shape types supported by Feature Classes

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `COMPLEX_LINE`                |
    | `LINE`                        |
    | `PATH`                        |
    | `POINT`                       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type          | Method and Description                                                                                       |
    |----------------------------|--------------------------------------------------------------------------------------------------------------|
    | `int`                      | `getValue``()`<br>Gets the numeric value of the shape type                                                   |
    | `java.lang.String`         | `toString``()`                                                                                               |
    | `static NFEFeatureShape`   | `valueOf``(int featureShapeValue)`<br>Gets a shape type based on a numeric type.                             |
    | `static NFEFeatureShape`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static NFEFeatureShape[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### POINT

          public static final NFEFeatureShape POINT

    <!-- -->

    - #### LINE

          public static final NFEFeatureShape LINE

    <!-- -->

    - #### COMPLEX_LINE

          public static final NFEFeatureShape COMPLEX_LINE

    <!-- -->

    - #### PATH

          public static final NFEFeatureShape PATH

  <!-- -->

  - ### Method Detail

    - #### values

          public static NFEFeatureShape[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (NFEFeatureShape c : NFEFeatureShape.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static NFEFeatureShape valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Enum<NFEFeatureShape>`

    <!-- -->

    - #### valueOf

          public static NFEFeatureShape valueOf(int featureShapeValue)

      Gets a shape type based on a numeric type.
      Parameters:
      `featureShapeValue` - a numeric value representing a shape type. The possible values are: Point=1, LINE=2, COMPLEX_LINE=3, PATH=4

      Returns:
      a shape type or null if the numeric value does not have a correspondence

    <!-- -->

    - #### getValue

          public int getValue()

      Gets the numeric value of the shape type
      Returns:
      a numeric value

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEFeatureLayerMetadata.md)
- [Next Class](NFEPredefinedConnectedPoint.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
