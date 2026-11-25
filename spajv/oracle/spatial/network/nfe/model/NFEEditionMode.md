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

- [Prev Class](NFEDBSequenceIdManager.md)
- [Next Class](NFEGeometryDescriptor.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model

## Enum NFEEditionMode

- java.lang.Object

- - java.lang.Enum\<NFEEditionMode\>

  - - oracle.spatial.network.nfe.model.NFEEditionMode

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<NFEEditionMode\>

  ------------------------------------------------------------------------



      public enum NFEEditionMode
      extends java.lang.Enum<NFEEditionMode>

  Defines values for the different edition modes supported by NFE

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                       |
    |-------------------------------------------------------------------------------------|
    | `FEATURES_FROM_SCRATCH`<br>Represents the FromScratch edition mode                  |
    | `FEATURES_OVER_EXISTING_NETWORK`<br>Represents the OverExistingNetwork edition mode |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                       |
    |---------------------------|--------------------------------------------------------------------------------------------------------------|
    | `int`                     | `getValue``()`<br>Gets the ordinal value of the current enum value                                           |
    | `java.lang.String`        | `toString``()`                                                                                               |
    | `static NFEEditionMode`   | `valueOf``(int editionModeValue)`<br>Gets an enum value corresponding to the given ordinal                   |
    | `static NFEEditionMode`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static NFEEditionMode[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### FEATURES_FROM_SCRATCH

          public static final NFEEditionMode FEATURES_FROM_SCRATCH

      Represents the FromScratch edition mode

    <!-- -->

    - #### FEATURES_OVER_EXISTING_NETWORK

          public static final NFEEditionMode FEATURES_OVER_EXISTING_NETWORK

      Represents the OverExistingNetwork edition mode

  <!-- -->

  - ### Method Detail

    - #### values

          public static NFEEditionMode[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (NFEEditionMode c : NFEEditionMode.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static NFEEditionMode valueOf(java.lang.String name)

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
      `toString` in class `java.lang.Enum<NFEEditionMode>`

    <!-- -->

    - #### getValue

          public int getValue()

      Gets the ordinal value of the current enum value
      Returns:

    <!-- -->

    - #### valueOf

          public static NFEEditionMode valueOf(int editionModeValue)

      Gets an enum value corresponding to the given ordinal
      Parameters:
      `editionModeValue` - an ordinal that corresponds to an enum value

      Returns:
      an enum value or null the ordinal does not corresponds to any enum value

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

- [Prev Class](NFEDBSequenceIdManager.md)
- [Next Class](NFEGeometryDescriptor.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
