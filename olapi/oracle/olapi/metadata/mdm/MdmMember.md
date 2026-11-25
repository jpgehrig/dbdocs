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

- [Prev Class](MdmMeasureModel.md)
- [Next Class](MdmMemberListMapOwner.md)

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

## Interface MdmMember

- All Known Implementing Classes:
  [MdmBaseMeasure](MdmBaseMeasure.md), [MdmDerivedMeasure](MdmDerivedMeasure.md), [MdmMeasure](MdmMeasure.md), [MdmStandardMember](MdmStandardMember.md), [MdmTimeMember](MdmTimeMember.md)

  ------------------------------------------------------------------------



      public interface MdmMember

  An interface for a custom member of an `MdmPrimaryDimension`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                             | Method and Description                                                                                                       |
    |-------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
    | [`FundamentalMetadataObject`](../../data/source/FundamentalMetadataObject.md) | `getDataType``()`<br>Gets the data type of the `MdmMember`.                                                                  |
    | `java.lang.String`                                                            | `getDescription``()`<br>Gets the description of the `MdmMember`.                                                             |
    | [`MdmLevel`](MdmLevel.md)                                                     | `getLevel``()`<br>Gets the `MdmLevel` of which the `MdmMember` is a member.                                                  |
    | `int`                                                                         | `getLevelDepth``()`<br>Gets the depth in the hierarchy of the level of which the `MdmMember` is a member.                    |
    | `java.lang.String`                                                            | `getLocalValue``()`<br>Gets the local value of the `MdmMember`.                                                              |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md)                               | `getOwnerDimension``()`<br>Gets the `MdmPrimaryDimension` of which the `MdmMember` is a member.                              |
    | [`MdmLevel`](MdmLevel.md)                                                     | `getParentLevel``()`<br>Gets the `MdmLevel` of which the parent of the `MdmMember` is a member.                              |
    | `java.lang.String`                                                            | `getParentLocalValue``()`<br>Gets the local value of the parent of the `MdmMember`.                                          |
    | `java.lang.String`                                                            | `getParentValue``()`<br>Gets the unique value of the parent of the `MdmMember`.                                              |
    | `int`                                                                         | `getPrecedence``()`<br>Gets the precedence of the `MdmMember`, with the higher integer value indicating a higher precedence. |
    | `java.lang.String`                                                            | `getShortDescription``()`<br>Gets the short description of the `MdmMember`.                                                  |
    | [`Source`](../../data/source/Source.md)                                       | `getSource``()`<br>Gets the `Source` for the `MdmMember`.                                                                    |
    | `java.lang.String`                                                            | `getValue``()`<br>Gets the unique value of the `MdmMember`.                                                                  |

<!-- -->

- - ### Method Detail

    - #### getOwnerDimension

          MdmPrimaryDimension getOwnerDimension()

      Gets the `MdmPrimaryDimension` of which the `MdmMember` is a member.
      Returns:
      The `MdmPrimaryDimension` of which the `MdmMember` is a member.

    <!-- -->

    - #### getValue

          java.lang.String getValue()

      Gets the unique value of the `MdmMember`.
      Returns:
      A `String` that contains the unique value of the `MdmMember`.

    <!-- -->

    - #### getLocalValue

          java.lang.String getLocalValue()

      Gets the local value of the `MdmMember`.
      Returns:
      A `String` that contains the local value of the `MdmMember`.

    <!-- -->

    - #### getLevel

          MdmLevel getLevel()

      Gets the `MdmLevel` of which the `MdmMember` is a member.
      Returns:
      The `MdmLevel` of which the `MdmMember` is a member.

    <!-- -->

    - #### getLevelDepth

          int getLevelDepth()

      Gets the depth in the hierarchy of the level of which the `MdmMember` is a member.
      Returns:
      An integer that identifies the depth in the hierarchy of the level of which the `MdmMember` is a member.

    <!-- -->

    - #### getParentValue

          java.lang.String getParentValue()

      Gets the unique value of the parent of the `MdmMember`.
      Returns:
      A `String` that contains the unique value of the parent of the `MdmMember`.

    <!-- -->

    - #### getParentLocalValue

          java.lang.String getParentLocalValue()

      Gets the local value of the parent of the `MdmMember`.
      Returns:
      A `String` that contains the local value of the parent of the `MdmMember`.

    <!-- -->

    - #### getParentLevel

          MdmLevel getParentLevel()

      Gets the `MdmLevel` of which the parent of the `MdmMember` is a member.
      Returns:
      The `MdmLevel` of which the parent of the `MdmMember` is a member.

    <!-- -->

    - #### getDescription

          java.lang.String getDescription()

      Gets the description of the `MdmMember`.
      Returns:
      A `String` that contains the description of the `MdmMember`.

    <!-- -->

    - #### getShortDescription

          java.lang.String getShortDescription()

      Gets the short description of the `MdmMember`.
      Returns:
      A `String` that contains the short description of the `MdmMember`.

    <!-- -->

    - #### getSource

          Source getSource()

      Gets the `Source` for the `MdmMember`.
      Returns:
      The `Source` for the `MdmMember`.

    <!-- -->

    - #### getDataType

          FundamentalMetadataObject getDataType()

      Gets the data type of the `MdmMember`.
      Returns:
      The `FundamentalMetadataObject` that represents the data type of the `MdmMember`.

    <!-- -->

    - #### getPrecedence

          int getPrecedence()

      Gets the precedence of the `MdmMember`, with the higher integer value indicating a higher precedence. When you create a custom member of a dimension, you specify a precedence. Oracle OLAP creates an `Assignment` for the appropriate `MdmModel` and gives the `Assignment` the precedence you specify for the custom member. Oracle OLAP uses the precedence value in determining the order in which it evaluates the `Assignment` objects of the `MdmModel`. Oracle OLAP uses the precedence value in determining the order in which it evaluates the `Assignment` objects of an `MdmModel`.
      Returns:
      An integer that specifies the precedence of the `MdmMember`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMeasureModel.md)
- [Next Class](MdmMemberListMapOwner.md)

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
