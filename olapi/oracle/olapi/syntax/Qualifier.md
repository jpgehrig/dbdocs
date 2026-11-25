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

- [Prev Class](QDRExpression.md)
- [Next Class](Query.md)

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

## Class Qualifier

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.Qualifier

<!-- -->

-

  ------------------------------------------------------------------------



      public final class Qualifier
      extends DataObject

  A `DataObject` that represents a dimension member for a `QDRExpression`. A `Qualifier` has an associated `MdmPrimaryDimension` and a `TypedExpression` that evaluates to a member of the dimension.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Qualifier``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dimension, `[`TypedExpression`](TypedExpression.md)` expression)`<br>Creates a `Qualifier` that has the specified dimension member. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                    |
    |-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md) | `getDimension``()`<br>Gets the dimension that is associated with this `Qualifier`.                                                                                                                                        |
    | `java.lang.String`                                              | `getDimensionID``()`<br>Gets the ID of the dimension that is associated with this `Qualifier`.                                                                                                                            |
    | [`TypedExpression`](TypedExpression.md)                         | `getExpression``()`<br>Gets the expression of this `Qualifier`, which evaluates to a dimension member.                                                                                                                    |
    | `boolean`                                                       | `isCompositeObject``()`<br>Indicates whether this `Qualifier` contains other `SyntaxObject` objects.                                                                                                                      |
    | `java.lang.Object`                                              | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitQualifier` method of the `SyntaxObjectVisitor` and passes that method this `Qualifier` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Qualifier

          public Qualifier(MdmPrimaryDimension dimension,
                           TypedExpression expression)

      Creates a `Qualifier` that has the specified dimension member.
      Parameters:
      `dimension` - An `MdmPrimaryDimension`.

      `expression` - A `TypedExpression` that evaluates to a member of the dimension.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitQualifier` method of the `SyntaxObjectVisitor` and passes that method this `Qualifier` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitQualifier` method.

    <!-- -->

    - #### getDimension

          public MdmPrimaryDimension getDimension()

      Gets the dimension that is associated with this `Qualifier`.
      Returns:
      An `MdmPrimaryDimension`.

    <!-- -->

    - #### getDimensionID

          public java.lang.String getDimensionID()

      Gets the ID of the dimension that is associated with this `Qualifier`.
      Returns:
      A `String` that contains the ID of the `MdmPrimaryDimension` associated with this `Qualifier`.

    <!-- -->

    - #### getExpression

          public TypedExpression getExpression()

      Gets the expression of this `Qualifier`, which evaluates to a dimension member.
      Returns:
      A `TypedExpression` that evaluates to a member of the specified dimension.

    <!-- -->

    - #### isCompositeObject

          public boolean isCompositeObject()

      Indicates whether this `Qualifier` contains other `SyntaxObject` objects. Because a `Qualifier` contains a `TypedExpression`, this method returns `true`.
      Returns:
      A `boolean` that is `true` if this `Qualifier` contains other `SyntaxObject` objects or `false` if it does not.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](QDRExpression.md)
- [Next Class](Query.md)

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
