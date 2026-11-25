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

- [Prev Class](NFEAttributeDescriptor.md)
- [Next Class](NFEBasicAttributeConstraint.md)

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

## Enum NFEAttributeType

- java.lang.Object

- - java.lang.Enum\<NFEAttributeType\>

  - - oracle.spatial.network.nfe.model.feature.NFEAttributeType

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<NFEAttributeType\>

  ------------------------------------------------------------------------



      public enum NFEAttributeType
      extends java.lang.Enum<NFEAttributeType>

  Possible types of a feature layer's attribute

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `DATE`                        |
    | `INTEGER`                     |
    | `NUMBER`                      |
    | `SDO_GEOMETRY`                |
    | `TIMESTAMP`                   |
    | `VARCHAR2`                    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                        |
    |-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Class<?>`        | `getTypeClass``()`<br>Gets the Java Class that corresponds to the current type                                                                                |
    | `java.lang.Object`          | `parseJavaValue``(java.lang.String strValue)`<br>Gets the representation of the string parameter as the appropriate Java Class instance for the current type. |
    | `static NFEAttributeType`   | `parseString``(java.lang.String typeStr)`<br>Given an attribute type name, it returns the actual NFEAttributeType for that name.                              |
    | `java.lang.String`          | `toString``()`                                                                                                                                                |
    | `static NFEAttributeType`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.                                                         |
    | `static NFEAttributeType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                  |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### NUMBER

          public static final NFEAttributeType NUMBER

    <!-- -->

    - #### INTEGER

          public static final NFEAttributeType INTEGER

    <!-- -->

    - #### VARCHAR2

          public static final NFEAttributeType VARCHAR2

    <!-- -->

    - #### DATE

          public static final NFEAttributeType DATE

    <!-- -->

    - #### TIMESTAMP

          public static final NFEAttributeType TIMESTAMP

    <!-- -->

    - #### SDO_GEOMETRY

          public static final NFEAttributeType SDO_GEOMETRY

  <!-- -->

  - ### Method Detail

    - #### values

          public static NFEAttributeType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (NFEAttributeType c : NFEAttributeType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static NFEAttributeType valueOf(java.lang.String name)

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
      `toString` in class `java.lang.Enum<NFEAttributeType>`

    <!-- -->

    - #### parseJavaValue

          public java.lang.Object parseJavaValue(java.lang.String strValue)

      Gets the representation of the string parameter as the appropriate Java Class instance for the current type. If it is not possible to represent the string as the current type, null is returned.
      Parameters:
      `strValue` - a string value

      Returns:
      the Object equivalent of the string value or null if it cannot be represented by the current type

    <!-- -->

    - #### parseString

          public static NFEAttributeType parseString(java.lang.String typeStr)

      Given an attribute type name, it returns the actual NFEAttributeType for that name.
      Parameters:
      `typeStr` - an attribute type name. It is the same that the name of the current enumeration values and is not sensible to the case.

      Returns:
      an NFEAttributeType value or null if it does not match any value number.

    <!-- -->

    - #### getTypeClass

          public java.lang.Class<?> getTypeClass()

      Gets the Java Class that corresponds to the current type
      Returns:
      a Java Class

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

- [Prev Class](NFEAttributeDescriptor.md)
- [Next Class](NFEBasicAttributeConstraint.md)

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
