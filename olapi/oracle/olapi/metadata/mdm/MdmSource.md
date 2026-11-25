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

- [Prev Class](MdmSingleValuedAttribute.md)
- [Next Class](MdmStandardDimension.md)

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

## Class MdmSource

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - oracle.olapi.metadata.mdm.MdmSource

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmColumn](MdmColumn.md), [MdmDimension](MdmDimension.md), [MdmDimensionedObject](MdmDimensionedObject.md), [MdmStandardMember](MdmStandardMember.md), [MdmTable](MdmTable.md), [MdmTimeMember](MdmTimeMember.md)

  ------------------------------------------------------------------------



      public abstract class MdmSource
      extends MdmObject

  An `MdmObject` that represents a measure, dimension, or other set of data (such as an attribute). To retrieve the data values that an `MdmSource` represents, an application calls the `getSource` method of the `MdmSource`. The method returns a `Source` that an application can use to create queries on the data that the `MdmSource` represents.
  A `Source` returned by the `getSource` method of an `MdmSource` is a primary `Source`. An application creates a query by using a method of the primary `Source` to create a derived `Source` that specifies a selection of its elements, or a calculation or some other manipulation of the data.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                             | Method and Description                                                                                                                   |
    |-------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | [`FundamentalMetadataObject`](../../data/source/FundamentalMetadataObject.md) | `getDataType``()`<br>Gets the OLAP Java API data type of the `MdmSource`.                                                                |
    | [`Source`](../../data/source/Source.md)                                       | `getSource``()`<br>Gets the primary `Source` through which an application can create queries on the data represented by the `MdmSource`. |
    | `abstract `[`MetadataObject`](../MetadataObject.md)                           | `getType``()`<br>Gets the type of the `MdmSource`.                                                                                       |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`acceptVisitor`](MdmObject.md)`, `[`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getDataType

          public FundamentalMetadataObject getDataType()

      Gets the OLAP Java API data type of the `MdmSource`. The data type is a `FundamentalMetadataObject` that represents one of the following OLAP Java API data types:
      - Boolean
      - Double
      - Integer
      - Float
      - Short
      - String
      - Number (a general type that represents any of the numeric OLAP API data types, which are Integer, Double, Float, and Short)
      - Value (a general type that represents any OLAP Java API data type)

      In this documentation, the OLAP Java API data types appear in regular font to distinguish them from the Java data types, such as `boolean`, and the classes that encapsulate them, such as `Boolean`. The Java data types and classes appear in monospace font.

      Returns:
      The `FundamentalMetadataObject` that represents the OLAP Java API data type of the `MdmSource`.

    <!-- -->

    - #### getSource

          public final Source getSource()

      Gets the primary `Source` through which an application can create queries on the data represented by the `MdmSource`.
      The returned `Source` has no outputs. If the `MdmSource` is an `MdmDimension`, then the returned `Source` has no inputs. If the `MdmSource` is an `MdmDimensionedObject` (an `MdmMeasure` or an `MdmAttribute`), then the returned `Source` has inputs that correspond to the dimensions of the `MdmDimensionedObject`.

      Returns:
      A `Source` through which an application can create queries on the data represented by the `MdmSource`.

    <!-- -->

    - #### getType

          public abstract MetadataObject getType()

      Gets the type of the `MdmSource`. The type is the `MetadataObject` whose elements provide the pool from which the `MdmSource` draws its elements. Typically, the type is either an `MdmSource` or a `FundamentalMetadataObject` that represents an OLAP Java API data type such as String, Integer, or Boolean.
      Returns:
      The `MetadataObject` that is the type of the `MdmSource`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmSingleValuedAttribute.md)
- [Next Class](MdmStandardDimension.md)

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
