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

- [Prev Class](StringSource.md)
- [Next Class](UnmatchedInputsException.md)

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

## Class Template

- java.lang.Object

- - oracle.olapi.data.source.Template

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class Template
      extends java.lang.Object

  The basis for creating a `Source` that an application can dynamically change. An application can use a `Template` to take the selections made by an end user and produce a `Source` that represents a query on the data store, or a step in producing a query.
  A `Template` uses the following related objects.

  - `MetadataState`
  - `DataProvider`
  - `SourceGenerator`
  - `DynamicDefinition`

  Those objects work together as follows:

  - The `MetadataState` implementation for a `Template` has fields for storing values.
  - An application passes the `MetadataState` and the `DataProvider` to the `Template` constructor. The `Template` abstract class has methods that create a `DynamicDefinition` and that get and set the current state of the `MetadataState`. A class that extends `Template` adds methods that set the values of the fields of its `MetadataState`.
  - A `SourceGenerator` implementation has a `generateSource` method that uses the current state of the data in the `MetadataState` to produce a `Source`.
  - The `Template` gets a `DynamicDefinition` by passing a `SourceGenerator` to its `createDynamicDefinition` method.
  - The `DynamicDefinition` has a `getSource` method that returns the `Source` produced by the `SourceGenerator`. That `Source` is the dynamic `Source` for the `Template`.

  In the process of producing a `Source` that represents a single query, an application can use the `Source` objects produced by various other `Template` implementations. The application can change the selection of data for any one of the `Template` objects that comprise the query. Because the `DynamicDefinition` that gets the `Source` for a `Template` is a proxy, the application does not have to recreate all of the component `Source` objects to produce a `Source` for the query that includes the new selection. Instead, the application just calls the `getSource` method of the `DynamicDefinition` for the `Template` that produces the query, and the current state of the changed `Template` component is used in rebuilding the query.
  An example of a `Template` that produces a query is the `TopBottomTemplate.java` class. In building the query, it uses the `Source` produced by the `SingleSelectionTemplate.java` class. The `TopBottomTest.java` class is an example program that creates a `SingleSelectionTemplate` and a `TopBottomTemplate.java`. For information on how to get the example classes, see [Example Oracle OLAP Java API Programs](../../../../doc-files/ExamplePrograms.md).

  A `SingleSelectionTemplate` object produces a `Source` that represents the values of a measure that are specified by a set of single members of all but one of the dimensions of the measure. A `TopBottomTemplate` adds the remaining dimension of the measure. It selects the elements of that dimension that are specified by the criteria represented by the `Source` for the `SingleSelectionTemplate`. It sorts the selection in ascending or descending order and produces a `Source` that represents a specified number of elements from the sorted selection.

  The `TopBottomTest.java` example program creates a `SingleSelectionTemplate` and a `TopBottomTemplate.java`. The program produces a `Source` that specifies the ten products that have the highest number of units sold for the set of single Time, Channel, and Customer dimension values. It prepares and commits the current `Transaction`. It then creates a `Cursor` for that `Source` and displays the values of the `Cursor`. The example classes `TopBottomTemplate.java` and `SingleSelectionTemplate.java` contain inner classes that implement the `SourceGenerator` interface. The `TopBottomTemplate` produces a query and the `SingleSelectionTemplate` produces a `Source` that the `TopBottomTemplate` uses in the process of building the query.

  The program next changes the value for one of the dimensions specified by the `SingleSelectionTemplate`, and it changes the number of elements to select and the type of the selection. It prepares and commits the current `Transaction`, creates a new `Cursor` for the `Source`, and displays the values of the `Cursor`. The values are now the five products that have the lowest number of units sold for the set of the other dimension values.

  Before creating the new `Cursor`, the program does not need to call the `getSource` method of the `DynamicDefinition` for either the `SingleSelectionTemplate` or the `TopBottomTemplate`. Committing the `Transaction` automatically updates the dynamic `Source` objects that those methods returned so that those `Source` objects represent the current state of the `Template` objects.

  See Also:
  [`DynamicDefinition`](DynamicDefinition.md), [`MetadataState`](../../transaction/metadataStateManager/MetadataState.md), [`SourceGenerator`](SourceGenerator.md), [`TransactionProvider`](../../transaction/TransactionProvider.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                                                                                                            |
    |-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected` | `Template``(`[`MetadataState`](../../transaction/metadataStateManager/MetadataState.md)` initialState, `[`DataProvider`](DataProvider.md)` dataProvider)`<br>Creates a new `Template`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                      | Method and Description                                                                                                                                                                                                                                                                         |
    |----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected `[`DynamicDefinition`](DynamicDefinition.md)                                | `createDynamicDefinition``(`[`SourceGenerator`](SourceGenerator.md)` sourceGenerator)`<br>Creates a `DynamicDefinition` that acts as a proxy for the `SourceDefinition` for the `Source` generated by the `SourceGenerator` and returned by the `getSource` method of the `DynamicDefinition`. |
    | `protected `[`MetadataState`](../../transaction/metadataStateManager/MetadataState.md) | `getCurrentState``()`<br>Gets the current state for this `Template`.                                                                                                                                                                                                                           |
    | `protected `[`MetadataState`](../../transaction/metadataStateManager/MetadataState.md) | `getCurrentStateForRead``()`<br>Gets the actual `MetadataState` object for this `Template` rather than a clone of the state.                                                                                                                                                                   |
    | `protected `[`MetadataState`](../../transaction/metadataStateManager/MetadataState.md) | `getCurrentStateForWrite``()`<br>Gets the current state for this `Template`.                                                                                                                                                                                                                   |
    | [`DataProvider`](DataProvider.md)                                                      | `getDataProvider``()`<br>Gets the `DataProvider` for this `Template`.                                                                                                                                                                                                                          |
    | `protected void`                                                                       | `setCurrentState``(`[`MetadataState`](../../transaction/metadataStateManager/MetadataState.md)` state)`<br>Specifies a state as the current state for this `Template`.                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Template

          protected Template(MetadataState initialState,
                             DataProvider dataProvider)
                      throws TransactionTypeUnavailableException,
                             TransactionInactiveException

      Creates a new `Template`.
      Parameters:
      `initialState` - The `MetadataState` that stores values for this `Template`.

      `dataProvider` - The `DataProvider` created using the current `TransactionProvider`.

      Throws:
      [`TransactionInactiveException`](../../transaction/TransactionInactiveException.md)

      [`TransactionTypeUnavailableException`](../../transaction/TransactionTypeUnavailableException.md)

  <!-- -->

  - ### Method Detail

    - #### createDynamicDefinition

          protected DynamicDefinition createDynamicDefinition(SourceGenerator sourceGenerator)

      Creates a `DynamicDefinition` that acts as a proxy for the `SourceDefinition` for the `Source` generated by the `SourceGenerator` and returned by the `getSource` method of the `DynamicDefinition`.
      Parameters:
      `sourceGenerator` - The `SourceGenerator` that generates a `Source` using the current state of this `Template`.

      Returns:
      A `DynamicDefinition` that provides access to the `Source` produced by the `SourceGenerator`.

    <!-- -->

    - #### getCurrentState

          protected MetadataState getCurrentState()
                                           throws TransactionalObjectInvalidException,
                                                  TransactionTypeUnavailableException,
                                                  TransactionInactiveException

      Gets the current state for this `Template`.
      Returns:
      The current state for this `Template`.

      Throws:
      [`TransactionalObjectInvalidException`](../../transaction/TransactionalObjectInvalidException.md)

      [`TransactionInactiveException`](../../transaction/TransactionInactiveException.md)

      [`TransactionTypeUnavailableException`](../../transaction/TransactionTypeUnavailableException.md)

    <!-- -->

    - #### getCurrentStateForRead

          protected MetadataState getCurrentStateForRead()
                                                  throws TransactionalObjectInvalidException,
                                                         TransactionTypeUnavailableException,
                                                         TransactionInactiveException

      Gets the actual `MetadataState` object for this `Template` rather than a clone of the state. Do not modify the state returned by this method; use it only for read operations.
      Returns:
      The current state for this `Template`.

      Throws:
      [`TransactionalObjectInvalidException`](../../transaction/TransactionalObjectInvalidException.md)

      [`TransactionTypeUnavailableException`](../../transaction/TransactionTypeUnavailableException.md)

      [`TransactionInactiveException`](../../transaction/TransactionInactiveException.md)

    <!-- -->

    - #### getCurrentStateForWrite

          protected MetadataState getCurrentStateForWrite()
                                                   throws TransactionalObjectInvalidException,
                                                          TransactionTypeUnavailableException,
                                                          TransactionInactiveException

      Gets the current state for this `Template`. The returned state is a clone of the actual state, so you can modify it. If you modify it, then you must reset the state by passing it to the `setCurrentState` method.
      Returns:
      The current state for this `Template`.

      Throws:
      [`TransactionalObjectInvalidException`](../../transaction/TransactionalObjectInvalidException.md)

      [`TransactionInactiveException`](../../transaction/TransactionInactiveException.md)

      [`TransactionTypeUnavailableException`](../../transaction/TransactionTypeUnavailableException.md)

    <!-- -->

    - #### getDataProvider

          public DataProvider getDataProvider()

      Gets the `DataProvider` for this `Template`.
      Returns:
      The `DataProvider` with which this `Template` was constructed.

    <!-- -->

    - #### setCurrentState

          protected void setCurrentState(MetadataState state)
                                  throws CursorLockException,
                                         WriteLockException,
                                         TransactionTypeUnavailableException,
                                         TransactionInactiveException

      Specifies a state as the current state for this `Template`.
      Parameters:
      `state` - The state to specify as the current state for this `Template`.

      Throws:
      [`CursorLockException`](CursorLockException.md)

      [`TransactionInactiveException`](../../transaction/TransactionInactiveException.md)

      [`TransactionTypeUnavailableException`](../../transaction/TransactionTypeUnavailableException.md)

      [`WriteLockException`](../../transaction/WriteLockException.md)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](StringSource.md)
- [Next Class](UnmatchedInputsException.md)

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
