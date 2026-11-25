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

- [Prev Class](Source.md)
- [Next Class](SourceGenerator.md)

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

## Class SourceDefinition

- java.lang.Object

- - oracle.olapi.data.source.SourceDefinition

<!-- -->

- Direct Known Subclasses:
  [DynamicDefinition](DynamicDefinition.md)

  ------------------------------------------------------------------------



      public abstract class SourceDefinition
      extends java.lang.Object

  Contains information about the origins of the `Source` with which it is associated. Every `Source` has an associated `SourceDefinition`. The only subclass of `SourceDefinition` that appears in this documentation is `DynamicDefinition` because it is the only one that is used by a client application.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                                                                      |
    |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | [`DataProvider`](DataProvider.md) | `getDataProvider``()`<br>Gets the `DataProvider` that produced the `Source` that is associated with the `SourceDefinition`. |
    | [`Source`](Source.md)             | `getSource``()`<br>Gets the `Source` associated with the `SourceDefinition`.                                                |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getDataProvider

          public final DataProvider getDataProvider()

      Gets the `DataProvider` that produced the `Source` that is associated with the `SourceDefinition`.
      Returns:
      The `DataProvider` that produced the `Source` that is associated with the `SourceDefinition`.

    <!-- -->

    - #### getSource

          public final Source getSource()

      Gets the `Source` associated with the `SourceDefinition`.
      Returns:
      The `Source` associated with the `SourceDefinition`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Source.md)
- [Next Class](SourceGenerator.md)

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
