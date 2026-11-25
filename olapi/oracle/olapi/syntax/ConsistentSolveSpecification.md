Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](ConsistentSolveCommand.md)
- [Next Class](DataObject.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.olapi.syntax

## Class ConsistentSolveSpecification

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.ConsistentSolveSpecification

<!-- -->

-

  ------------------------------------------------------------------------



      public class ConsistentSolveSpecification
      extends SyntaxObject

  A `SyntaxObject` that specifies how Oracle OLAP generates solved data for an `MdmBaseMeasure` or for all of the `MdmBaseMeasure` objects of an `MdmCube`. A `ConsistentSolveSpecification` contains an ordered list of `ConsistentSolveCommand` objects. An application creates a new `ConsistentSolveSpecification` and then associates it with an `MdmCube` or `MdmBaseMeasure` by calling the `setConsistentSolveSpecification` method of the cube or the measure. The `ConsistentSolveCommand` objects specify the way in which Oracle OLAP aggregates the measure data for each of the dimensions. Executing the `ConsistentSolveCommand` objects produces the consistent state of the cube.
  An application can make intermediate, possibly temporary solves to some part of the cube, such as aggregating or allocating a set of measure values. However, because Oracle OLAP does not rebuild the entire cube until the application requests it, the state of the cube is not then consistent. The `ConsistentSolveSpecification` of the cube defines the operations that create the consistent state. Therefore, the application can achieve the consistent state again by executing a build of the entire cube.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                     |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ConsistentSolveSpecification``(`[`ConsistentSolveCommand`](ConsistentSolveCommand.md)`[] commands)`<br>Creates a `ConsistentSolveSpecification` that has the specified commands.               |
    | `ConsistentSolveSpecification``(java.util.List<`[`ConsistentSolveCommand`](ConsistentSolveCommand.md)`> commands)`<br>Creates a `ConsistentSolveSpecification` that has the specified commands. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                                                                                                                                                                          |
    |-----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ConsistentSolveCommand`](ConsistentSolveCommand.md)`[]` | `getCommands``()`<br>Gets the `ConsistentSolveCommand` objects of this `ConsistentSolveSpecification`.                                                                                                                                                          |
    | `java.lang.Object`                                        | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitConsistentSolveSpecification` method of the `SyntaxObjectVisitor` and passes that method this `ConsistentSolveSpecification` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ConsistentSolveSpecification

          public ConsistentSolveSpecification(ConsistentSolveCommand[] commands)

      Creates a `ConsistentSolveSpecification` that has the specified commands.
      Parameters:
      `commands` - An array of `ConsistentSolveCommand` objects.

    <!-- -->

    - #### ConsistentSolveSpecification

          public ConsistentSolveSpecification(java.util.List<ConsistentSolveCommand> commands)

      Creates a `ConsistentSolveSpecification` that has the specified commands.
      Parameters:
      `commands` - A `List` of `ConsistentSolveCommand` objects.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitConsistentSolveSpecification` method of the `SyntaxObjectVisitor` and passes that method this `ConsistentSolveSpecification` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitConsistentSolveSpecification` method.

    <!-- -->

    - #### getCommands

          public ConsistentSolveCommand[] getCommands()

      Gets the `ConsistentSolveCommand` objects of this `ConsistentSolveSpecification`.
      Returns:
      An array of the `ConsistentSolveCommand` objects of this `ConsistentSolveSpecification`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ConsistentSolveCommand.md)
- [Next Class](DataObject.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
