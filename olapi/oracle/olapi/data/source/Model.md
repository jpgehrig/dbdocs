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

- [Prev Class](LiteralQualification.md)
- [Next Class](NumberParameter.md)

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

## Interface Model

- All Known Implementing Classes:
  [CustomModel](CustomModel.md), [MdmDimensionCalculationModel](../../metadata/mdm/MdmDimensionCalculationModel.md), [MdmModel](../../metadata/mdm/MdmModel.md)

  ------------------------------------------------------------------------



      public interface Model

  An interface for an object that represents a set of assignments that apply to a `Source` that has one or more inputs. Each assignment specifies a calculation that supplies a value for the `Source`. The assigned value can override an existing value.
  An OLAP Java API `Model` is analogous to the SQL `MODEL` clause. The assignments of an OLAP Java API `Model` are analogous to the `UPDATE RULES` in the SQL `MODEL` clause. Like the SQL `MODEL` clause, the assignments in an OLAP Java API `Model` only modify values in the context of a query; they do not change the persistent data itself.

  The assignments of a `Model` are represented by `Assignment` objects. The `assign` methods of a `Model` create `Assignment` objects and add them to the `Model`. An `Assignment` has one or more `Qualification` objects and an assigned `Source`. A `Qualification` specifies an element of a `Source` that is an input of the `Model`. That `Source` is the *qualified* `Source` of the `Qualification`. The assigned `Source` provides the value that the Oracle OLAP assigns for the set of `Qualification` objects. For a diagram of the `Model` class associations, see [Model Class Associations](doc-files/modelrel.md).

  The `Model` interface has methods for the following operations.

  - Getting the type, the inputs, and the outputs of the `Model`.
  - Getting the `Assignment` objects.
  - Getting the parent `Model` objects.
  - Getting and setting the default precedence value.

  The type of a `Model` is the `Source` for an OLAP Java API data type. The type of a `Model` must match the type of the `Source` to which Oracle OLAP assigns the value specified by the `Model`. The data type of the `Model` must match the data type of the value that the `Model` assigns. For example, if the type of the `Model` is Number, then the `Model` applies only to `NumberSource` objects and the `assigned` `Source` objects of the `Assignment` objects of the `Model` must be `NumberSource` objects.

  An input of a `Model` is the `Source` object for a dimension or list that has the elements for which the `Model` specifies a value. A `Model` has an input for each `Source` that is the type or is an input of the `Source` for the `Model`. If the `Model` has more than one input, then adding an `Assignment` to it requires the use of an `assign` method that takes an array of `Qualification` objects or of `String` values.

  An output of a `Model` is also a `Source` object. A `Model` can inherit the `Assignment` objects of a parent `Model`. For more information on outputs and parent `Model` objects, see [`CustomModel`](CustomModel.md).

  The precedence values of the `Assignment` objects of a `Model` affect the order in which Oracle OLAP calculates and assigns their values. Oracle OLAP evaluates an `Assignment` with a higher precedence value before an `Assignment` with a lower value.

  `Model` objects require the use of unique dimension hierarchy member values. For more information on unique and local dimension hierarchy values, see the Overview.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                                                                                                                       |
    |-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                | `assign``(`[`Qualification`](Qualification.md)`[] qualifications, `[`Source`](Source.md)` assigned)`<br>Creates an `Assignment` with the default precedence and adds it to the `Model`.                                                                                                                      |
    | `void`                | `assign``(`[`Qualification`](Qualification.md)`[] qualifications, `[`Source`](Source.md)` assigned, int precedence)`<br>Creates an `Assignment` with the specified precedence and adds it to the `Model`.                                                                                                    |
    | `void`                | `assign``(java.lang.String[] values, `[`Source`](Source.md)` assigned)`<br>Creates an `Assignment` with the default precedence and adds it to the `Model`.                                                                                                                                                   |
    | `void`                | `assign``(java.lang.String[] values, `[`Source`](Source.md)` assigned, int precedence)`<br>Creates an `Assignment` with the specified precedence and adds it to the `Model`.                                                                                                                                 |
    | `void`                | `assign``(java.lang.String value, `[`Source`](Source.md)` assigned)`<br>Creates an `Assignment` with the default precedence and adds it to the `Model`; use this method for a `Model` that has only one input.                                                                                               |
    | `void`                | `assign``(java.lang.String value, `[`Source`](Source.md)` assigned, int precedence)`<br>Creates an `Assignment` with the specified precedence and adds it to the `Model`; use this method for a `Model` that has only one input.                                                                             |
    | [`Source`](Source.md) | `createSolvedSource``()`<br>Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of the `Model`; elements of the returned `Source` that do not have an assigned value have a value of `null`.                                                                        |
    | [`Source`](Source.md) | `createSolvedSource``(`[`Source`](Source.md)` defaultValues)`<br>Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of the `Model`; elements of the returned `Source` that do not have an assigned value have the value specified by the `defaultValues` `Source`. |
    | `java.util.List`      | `getAssignments``()`<br>Gets the `Assignment` objects of the `Model`.                                                                                                                                                                                                                                        |
    | `int`                 | `getDefaultPrecedence``()`<br>Gets the default precedence value for the `Model`.                                                                                                                                                                                                                             |
    | `java.util.List`      | `getInputs``()`<br>Gets the `Source` objects that are the inputs of the `Model`.                                                                                                                                                                                                                             |
    | `java.util.List`      | `getOutputs``()`<br>Gets the `Source` objects that are the outputs of the `Model`.                                                                                                                                                                                                                           |
    | `java.util.List`      | `getParentModels``()`<br>Gets the `Model` objects that are the parents of the `Model`.                                                                                                                                                                                                                       |
    | [`Source`](Source.md) | `getType``()`<br>Gets the `Source` for the `FundamentalMetadataObject` that represents the data type of the `Model`.                                                                                                                                                                                         |
    | `void`                | `setDefaultPrecedence``(int precedence)`<br>Specifies the default precedence, which is the precedence value for `Assignment` objects that are created by methods that do not specify a precedence value.                                                                                                     |
    | `void`                | `unassign``(`[`Assignment`](Assignment.md)` assignment)`<br>Removes an `Assignment` from the `Model`.                                                                                                                                                                                                        |

