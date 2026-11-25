Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](MdmDescription.md)
- [Next Class](MdmDimension.md)

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

oracle.olapi.metadata.mdm

## Class MdmDescriptionType

- java.lang.Object

- - oracle.olapi.metadata.mdm.MdmDescriptionType

<!-- -->

-

  ------------------------------------------------------------------------



      public class MdmDescriptionType
      extends java.lang.Object

  Represents a type of description for an `MdmDescription`. Static methods of this class return standard types of descriptions such as name, plural name, description, long description, and others. An application can create other types of descriptions by constructing new `MdmDescriptionType` objects.
  An application specifies an `MdmDescriptionType` when calling the [`findOrCreateDescription`](MdmObject.md) method of an `MdmObject`, which returns an `MdmDescription`.

  See Also:
  [`MdmDescription`](MdmDescription.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                         |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `MdmDescriptionType``(java.lang.String type)`<br>Creates a new `MdmDescriptionType` of the specified type.                                                                          |
    | `MdmDescriptionType``(java.lang.String type, MdmDescriptionType defaultType)`<br>Creates a new `MdmDescriptionType` of the specified type and specifies a default description type. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                 |
    |-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static MdmDescriptionType` | `getDescriptionDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a description to associate with an `MdmObject`.            |
    | `java.lang.String`          | `getDescriptiveType``()`<br>Gets the description type of this `MdmDescriptionType`.                                                                                    |
    | `MdmDescriptionType`        | `getDescriptiveTypeDefault``()`<br>Gets the default description type associated with this `MdmDescriptionType`.                                                        |
    | `static MdmDescriptionType` | `getLongDescriptionDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a long description to associate with an `MdmObject`.   |
    | `static MdmDescriptionType` | `getLongNameDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a long version of a name to associate with an `MdmObject`.    |
    | `static MdmDescriptionType` | `getLongPluralNameDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a long plural name to associate with an `MdmObject`.    |
    | `static MdmDescriptionType` | `getNameDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a name to associate with an `MdmObject`.                          |
    | `static MdmDescriptionType` | `getPluralNameDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a plural name to associate with an `MdmObject`.             |
    | `static MdmDescriptionType` | `getShortDescriptionDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a short description to associate with an `MdmObject`. |
    | `static MdmDescriptionType` | `getShortNameDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a short version of a name to associate with an `MdmObject`.  |
    | `static MdmDescriptionType` | `getShortPluralNameDescriptionType``()`<br>Gets an `MdmDescriptionType` for an `MdmDescription` that represents a short plural name to associate with an `MdmObject`.  |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### MdmDescriptionType

          public MdmDescriptionType(java.lang.String type)

      Creates a new `MdmDescriptionType` of the specified type.
      Parameters:
      `type` - A `String` that specifies the type of the new `MdmDescriptionType`.

    <!-- -->

    - #### MdmDescriptionType

          public MdmDescriptionType(java.lang.String type,
                                    MdmDescriptionType defaultType)

      Creates a new `MdmDescriptionType` of the specified type and specifies a default description type.
      Parameters:
      `type` - A `String` that specifies the type of the new `MdmDescriptionType`.

      `defaultType` - The `MdmDescriptionType` to use as the default type.

  <!-- -->

  - ### Method Detail

    - #### getDescriptiveTypeDefault

          public final MdmDescriptionType getDescriptiveTypeDefault()

      Gets the default description type associated with this `MdmDescriptionType`.
      Returns:
      An `MdmDescriptionType` that is the default type specified for this `MdmDescriptionType`.

    <!-- -->

    - #### getDescriptiveType

          public final java.lang.String getDescriptiveType()

      Gets the description type of this `MdmDescriptionType`.
      Returns:
      A `String` that contains the name of the type of description that this `MdmDescriptionType` represents.

    <!-- -->

    - #### getNameDescriptionType

          public static MdmDescriptionType getNameDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a name to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a name.

    <!-- -->

    - #### getShortNameDescriptionType

          public static MdmDescriptionType getShortNameDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a short version of a name to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a short name.

    <!-- -->

    - #### getLongNameDescriptionType

          public static MdmDescriptionType getLongNameDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a long version of a name to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a long name.

    <!-- -->

    - #### getShortPluralNameDescriptionType

          public static MdmDescriptionType getShortPluralNameDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a short plural name to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a short plural name.

    <!-- -->

    - #### getPluralNameDescriptionType

          public static MdmDescriptionType getPluralNameDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a plural name to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a plural name.

    <!-- -->

    - #### getLongPluralNameDescriptionType

          public static MdmDescriptionType getLongPluralNameDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a long plural name to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a long plural name.

    <!-- -->

    - #### getDescriptionDescriptionType

          public static MdmDescriptionType getDescriptionDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a description to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a description.

    <!-- -->

    - #### getShortDescriptionDescriptionType

          public static MdmDescriptionType getShortDescriptionDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a short description to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a short description.

    <!-- -->

    - #### getLongDescriptionDescriptionType

          public static MdmDescriptionType getLongDescriptionDescriptionType()

      Gets an `MdmDescriptionType` for an `MdmDescription` that represents a long description to associate with an `MdmObject`.
      Returns:
      An `MdmDescriptionType` for an `MdmDescription` that represents a long description.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDescription.md)
- [Next Class](MdmDimension.md)

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
