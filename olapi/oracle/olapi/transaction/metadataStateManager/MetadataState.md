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

- Prev Class
- Next Class

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

oracle.olapi.transaction.metadataStateManager

## Interface MetadataState

-

  ------------------------------------------------------------------------



      public interface MetadataState

  An interface for an object that stores values for a `Template`. An implementation of this interface must include a `clone` method that saves the current state of the values. When instantiating a new `Template`, an application passes a `MetadataState` to the `Template` constructor. The `Template` has methods for getting and setting the values stored by the `MetadataState`. When an application gets the `Source` produced by the `Template`, by calling the `getSource` method on a `DynamicDefinition`, the `MetadataState` is passed to the `generateSource` method on the `SourceGenerator` for the `Template`.
  As an example of a `MetadataState`, suppose a `Template` produces a `Source` that defines the selection of a number of data values from the top or bottom of the elements of a measure for one of the dimensions of the measure. The other dimensions of the measure are limited to single values. The `Source` represents a request for data such as, "Give me the ten products that have the highest sales amount values of those sold through the direct sales channel to customers from San Francisco in the first quarter of the calendar year 2000 while a televised promotion was occurring."

  The `MetadataState` for that `Template` has fields for storing the following kinds of values:

  - A `Source` representing the dimension on which to base the selection of the number of values from the top or bottom, such as a `Source` representing the products dimension.
  - A `Source` representing a request for the values of the measure defined by the single-valued dimensions as outputs, such as a `Source` representing a request for the values of all the sales amounts made through the direct sales channel to customers from San Francisco in the first quarter of the calendar year 2000 while a televised promotion was occurring.
  - A `float` representing the number of data values to select.
  - An `int` representing whether the selection of values is from the top or bottom.

  In using a `Template`, an application sets the values in the `MetadataState` by calling methods on the `Template`. The application then gets the `Source` produced by the `Template` by calling the `getSource` method on a `DynamicDefinition` created by the `Template`.

  See Also:
  [`SourceGenerator`](../../data/source/SourceGenerator.md), [`Template`](../../data/source/Template.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                            |
    |--------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `clone``()`<br>Creates a copy of this `MetadataState`, thus saving the current state of the values stored by the `MetadataState`. |

<!-- -->

- - ### Method Detail

    - #### clone

          java.lang.Object clone()

      Creates a copy of this `MetadataState`, thus saving the current state of the values stored by the `MetadataState`.
      Returns:
      A copy of this `MetadataState`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- Next Class

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