<!-- -->

- - ### Method Detail

    - #### getType

          Source getType()

      Gets the `Source` for the `FundamentalMetadataObject` that represents the data type of the `Model`.
      Returns:
      The fundamental `Source` that is the type of the `Model`.

    <!-- -->

    - #### getInputs

          java.util.List getInputs()

      Gets the `Source` objects that are the inputs of the `Model`.
      Returns:
      A `List` of the `Source` objects that are the inputs of the `Model`.

    <!-- -->

    - #### getOutputs

          java.util.List getOutputs()

      Gets the `Source` objects that are the outputs of the `Model`. A `CustomModel` can have outputs. An `MdmModel` does not have outputs.
      Returns:
      A `List` of the `Source` objects that are the outputs of the `Model`.

    <!-- -->

    - #### getParentModels

          java.util.List getParentModels()

      Gets the `Model` objects that are the parents of the `Model`. A `Model` can inherit the `Assignment` objects of a parent if the type, the inputs, and any outputs of the `Model` are the same as those of the parent `Model`.
      Returns:
      A `List` of the `Model` objects that are the parent models of the `Model`.

    <!-- -->

    - #### getAssignments

          java.util.List getAssignments()

      Gets the `Assignment` objects of the `Model`.
      Returns:
      A `List` of the `Assignment` objects of the `Model`.

    <!-- -->

    - #### assign

          void assign(Qualification[] qualifications,
                      Source assigned)

      Creates an `Assignment` with the default precedence and adds it to the `Model`.
      Parameters:
      `qualifications` - An array of `Qualification` objects, each of which specifies an element of an input `Source`. The array can include a `Qualification` for each input of the `Model`.

      `assigned` - A `Source` that specifies the value to assign.

    <!-- -->

    - #### assign

          void assign(Qualification[] qualifications,
                      Source assigned,
                      int precedence)

      Creates an `Assignment` with the specified precedence and adds it to the `Model`.
      Parameters:
      `qualifications` - An array of `Qualification` objects, each of which specifies an element of an input `Source`. The array can include a `Qualification` for each input of the `Model`.

      `assigned` - A `Source` that specifies the value to assign.

      `precedence` - An integer that specifies a precedence value for the `Assignment`.

    <!-- -->

    - #### assign

          void assign(java.lang.String value,
                      Source assigned)

      Creates an `Assignment` with the default precedence and adds it to the `Model`; use this method for a `Model` that has only one input.
      Parameters:
      `value` - A `String` that specifies an element of the input `Source`.

      `assigned` - A `Source` that specifies the value to assign.

    <!-- -->

    - #### assign

          void assign(java.lang.String value,
                      Source assigned,
                      int precedence)

      Creates an `Assignment` with the specified precedence and adds it to the `Model`; use this method for a `Model` that has only one input.
      Parameters:
      `value` - A `String` that specifies an element of the input `Source`.

      `assigned` - A `Source` that specifies the value to assign.

      `precedence` - An integer that specifies a precedence value for the `Assignment`.

    <!-- -->

    - #### assign

          void assign(java.lang.String[] values,
                      Source assigned)

      Creates an `Assignment` with the default precedence and adds it to the `Model`.
      Parameters:
      `values` - An array of `String` objects each of which specifies an element of an input `Source`. The array can include a element for each input of the `Model`.

      `assigned` - A `Source` that specifies the value to assign.

    <!-- -->

    - #### assign

          void assign(java.lang.String[] values,
                      Source assigned,
                      int precedence)

      Creates an `Assignment` with the specified precedence and adds it to the `Model`.
      Parameters:
      `values` - An array of `String` objects each of which specifies an element of an input `Source`. The array can include a element for each input of the `Model`.

      `assigned` - A `Source` that specifies the value to assign.

      `precedence` - An integer that specifies a precedence value for the `Assignment`.

    <!-- -->

    - #### unassign

          void unassign(Assignment assignment)

      Removes an `Assignment` from the `Model`.
      Parameters:
      `assignment` - The `Assignment` to remove.

    <!-- -->

    - #### getDefaultPrecedence

          int getDefaultPrecedence()

      Gets the default precedence value for the `Model`.
      Returns:
      An integer that represents the precedence for `Assignment` objects that are created by methods that do not specify a precedence value.

    <!-- -->

    - #### setDefaultPrecedence

          void setDefaultPrecedence(int precedence)

      Specifies the default precedence, which is the precedence value for `Assignment` objects that are created by methods that do not specify a precedence value.
      Parameters:
      `precedence` - An integer value to set as the default precedence.

    <!-- -->

    - #### createSolvedSource

          Source createSolvedSource()

      Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of the `Model`; elements of the returned `Source` that do not have an assigned value have a value of `null`. The `Source` has as inputs the `Source` objects that are the inputs of the `Model` associated with it.
      Returns:
      A `Source` that represents the results of the evaluation of the `Assignment` objects of the `Model` and that has `null` for unassigned values.

    <!-- -->

    - #### createSolvedSource

          Source createSolvedSource(Source defaultValues)

      Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of the `Model`; elements of the returned `Source` that do not have an assigned value have the value specified by the `defaultValues` `Source`. The `Source` has as inputs the `Source` objects that are the inputs of the `Model` associated with it.
      Parameters:
      `defaultValues` - A `Source` that specifies the value to assign for a member of an input when the `Assignment` objects of the `Model` do not assign a value for the input member.

      Returns:
      A `Source` that represents the results of the evaluation of the `Assignment` objects of the `Model` and that has the value of `defaultValues` for unassigned values.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](LiteralQualification.md)
- [Next Class](NumberParameter.md)

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
