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

- [Prev Class](FunctionDescriptorTypedExpressionArgument.md)
- [Next Class](HierarchicalCondition.md)

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

## Class GroupCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - oracle.olapi.syntax.GroupCommand

<!-- -->

-

  ------------------------------------------------------------------------



      public final class GroupCommand
      extends BuildCommand

  A `BuildCommand` that represents a group of `SimpleCommand` objects that operate on the specified `MdmBaseMeasure` objects when the condition specified by a `SymmetricCondition` is true.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `GroupCommand``(java.util.List<`[`SimpleCommand`](SimpleCommand.md)`> commands, `[`SymmetricCondition`](SymmetricCondition.md)` whereCondition, java.util.List<`[`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)`> measures)`<br>Creates a `GroupCommand` that has the specified lists of `SimpleCommand` and `MdmBaseMeasure` objects, and the specified `SymmetricCondition`. |
    | `GroupCommand``(`[`SimpleCommand`](SimpleCommand.md)`[] commands, `[`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)`[] measures)`<br>Creates a `GroupCommand` that has the specified arrays of `SimpleCommand` and `MdmBaseMeasure` objects.                                                                                                                                    |
    | `GroupCommand``(`[`SimpleCommand`](SimpleCommand.md)`[] commands, `[`SymmetricCondition`](SymmetricCondition.md)` whereCondition)`<br>Creates a `GroupCommand` that has the specified arrays of `SimpleCommand` objects and the specified `SymmetricCondition`.                                                                                                                      |
    | `GroupCommand``(`[`SimpleCommand`](SimpleCommand.md)`[] commands, `[`SymmetricCondition`](SymmetricCondition.md)` whereCondition, `[`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)`[] measures)`<br>Creates a `GroupCommand` that has the specified arrays of `SimpleCommand` and `MdmBaseMeasure` objects, and the specified `SymmetricCondition`.                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                                                                                                                                          |
    |-----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`SimpleCommand`](SimpleCommand.md)`[]`                   | `getCommands``()`<br>Gets the `SimpleCommand` objects that are associated this `GroupCommand`.                                                                                                                                  |
    | `java.lang.String[]`                                      | `getMeasureIDs``()`<br>Gets the IDs of the `MdmBaseMeasure` objects that are associated with this `GroupCommand`.                                                                                                               |
    | [`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)`[]` | `getMeasures``()`<br>Gets the `MdmBaseMeasure` objects that are associated with this `GroupCommand`.                                                                                                                            |
    | [`SymmetricCondition`](SymmetricCondition.md)             | `getWhereCondition``()`<br>Gets the `SymmetricCondition` that is associated with this `GroupCommand`.                                                                                                                           |
    | `java.lang.Object`                                        | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitGroupCommand` method of the `SyntaxObjectVisitor` and passes that method this `GroupCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GroupCommand

          public GroupCommand(SimpleCommand[] commands,
                              SymmetricCondition whereCondition)

      Creates a `GroupCommand` that has the specified arrays of `SimpleCommand` objects and the specified `SymmetricCondition`.
      Parameters:
      `commands` - An array of `SimpleCommand` objects.

      `whereCondition` - A `SymmetricCondition` that specifies the condition upon which the commands execute.

    <!-- -->

    - #### GroupCommand

          public GroupCommand(SimpleCommand[] commands,
                              MdmBaseMeasure[] measures)

      Creates a `GroupCommand` that has the specified arrays of `SimpleCommand` and `MdmBaseMeasure` objects.
      Parameters:
      `commands` - An array of `SimpleCommand` objects.

      `measures` - An array of `MdmBaseMeasure` objects.

    <!-- -->

    - #### GroupCommand

          public GroupCommand(SimpleCommand[] commands,
                              SymmetricCondition whereCondition,
                              MdmBaseMeasure[] measures)

      Creates a `GroupCommand` that has the specified arrays of `SimpleCommand` and `MdmBaseMeasure` objects, and the specified `SymmetricCondition`.
      Parameters:
      `commands` - An array of `SimpleCommand` objects.

      `whereCondition` - A `SymmetricCondition` that specifies the condition upon which the commands execute.

      `measures` - An array of `MdmBaseMeasure` objects.

    <!-- -->

    - #### GroupCommand

          public GroupCommand(java.util.List<SimpleCommand> commands,
                              SymmetricCondition whereCondition,
                              java.util.List<MdmBaseMeasure> measures)

      Creates a `GroupCommand` that has the specified lists of `SimpleCommand` and `MdmBaseMeasure` objects, and the specified `SymmetricCondition`.
      Parameters:
      `commands` - A `List` of `SimpleCommand` objects.

      `whereCondition` - A `SymmetricCondition` that specifies the condition upon which the commands execute.

      `measures` - A `List` of `MdmBaseMeasure` objects.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitGroupCommand` method of the `SyntaxObjectVisitor` and passes that method this `GroupCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitGroupCommand` method.

    <!-- -->

    - #### getMeasures

          public MdmBaseMeasure[] getMeasures()

      Gets the `MdmBaseMeasure` objects that are associated with this `GroupCommand`.
      Returns:
      An array of the `MdmBaseMeasure` objects associated with this `GroupCommand`.

    <!-- -->

    - #### getMeasureIDs

          public java.lang.String[] getMeasureIDs()

      Gets the IDs of the `MdmBaseMeasure` objects that are associated with this `GroupCommand`.
      Returns:
      An array of the `String` objects that contain the IDs of the `MdmBaseMeasure` objects associated with this `GroupCommand`.

    <!-- -->

    - #### getWhereCondition

          public SymmetricCondition getWhereCondition()

      Gets the `SymmetricCondition` that is associated with this `GroupCommand`.
      Returns:
      The `SymmetricCondition` associated with this `GroupCommand`.

    <!-- -->

    - #### getCommands

          public SimpleCommand[] getCommands()

      Gets the `SimpleCommand` objects that are associated this `GroupCommand`.
      Returns:
      The `SimpleCommand` objects associated with this `GroupCommand`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionDescriptorTypedExpressionArgument.md)
- [Next Class](HierarchicalCondition.md)

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
