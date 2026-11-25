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
- [Next Class](BooleanParameter.md)

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

## Class Assignment

- java.lang.Object

- - oracle.olapi.data.source.Assignment

<!-- -->

-

  ------------------------------------------------------------------------



      public class Assignment
      extends java.lang.Object

  An object that belongs to a `Model` and that represents a calculation, a set of `Source` elements, and a precedence. When Oracle OLAP applies a `Model` to an associated `Source`, the `Assignment` objects of the `Model` modify the values of that `Source`.
  The calculation of an `Assignment` is specified by its `assigned` `Source`. Its set of `Source` elements are represented by its `Qualification` objects, and its precedence is indicated by an integer.

  A `Qualification` specifies a `Source` and an element of that `Source`. The `Source` specified by a `Qualification` is its qualified `Source`. The precedence of an `Assignment` indicates the order in which Oracle OLAP evaluates it, relative to other `Assignment` objects, when Oracle OLAP applies the `Model` in retrieving or calculating data in a query.

  Typically, an application does not explicitly create `Assignment` objects. Oracle OLAP creates an `Assignment` object when an application creates a custom dimension member, or when the application calls an `assign` method of a `Model`.

  See Also:
  [`Model`](Model.md), [`CustomModel`](CustomModel.md), [`Qualification`](Qualification.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                              |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Assignment``(`[`Model`](Model.md)` owner, `[`Qualification`](Qualification.md)`[] qualifications, `[`Source`](Source.md)` assigned, int precedence)`<br>Creates an `Assignment` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                     |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                | `assign``(`[`Model`](Model.md)` newOwner, `[`Source`](Source.md)` oldQualifiedSource, `[`Source`](Source.md)` newQualifiedSource)`<br>Moves the ownership of the `Assignment` from one `Model` to another. |
    | [`Source`](Source.md) | `getAssignedSource``()`<br>The `Source` that represents the calculated value that the `Model` assigns for a `Source` that has the qualified `Source` objects as inputs.                                    |
    | [`Model`](Model.md)   | `getOwner``()`<br>Gets the `Model` to which the `Assignment` applies.                                                                                                                                      |
    | `int`                 | `getPrecedence``()`<br>Gets the precedence of the `Assignment`; a higher value indicates a higher precedence.                                                                                              |
    | `java.util.List`      | `getQualifications``()`<br>Gets the `Qualification` objects for the `Assignment`.                                                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Assignment

          public Assignment(Model owner,
                            Qualification[] qualifications,
                            Source assigned,
                            int precedence)

      Creates an `Assignment` object.
      Parameters:
      `owner` - The `Model` to which this `Assignment` applies.

      `qualifications` - An array of `Qualification` objects.

      `assigned` - A `Source` that specifies the value to assign for the qualified `Source` elements.

      `precedence` - The precedence of the `Assignment` in relation to the other `Assignment` objects of the `Model`.

  <!-- -->

  - ### Method Detail

    - #### assign

          public void assign(Model newOwner,
                             Source oldQualifiedSource,
                             Source newQualifiedSource)

      Moves the ownership of the `Assignment` from one `Model` to another.
      Parameters:
      `newOwner` - The `Model` to which you want the `Assignment` to apply.

      `oldQualifiedSource` - The qualified `Source` to replace in the `Qualification` objects of the `Assignment`.

      `newQualifiedSource` - The `Source` that replaces the old qualified `Source` in the `Qualification` objects of the `Assignment`.

    <!-- -->

    - #### getOwner

          public final Model getOwner()

      Gets the `Model` to which the `Assignment` applies.
      Returns:
      The `Model` to which the `Assignment` applies.

    <!-- -->

    - #### getQualifications

          public final java.util.List getQualifications()

      Gets the `Qualification` objects for the `Assignment`.
      Returns:
      A `List` of the `Qualification` objects of the `Assignment`.

    <!-- -->

    - #### getAssignedSource

          public final Source getAssignedSource()

      The `Source` that represents the calculated value that the `Model` assigns for a `Source` that has the qualified `Source` objects as inputs.
      Returns:
      A `Source` that represents the value to assign as the value specified by the qualified `Source` objects.

    <!-- -->

    - #### getPrecedence

          public final int getPrecedence()

      Gets the precedence of the `Assignment`; a higher value indicates a higher precedence. Oracle OLAP uses the precedence value in determining the order in which it evaluates the `Assignment` objects of a `Model`. It evaluates an `Assignment` with a higher value before one with a lower value.
      Returns:
      An integer that specifies the precedence of this `Model`.

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
- [Next Class](BooleanParameter.md)

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
