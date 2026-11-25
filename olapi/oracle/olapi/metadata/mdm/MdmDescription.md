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

- [Prev Class](MdmDerivedMeasure.md)
- [Next Class](MdmDescriptionType.md)

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

## Class MdmDescription

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - oracle.olapi.metadata.mdm.MdmDescription

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MdmDescription
      extends BaseMetadataObject

  A `BaseMetadataObject` that represents a description for an `MdmObject`. The Oracle OLAP Java API provides various types of descriptions, which are represented by instances of the `MdmDescriptionType` class. That class has static methods that return objects that represent a type of description, such as a name, a long name, a description, a short description, and others. An application can add to the available types of description by defining a new `MdmDescriptionType`.
  To find or create an `MdmDescription`, use the `findOrCreateDescription` method of an `MdmObject`. See the `getType` method for an example.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                 |
    |-----------------------------|----------------------------------------------------------------------------------------|
    | [`MdmObject`](MdmObject.md) | `getDescribedObject``()`<br>Gets the `MdmObject` that this `MdmDescription` describes. |
    | `java.lang.String`          | `getLanguage``()`<br>Gets the language that is associated with this `MdmDescription`.  |
    | `java.lang.String`          | `getName``()`<br>Gets the name of this `MetadataObject`.                               |
    | `java.lang.String`          | `getType``()`<br>Gets the type of description that this `MdmDescription` represents.   |
    | `java.lang.String`          | `getValue``()`<br>Gets the value that of this `MdmDescription`.                        |
    | `void`                      | `setValue``(java.lang.String value)`<br>Specifies the value of this `MdmDescription`.  |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getType

          public final java.lang.String getType()

      Gets the type of description that this `MdmDescription` represents. For example, the following code gets the type of an `MdmDescription` for `mdmStdDim`, which is an `MdmStandardDimension`.
           MdmDescription mdmDescr =
                mdmStdDim.findOrCreateDescription(
                                    MdmDescriptionType.getShortNameDescriptionType(),
                                    "AMERICAN",
                                    "MyDim");
           String type =  mdmDescr.getType();
           System.out.println("The type of the MdmDescription is " + type + ".");

      The output of the example is the following.
           The type of the MdmDescription is ShortName.

      Returns:
      A `String` that contains the type of description of this `MdmDescription`.

    <!-- -->

    - #### getLanguage

          public final java.lang.String getLanguage()

      Gets the language that is associated with this `MdmDescription`.
      Returns:
      A `String` that identifies the language associated with this `MdmDescription`.

    <!-- -->

    - #### getValue

          public final java.lang.String getValue()

      Gets the value that of this `MdmDescription`.
      Returns:
      A `String` that is the value of this `MdmDescription`.

    <!-- -->

    - #### setValue

          public final void setValue(java.lang.String value)

      Specifies the value of this `MdmDescription`.
      Parameters:
      `value` - A `String` that specifies the value for this `MdmDescription`.

    <!-- -->

    - #### getDescribedObject

          public final MdmObject getDescribedObject()

      Gets the `MdmObject` that this `MdmDescription` describes.
      Returns:
      The `MdmObject` that owns this `MdmDescription`.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of this `MetadataObject`.
      Overrides:
      [`getName`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      A `String` that contains the name of this `MetadataObject`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDerivedMeasure.md)
- [Next Class](MdmDescriptionType.md)

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
