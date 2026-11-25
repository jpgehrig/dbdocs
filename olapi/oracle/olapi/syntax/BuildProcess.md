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

- [Prev Class](BuildItem.md)
- [Next Class](BuildSpecification.md)

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

## Class BuildProcess

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.BuildProcess

<!-- -->

-

  ------------------------------------------------------------------------



      public final class BuildProcess
      extends SyntaxObject

  A `SyntaxObject` that contains one or more `BuildItem` objects, each of which specifies a database object to build and how to build it.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                               |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BuildProcess``(`[`BuildItem`](BuildItem.md)`[] items)`<br>Creates a `BuildProcess` that has the `BuildItem` objects in the specified array.              |
    | `BuildProcess``(java.util.List<`[`BuildItem`](BuildItem.md)`> items)`<br>Creates a `BuildProcess` that has the `BuildItem` objects in the specified list. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                                          |
    |---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BuildItem`](BuildItem.md)`[]` | `getBuildItems``()`<br>Gets the `BuildItem` objects that are contained by this `BuildProcess`.                                                                                                                                  |
    | `java.lang.String`              | `getLogOptions``()`<br>Get the `String` representing the specification of build log options.                                                                                                                                    |
    | `java.lang.Object`              | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitBuildProcess` method of the `SyntaxObjectVisitor` and passes that method this `BuildProcess` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BuildProcess

          public BuildProcess(BuildItem[] items)

      Creates a `BuildProcess` that has the `BuildItem` objects in the specified array.
      Parameters:
      `items` - An array of `BuildItem` objects.

    <!-- -->

    - #### BuildProcess

          public BuildProcess(java.util.List<BuildItem> items)

      Creates a `BuildProcess` that has the `BuildItem` objects in the specified list.
      Parameters:
      `items` - A `List` of `BuildItem` objects.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitBuildProcess` method of the `SyntaxObjectVisitor` and passes that method this `BuildProcess` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitBuildProcess` method.

    <!-- -->

    - #### getBuildItems

          public BuildItem[] getBuildItems()

      Gets the `BuildItem` objects that are contained by this `BuildProcess`.
      Returns:
      An array of the `BuildItem` objects contained by this `BuildProcess`.

    <!-- -->

    - #### getLogOptions

          public java.lang.String getLogOptions()

      Get the `String` representing the specification of build log options. The options are not themselves represented in the API syntax, but are handled as a string.
      Returns:
      A `String` representing the build log options, or null if no build log options specified.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BuildItem.md)
- [Next Class](BuildSpecification.md)

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
