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

- [Prev Class](DateSource.md)
- [Next Class](FundamentalMetadataObject.md)

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

## Class DynamicDefinition

- java.lang.Object

- - [oracle.olapi.data.source.SourceDefinition](SourceDefinition.md)

  - - oracle.olapi.data.source.DynamicDefinition

<!-- -->

-

  ------------------------------------------------------------------------



      public final class DynamicDefinition
      extends SourceDefinition

  A proxy for the `SourceDefinition` of the `Source` returned by the `SourceGenerator` for a `Template`. An application creates a `DynamicDefinition` for a `Template` by calling the `createDynamicDefinition` method on the `Template` and passing it a `SourceGenerator`. The application can then generate the `Source` defined by the `Template` by calling the `getSource` method of the `DynamicDefinition`. The `DynamicDefinition` inherits the `getSource` method from `SourceDefinition`.
  When an application calls the `getSource` method of the `DynamicDefinition`, the `generateSource` method of the `SourceGenerator` is called. That method uses the values stored in the `MetadataState` for the `Template` to create the `Source` returned by `getSource`. If the `Source` has no inputs, the application can create a `Cursor` for the `Source` to retrieve the data it specifies from the data store.

  An application can modify the query produced by the `Template` by calling methods of the `Template` to change the values of one or more of the fields in its `MetadataState` object. The application can then call the `getSource` method of the `DynamicDefinition` again to generate a `Source` using the new values or different logic or both. The instances of the `Template` and `DynamicDefinition` objects remain the same but the `Source` that the `Template` produces has changed.

  See Also:
  [`MetadataState`](../../transaction/metadataStateManager/MetadataState.md), [`SourceGenerator`](SourceGenerator.md), [`Template`](Template.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                                                  |
    |-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`SourceDefinition`](SourceDefinition.md) | `getCurrent``()`<br>Gets the `SourceDefinition` for the `Source` currently returned by the `generateSource` method of the `SourceGenerator` for this `DynamicDefinition`.                                                                                               |
    | [`SourceDefinition`](SourceDefinition.md) | `getCurrent``(`[`Transaction`](../../transaction/Transaction.md)` transaction)`<br>Gets the `SourceDefinition` for the `Source` currently returned by the `generateSource` method of the `SourceGenerator` for this `DynamicDefinition` in the specified `Transaction`. |
    | [`SourceGenerator`](SourceGenerator.md)   | `getSourceGenerator``()`<br>Gets the `SourceGenerator` for this `DynamicDefinition`.                                                                                                                                                                                    |
    | [`Template`](Template.md)                 | `getTemplate``()`<br>Gets the `Template` whose `createDynamicDefinition` method returned this `DynamicDefinition`.                                                                                                                                                      |
    | `boolean`                                 | `isModified``(`[`Transaction`](../../transaction/Transaction.md)` transaction)`<br>Indicates whether, in the specified `Transaction`, the `Template` for this `DynamicDefinition` has changed the `Source` that it generates for this `DynamicDefinition`.              |

    - ### Methods inherited from class oracle.olapi.data.source.[SourceDefinition](SourceDefinition.md)

      [`getDataProvider`](SourceDefinition.md)`, `[`getSource`](SourceDefinition.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getCurrent

          public final SourceDefinition getCurrent()

      Gets the `SourceDefinition` for the `Source` currently returned by the `generateSource` method of the `SourceGenerator` for this `DynamicDefinition`. The relationship between that `SourceDefinition` and the `Source` is immutable. For example, if the current state of the `Template` components is such that the `generateSource` method returns the result of a `join` method call, then a call to `getCurrent` returns a `JoinDefinition`. Calling the `getSource` method of that `JoinDefinition` always returns the same `Source`, the `Source` that is associated with it.
      In contrast, the `getSource` method of `DynamicDefinition` returns the `Source` that the `generateSource` method produces. The `DynamicDefinition` is a proxy for the `SourceDefinition` that is immutably associated with the `Source`. Thus if the current state of the values used to create the `Source` changes, then the `getSource` method returns a different `Source`, yet the `DynamicDefinition` remains the same.

      The `getCurrent` method is primarily informational, and is not used by an application in building a query. An application uses the `getSource` method to get the `Source` for the `Template` and then uses that `Source` in building a complex query or in the process of creating a `Cursor` for retrieving the data defined by the `Source`.

      Returns:
      The `SourceDefinition` for the `Source` currently generated by the `SourceGenerator`.

    <!-- -->

    - #### getCurrent

          public final SourceDefinition getCurrent(Transaction transaction)

      Gets the `SourceDefinition` for the `Source` currently returned by the `generateSource` method of the `SourceGenerator` for this `DynamicDefinition` in the specified `Transaction`.
      Parameters:
      `transaction` - The `Transaction` associated with the `Source`.

      Returns:
      The `SourceDefinition` for the `Source` currently generated by the `SourceGenerator`.

    <!-- -->

    - #### getSourceGenerator

          public final SourceGenerator getSourceGenerator()

      Gets the `SourceGenerator` for this `DynamicDefinition`.
      Returns:
      The `SourceGenerator` for this `DynamicDefinition`.

    <!-- -->

    - #### getTemplate

          public final Template getTemplate()

      Gets the `Template` whose `createDynamicDefinition` method returned this `DynamicDefinition`.
      Returns:
      The `Template` used in creating this `DynamicDefinition`.

    <!-- -->

    - #### isModified

          public final boolean isModified(Transaction transaction)

      Indicates whether, in the specified `Transaction`, the `Template` for this `DynamicDefinition` has changed the `Source` that it generates for this `DynamicDefinition`.
      Parameters:
      `transaction` - The `Transaction` to specify.

      Returns:
      `true` if the `Source` has been modified in the specified `Transaction` and `false` if it has not.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DateSource.md)
- [Next Class](FundamentalMetadataObject.md)

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
