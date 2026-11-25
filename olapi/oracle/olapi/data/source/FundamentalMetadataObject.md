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

- [Prev Class](DynamicDefinition.md)
- [Next Class](FundamentalMetadataProvider.md)

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

oracle.olapi.data.source

## Class FundamentalMetadataObject

- java.lang.Object

- - oracle.olapi.data.source.FundamentalMetadataObject

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../../metadata/MetadataObject.md)

  ------------------------------------------------------------------------



      public final class FundamentalMetadataObject
      extends java.lang.Object
      implements MetadataObject

  An object that represents a data type, function, or function parameter used by the Oracle OLAP Java API. Typically, application programmers only use the objects that represent OLAP Java API data types. They do not use the objects that represent OLAP Java API functions or their parameters. To get a `FundamentalMetadataObject` you use a method of the `FundamentalMetadataProvider` class. For example, to get a `FundamentalMetadataObject` that represents the OLAP Java API Boolean data type, use the `FundamentalMetadataProvider.getBooleanDataType()` method.
  A `FundamentalMetadataObject` has a unique identifier (ID) that persists from one `MetadataProvider` instance to another. Therefore, an application can store the ID for a `FundamentalMetadataObject` during one and then it can use that ID in a later session. Of course, repeated use assumes that the `FundamentalMetadataObject` has not changed from session to session.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                            |
    |-----------------------|-----------------------------------------------------------------------------------|
    | `java.lang.String`    | `getID``()`<br>Gets the unique identifier for this `FundamentalMetadataObject`.   |
    | [`Source`](Source.md) | `getSource``()`<br>Gets the `Source` object for this `FundamentalMetadataObject`. |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getID

          public final java.lang.String getID()

      Gets the unique identifier for this `FundamentalMetadataObject`.
      Specified by:
      [`getID`](../../metadata/MetadataObject.md) in interface [`MetadataObject`](../../metadata/MetadataObject.md)

      Returns:
      A `String` whose value is the unique identifier for this `FundamentalMetadataObject`.

    <!-- -->

    - #### getSource

          public final Source getSource()

      Gets the `Source` object for this `FundamentalMetadataObject`.
      Returns:
      The `Source` for this `FundamentalMetadataObject`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DynamicDefinition.md)
- [Next Class](FundamentalMetadataProvider.md)

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
