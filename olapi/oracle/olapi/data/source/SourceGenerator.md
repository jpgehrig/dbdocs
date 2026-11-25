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

- [Prev Class](SourceDefinition.md)
- [Next Class](SpecifiedCursorManager.md)

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

## Interface SourceGenerator

-

  ------------------------------------------------------------------------



      public interface SourceGenerator

  An interface for an object that produces a `Source` for a `Template`. The `Source` represents a query on the data store or a step in building a query. In producing the `Source`, a `SourceGenerator` uses the current state of the data stored in the `MetadataState` for the `Template`. The `generateSource` method of `SourceGenerator` returns the `Source` when it is called by the `getSource` method of a `DynamicDefinition` for the `Template`.
  To get the `Source` produced by the `generateSource` method, do the following:

  1.  Create a `Template` object.
  2.  Call the `createDynamicDefinition` method of the `Template` and pass it the `SourceGenerator`.
  3.  Call the `getSource` method of the `DynamicDefinition`.

  A `Template` can have more than one `DynamicDefinition`, each with a different `SourceGenerator`. Each `SourceGenerator` can a produce different `Source` object that is based on the same data, as specified by the current state of the `MetadataState`. However, any specific implementation of `SourceGenerator` must produce only one type of `Source`, such as a `BooleanSource`, a `NumberSource`, or a `StringSource`.

  The example classes `TopBottomTemplate.java` and `SingleSelectionTemplate.java` contain inner classes that implement the `SourceGenerator` interface. The `TopBottomTemplate` produces a query and the `SingleSelectionTemplate` produces a `Source` that the `TopBottomTemplate` uses in the process of building the query. For information on those classes and on the `TopBottomTest` example program that uses them, see [Example Oracle OLAP Java API Programs](../../../../doc-files/ExamplePrograms.md).

  See Also:
  [`Template`](Template.md), [`MetadataState`](../../transaction/metadataStateManager/MetadataState.md), [`DynamicDefinition`](DynamicDefinition.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                           |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Source`](Source.md) | `generateSource``(`[`MetadataState`](../../transaction/metadataStateManager/MetadataState.md)` state)`<br>Produces a `Source` that is based on the current state of the `MetadataState` object for a `Template`. |

<!-- -->

- - ### Method Detail

    - #### generateSource

          Source generateSource(MetadataState state)

      Produces a `Source` that is based on the current state of the `MetadataState` object for a `Template`.
      Parameters:
      `state` - The `MetadataState` whose fields contain the values of the current state of the `Template`.

      Returns:
      A `Source` that specifies a query or a step in building a query.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SourceDefinition.md)
- [Next Class](SpecifiedCursorManager.md)

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
