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

- [Prev Class](BuildProcess.md)
- [Next Class](CaseExpression.md)

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

## Class BuildSpecification

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.BuildSpecification

<!-- -->

-

  ------------------------------------------------------------------------



      public class BuildSpecification
      extends SyntaxObject

  A `SyntaxObject` that contains commands that specify how to build a `BuildItem`. You can associate a `BuildSpecification` with a `BuildItem` in the following ways.
  - Specify the `BuildSpecification` as the default `BuildSpecification` of the `AWCubeOrganization` of an `MdmCube` or the `AWPrimaryDimensionOrganization` of an `MdmPrimaryDimension`. Create a `BuildItem` for the cube or dimension using the `BuildItem(Buildable obj)` constructor.
  - Use the `addBuildSpecification(BuildSpecification spec)` method of an `AWCubeOrganization` to add the build specification to the cube organization. Create a `BuildItem` for the cube using one of the `BuildItem(Buildable obj, String buildName)` constructors.
  - Create a `BuildItem` for a cube or a dimension using one of the `BuildItem(Buildable obj, BuildSpecification inlineSpec)` constructors.

  If you create a `BuildItem` without specifying a `BuildSpecification`, a `BuildProcess` uses the default `BuildSpecification` for the buildable object. If you create a `BuildItem` and specify a `BuildSpecification`, a `BuildProcess` uses the named or inline `BuildSpecification` for the buildable object instead of the default build specificication.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                        |
    |-------------------|----------------------------------------------|
    | `static int`      | `AS_OF_BUILD_SCN`                            |
    | `static int`      | `AS_OF_CURRENT_SCN`<br>PUBLIC STATIC MEMBERS |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                       |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BuildSpecification``(java.lang.String name, `[`BuildCommand`](BuildCommand.md)`[] commands)`<br>Creates a new `BuildSpecification` that has the specified name and that contains the `BuildCommand` objects in the specified array.              |
    | `BuildSpecification``(java.lang.String name, java.util.List<`[`BuildCommand`](BuildCommand.md)`> commands)`<br>Creates a new `BuildSpecification` that has the specified name and that contains the `BuildCommand` objects in the specified list. |
    | `BuildSpecification``(java.lang.String name, java.util.List<`[`BuildCommand`](BuildCommand.md)`> commands, `[`OrderByClause`](OrderByClause.md)` orderBy)`                                                                                        |
    | `BuildSpecification``(java.lang.String name, java.util.List<`[`BuildCommand`](BuildCommand.md)`> commands, `[`OrderByClause`](OrderByClause.md)` orderBy, int flags)`                                                                             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                     | Method and Description                                                                                                                                                                                                                      |
    |---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BuildCommand`](BuildCommand.md)`[]` | `getCommands``()`<br>Gets the `BuildCommand` objects that are contained by this `BuildSpecification`.                                                                                                                                       |
    | `int`                                 | `getFlags``()`                                                                                                                                                                                                                              |
    | `java.lang.String`                    | `getName``()`<br>Gets the name of this `BuildSpecification`.                                                                                                                                                                                |
    | [`OrderByClause`](OrderByClause.md)   | `getOrderByClause``()`                                                                                                                                                                                                                      |
    | `boolean`                             | `isOrderByOnly``()`                                                                                                                                                                                                                         |
    | `java.lang.Object`                    | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitBuildSpecification` method of the `SyntaxObjectVisitor` and passes that method this `BuildSpecification` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### AS_OF_CURRENT_SCN

          public static final int AS_OF_CURRENT_SCN

      PUBLIC STATIC MEMBERS
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AS_OF_BUILD_SCN

          public static final int AS_OF_BUILD_SCN

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### BuildSpecification

          public BuildSpecification(java.lang.String name,
                                    BuildCommand[] commands)

      Creates a new `BuildSpecification` that has the specified name and that contains the `BuildCommand` objects in the specified array.
      Parameters:
      `name` - A `String` that contains the name for the `BuildSpecification`.

      `commands` - An array of `BuildCommand` objects for the `BuildSpecification`.

    <!-- -->

    - #### BuildSpecification

          public BuildSpecification(java.lang.String name,
                                    java.util.List<BuildCommand> commands)

      Creates a new `BuildSpecification` that has the specified name and that contains the `BuildCommand` objects in the specified list.
      Parameters:
      `name` - A `String` that contains the name for the `BuildSpecification`.

      `commands` - A `List` of `BuildCommand` objects for the `BuildSpecification`.

    <!-- -->

    - #### BuildSpecification

          public BuildSpecification(java.lang.String name,
                                    java.util.List<BuildCommand> commands,
                                    OrderByClause orderBy)

    <!-- -->

    - #### BuildSpecification

          public BuildSpecification(java.lang.String name,
                                    java.util.List<BuildCommand> commands,
                                    OrderByClause orderBy,
                                    int flags)

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitBuildSpecification` method of the `SyntaxObjectVisitor` and passes that method this `BuildSpecification` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitBuildSpecification` method.

    <!-- -->

    - #### getCommands

          public BuildCommand[] getCommands()

      Gets the `BuildCommand` objects that are contained by this `BuildSpecification`.
      Returns:
      An array of the `BuildCommand` objects contained by this `BuildSpecification`.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of this `BuildSpecification`.
      Returns:
      A `String` that contains the name of this `BuildSpecification`.

    <!-- -->

    - #### getOrderByClause

          public OrderByClause getOrderByClause()

    <!-- -->

    - #### isOrderByOnly

          public boolean isOrderByOnly()

    <!-- -->

    - #### getFlags

          public int getFlags()

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BuildProcess.md)
- [Next Class](CaseExpression.md)

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
