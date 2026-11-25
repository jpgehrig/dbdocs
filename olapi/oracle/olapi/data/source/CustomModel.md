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

- [Prev Class](CursorSpecificationVisitor.md)
- [Next Class](DataProvider.md)

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

## Class CustomModel

- java.lang.Object

- - oracle.olapi.data.source.CustomModel

<!-- -->

- All Implemented Interfaces:
  [Model](Model.md)

  ------------------------------------------------------------------------



      public final class CustomModel
      extends java.lang.Object
      implements Model

  A `Model` that an application can explicitly create. To create a `CustomModel`, call one of the `createModel` methods of a `DataProvider`.
  By calling a `createSolvedSource` method of a `CustomModel`, you can produce a `Source` that represents the evaluation of the `Assignment` objects of the `CustomModel`. The solved `Source` has all of the inputs of the `CustomModel`.

  See Also:
  [`Assignment`](Assignment.md), [`Qualification`](Qualification.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `CustomModel``(`[`DataProvider`](DataProvider.md)` dataProvider, `[`Source`](Source.md)`[] inputs, `[`Source`](Source.md)` type, `[`Source`](Source.md)`[] outputs, `[`Model`](Model.md)`[] parentModels, `[`Transaction`](../../transaction/Transaction.md)` transaction)`<br>Creates a new `CustomModel`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                                                       |
    |-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                | `assign``(`[`Qualification`](Qualification.md)`[] qualifications, `[`Source`](Source.md)` assigned)`<br>Creates an `Assignment` with the default precedence and adds it to the `CustomModel`.                                                |
    | `void`                | `assign``(`[`Qualification`](Qualification.md)`[] qualifications, `[`Source`](Source.md)` assigned, int precedence)`<br>Creates an `Assignment` with the specified precedence and adds it to the `CustomModel`.                              |
    | `void`                | `assign``(java.lang.String[] values, `[`Source`](Source.md)` assigned)`<br>Creates an `Assignment` with the default precedence and adds it to the `CustomModel`.                                                                             |
    | `void`                | `assign``(java.lang.String[] values, `[`Source`](Source.md)` assigned, int precedence)`<br>Creates an `Assignment` with the specified precedence and adds it to the `CustomModel`.                                                           |
    | `void`                | `assign``(java.lang.String value, `[`Source`](Source.md)` assigned)`<br>Creates an `Assignment` with the default precedence and adds it to the `Model`; use this method for a `CustomModel` that has only one input.                         |
    | `void`                | `assign``(java.lang.String value, `[`Source`](Source.md)` assigned, int precedence)`<br>Creates an `Assignment` with the specified precedence and adds it to the `CustomModel`; use this method for a `CustomModel` that has only one input. |
    | [`Source`](Source.md) | `createSolvedSource``()`<br>Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of `CustomModel`.                                                                                                   |
    | [`Source`](Source.md) | `createSolvedSource``(`[`Source`](Source.md)` defaultValues)`<br>Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of the `CustomModel`.                                                          |
    | `java.util.List`      | `getAssignments``()`<br>Gets the `Assignment` objects of the `CustomModel`.                                                                                                                                                                  |
    | `int`                 | `getDefaultPrecedence``()`<br>Gets the default precedence value for the `CustomModel`.                                                                                                                                                       |
    | `java.lang.String`    | `getID``()`<br>Gets a `String` that uniquely identifies the `CustomModel`.                                                                                                                                                                   |
    | `java.util.List`      | `getInputs``()`<br>Gets the `Source` objects that are the inputs of the `CustomModel`.                                                                                                                                                       |
    | `java.util.List`      | `getOutputs``()`<br>Gets the `Source` objects that are the outputs of the `CustomModel`.                                                                                                                                                     |
    | `java.util.List`      | `getParentModels``()`<br>Gets the `Model` objects from which the `CustomModel` inherits `Assignment` objects.                                                                                                                                |
    | [`Source`](Source.md) | `getType``()`<br>Gets the `Source` for the `FundamentalMetadataObject` that represents the data type of the `CustomModel`.                                                                                                                   |
    | `void`                | `setDefaultPrecedence``(int precedence)`<br>Specifies the default precedence, which is the precedence value for `Assignment` objects that are created by methods that do not specify a precendence value.                                    |
    | `void`                | `unassign``(`[`Assignment`](Assignment.md)` assignment)`<br>Removes an `Assignment` from the `CustomModel`.                                                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### CustomModel

          public CustomModel(DataProvider dataProvider,
                             Source[] inputs,
                             Source type,
                             Source[] outputs,
                             Model[] parentModels,
                             Transaction transaction)

      Creates a new `CustomModel`. An application typically creates a `CustomModel` by calling one of the `createModel` methods of the `DataProvider` it is using.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `inputs` - An array of `Source` objects that are the inputs of the `CustomModel`. The `Qualification` objects of the `Assignment` objects of the `CustomModel` specify the values of the inputs for which the `CustomModel` assigns values.

      `type` - The `Source` for the `FundamentalMetadataObject` for the data type that you want the `CustomModel` to have.

      `outputs` - An array of `Source` objects that you want the `CustomModel` to have as outputs. An assigned `Source` of the `Assignment` objects of the `CustomModel` must have the same the outputs as the `CustomModel`.

      `parentModels` - An array of `Model` objects from which the `CustomModel` inherits `Assignment` objects.

      `transaction` - The current `Transaction`.

  <!-- -->

  - ### Method Detail

    - #### getID

          public final java.lang.String getID()

      Gets a `String` that uniquely identifies the `CustomModel`.
      Returns:
      A `String` that uniquely identifies the `CustomModel`.

    <!-- -->

    - #### getType

          public final Source getType()

      Gets the `Source` for the `FundamentalMetadataObject` that represents the data type of the `CustomModel`.
      Specified by:
      [`getType`](Model.md) in interface [`Model`](Model.md)

      Returns:
      The fundamental `Source` that is the type of the `CustomModel`.

    <!-- -->

    - #### getInputs

          public final java.util.List getInputs()

      Gets the `Source` objects that are the inputs of the `CustomModel`.
      Specified by:
      [`getInputs`](Model.md) in interface [`Model`](Model.md)

      Returns:
      A `List` of the `Source` objects that are the inputs of the `CustomModel`.

    <!-- -->

    - #### getOutputs

          public final java.util.List getOutputs()

      Gets the `Source` objects that are the outputs of the `CustomModel`.
      Specified by:
      [`getOutputs`](Model.md) in interface [`Model`](Model.md)

      Returns:
      A `List` of the `Source` objects that are the outputs of the `CustomModel`.

    <!-- -->

    - #### getParentModels

          public final java.util.List getParentModels()

      Gets the `Model` objects from which the `CustomModel` inherits `Assignment` objects.
      Specified by:
      [`getParentModels`](Model.md) in interface [`Model`](Model.md)

      Returns:
      A `List` of the `Model` objects from which the `CustomModel` inherits `Assignment` objects.

    <!-- -->

    - #### getAssignments

          public java.util.List getAssignments()

      Gets the `Assignment` objects of the `CustomModel`.
      Specified by:
      [`getAssignments`](Model.md) in interface [`Model`](Model.md)

      Returns:
      A `List` of the `Assignment` objects of the `CustomModel`.

    <!-- -->

    - #### assign

          public void assign(Qualification[] qualifications,
                             Source assigned)

      Creates an `Assignment` with the default precedence and adds it to the `CustomModel`.
      Specified by:
      [`assign`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `qualifications` - An array of `Qualification` objects, each of which specifies a `Source` and an element of that `Source`. The array must have a `Qualification` for each input of the `CustomModel`.

      `assigned` - A `Source` that is the assigned `Source` for the `Assignment`.

    <!-- -->

    - #### assign

          public void assign(Qualification[] qualifications,
                             Source assigned,
                             int precedence)

      Creates an `Assignment` with the specified precedence and adds it to the `CustomModel`.
      Specified by:
      [`assign`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `qualifications` - An array of `Qualification` objects, each of which specifies a `Source` and an element of that `Source`. The array must have a `Qualification` for each input of the `CustomModel`.

      `assigned` - A `Source` that is the assigned `Source` for the `Assignment`.

      `precedence` - An integer that specifies the precedence value for the `Assignment`.

    <!-- -->

    - #### assign

          public void assign(java.lang.String value,
                             Source assigned)

      Creates an `Assignment` with the default precedence and adds it to the `Model`; use this method for a `CustomModel` that has only one input.
      Specified by:
      [`assign`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `value` - A `String` that contains the value of an element of the qualified `Source` for the `Qualification` of the `Assignment`.

      `assigned` - A `Source` that is the assigned `Source` for the `Assignment`.

    <!-- -->

    - #### assign

          public void assign(java.lang.String value,
                             Source assigned,
                             int precedence)

      Creates an `Assignment` with the specified precedence and adds it to the `CustomModel`; use this method for a `CustomModel` that has only one input.
      Specified by:
      [`assign`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `value` - A `String` that contains the value of an element of the qualified `Source` for the `Qualification` of the `Assignment`.

      `assigned` - A `Source` that is the assigned `Source` of the `Assignment`.

      `precedence` - An integer that specifies the precedence value for the `Assignment`.

    <!-- -->

    - #### assign

          public void assign(java.lang.String[] values,
                             Source assigned)

      Creates an `Assignment` with the default precedence and adds it to the `CustomModel`.
      Specified by:
      [`assign`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `values` - An array of `String` objects, each of which contains the value of an element of a qualified `Source` for the `Qualification` objects of the `Assignment`. The array must have a `String` value for each input of the `CustomModel`.

      `assigned` - A `Source` that is the assigned `Source` for the `Assignment`.

    <!-- -->

    - #### assign

          public void assign(java.lang.String[] values,
                             Source assigned,
                             int precedence)

      Creates an `Assignment` with the specified precedence and adds it to the `CustomModel`.
      Specified by:
      [`assign`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `values` - An array of `String` objects, each of which contains the value of an element of a qualified `Source` for the `Qualification` objects of the `Assignment`. The array must have a `String` value for each input of the `CustomModel`.

      `assigned` - A `Source` that is the assigned `Source` for the `Assignment`.

      `precedence` - An integer that specifies the precedence value for the `Assignment`.

    <!-- -->

    - #### unassign

          public void unassign(Assignment assignment)

      Removes an `Assignment` from the `CustomModel`.
      Specified by:
      [`unassign`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `assignment` - The `Assignment` to remove.

    <!-- -->

    - #### getDefaultPrecedence

          public int getDefaultPrecedence()

      Gets the default precedence value for the `CustomModel`.
      Specified by:
      [`getDefaultPrecedence`](Model.md) in interface [`Model`](Model.md)

      Returns:
      An integer that represents the precedence for `Assignment` objects that are created by methods that do not specify a precedence value.

    <!-- -->

    - #### setDefaultPrecedence

          public void setDefaultPrecedence(int precedence)

      Specifies the default precedence, which is the precedence value for `Assignment` objects that are created by methods that do not specify a precendence value.
      Specified by:
      [`setDefaultPrecedence`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `precedence` - An integer value to set as the default precedence; a higher value indicates a higher precedence.

    <!-- -->

    - #### createSolvedSource

          public final Source createSolvedSource()

      Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of `CustomModel`. For an element of the returned `Source` that does not have an assigned value, the value is `null`.
      Specified by:
      [`createSolvedSource`](Model.md) in interface [`Model`](Model.md)

      Returns:
      A `Source` represents the results of the evaluation of the `Assignment` objects of `Model` and that has `null` for unassigned values.

    <!-- -->

    - #### createSolvedSource

          public final Source createSolvedSource(Source defaultValues)

      Creates a `Source` that represents the results of the evaluation of the `Assignment` objects of the `CustomModel`. The elements of the returned `Source` that do not have an assigned value have the value specified by the `defaultValues` `Source`.
      Specified by:
      [`createSolvedSource`](Model.md) in interface [`Model`](Model.md)

      Parameters:
      `defaultValues` - A `Source` that specifies the value that you want Oracle OLAP to assign for a member of an input when the `Assignment` objects of the `CustomModel` do not assign a value for the input member.

      Returns:
      A `Source` that represents the results of the evaluation of the `Assignment` objects of the `CustomModel` and that has the values of `defaultValues` for unassigned values.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CursorSpecificationVisitor.md)
- [Next Class](DataProvider.md)

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
