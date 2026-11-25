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

- [Prev Class](ComparisonCondition.md)
- [Next Class](Condition.md)

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

## Class CompileCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.CompileCommand

<!-- -->

-

  ------------------------------------------------------------------------



      public final class CompileCommand
      extends SimpleCommand

  A `SimpleCommand` that causes the build process to determine and validate relationships, such as the attributes of a dimension, and to store information about the relationships. You can use a `CompileCommand` after a `LoadCommand` in a `BuildSpecification`. An application gets a `CompileCommand` by using a static field constant.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                          |
    |---------------------------|--------------------------------------------------------------------------------|
    | `static CompileCommand`   | `DEFAULT`<br>Produces a `CompileCommand` that executes a default compilation.  |
    | `static java.lang.String` | `DEFAULT_OPTION`<br>A constant that represents the default compilation option. |
    | `static CompileCommand`   | `INSTANCE`<br>Produces a `CompileCommand` that executes a default compilation. |
    | `static CompileCommand`   | `NO_SORT`<br>Produces a `CompileCommand` that has the `NO SORT` option.        |
    | `static java.lang.String` | `NO_SORT_OPTION`<br>A constant that represents the NO SORT option.             |
    | `static CompileCommand`   | `SORT`<br>Produces a `CompileCommand` that has the `SORT` option.              |
    | `static CompileCommand`   | `SORT_ONLY`<br>Produces a `CompileCommand` that has the `SORT ONLY` option.    |
    | `static java.lang.String` | `SORT_ONLY_OPTION`<br>A constant that represents the SORT ONLY option.         |
    | `static java.lang.String` | `SORT_OPTION`<br>A constant that represents the SORT option.                   |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------|
    | `CompileCommand``(java.lang.String option)`<br>Creates a `CompileCommand` with the specified compilation command option. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                              |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getCompileOption``()`<br>Gets the compilation command option of this `CompileCommand`.                                                                                                                                             |
    | `java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitCompileCommand` method of the `SyntaxObjectVisitor` and passes that method this `CompileCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT_OPTION

          public static final java.lang.String DEFAULT_OPTION

      A constant that represents the default compilation option.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SORT_OPTION

          public static final java.lang.String SORT_OPTION

      A constant that represents the SORT option.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NO_SORT_OPTION

          public static final java.lang.String NO_SORT_OPTION

      A constant that represents the NO SORT option.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SORT_ONLY_OPTION

          public static final java.lang.String SORT_ONLY_OPTION

      A constant that represents the SORT ONLY option.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT

          public static final CompileCommand DEFAULT

      Produces a `CompileCommand` that executes a default compilation.

    <!-- -->

    - #### INSTANCE

          public static final CompileCommand INSTANCE

      Produces a `CompileCommand` that executes a default compilation. The `CompileCommand` has the `DEFAULT_OPTION` option.

    <!-- -->

    - #### SORT

          public static final CompileCommand SORT

      Produces a `CompileCommand` that has the `SORT` option.

    <!-- -->

    - #### NO_SORT

          public static final CompileCommand NO_SORT

      Produces a `CompileCommand` that has the `NO SORT` option.

    <!-- -->

    - #### SORT_ONLY

          public static final CompileCommand SORT_ONLY

      Produces a `CompileCommand` that has the `SORT ONLY` option.

  <!-- -->

  - ### Constructor Detail

    - #### CompileCommand

          public CompileCommand(java.lang.String option)

      Creates a `CompileCommand` with the specified compilation command option.
      Parameters:
      `option` - A `String` that contains a compilation command option, such as `DEFAULT_OPTION` or `SORT_OPTION`.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitCompileCommand` method of the `SyntaxObjectVisitor` and passes that method this `CompileCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitCompileCommand` method.

    <!-- -->

    - #### getCompileOption

          public java.lang.String getCompileOption()

      Gets the compilation command option of this `CompileCommand`. For the default option, this method returns an empty string.
      Returns:
      A `String` that contains the compilation command option of this `CompileCommand`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ComparisonCondition.md)
- [Next Class](Condition.md)

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
