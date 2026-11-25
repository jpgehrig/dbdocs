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

- [Prev Class](AggregateOverClause.md)
- [Next Class](AggregationCase.md)

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

## Class AggregateOverMembersClause

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.AggregateOverClause](AggregateOverClause.md)

    - - oracle.olapi.syntax.AggregateOverMembersClause

<!-- -->

-

  ------------------------------------------------------------------------



      public final class AggregateOverMembersClause
      extends AggregateOverClause

  An `AggregateOverClause` that specifies a list of dimension members as the `OVER` clause for an `AggregationFunctionExpression`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                   |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AggregateOverMembersClause``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, java.util.List<java.lang.String> members)`<br>Creates an `AggregateOverMembersClause` that specifies members of a dimension as the `OVER` clause for an `AggregationFunctionExpression`. |
    | `AggregateOverMembersClause``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, java.lang.String[] members)`<br>Creates an `AggregateOverMembersClause` that specifies members of a dimension as the `OVER` clause for an `AggregationFunctionExpression`.               |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                                                      |
    |-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md) | `getDimension``()`<br>Gets the `MdmPrimaryDimension` that contains the members to use in the aggregation.                                                                                                                                                   |
    | `java.lang.String`                                              | `getDimensionID``()`<br>Gets the ID of the `MdmPrimaryDimension` that contains the members to use in the aggregation.                                                                                                                                       |
    | `java.lang.String[]`                                            | `getMembers``()`<br>Gets the dimension members to use in the aggregation.                                                                                                                                                                                   |
    | `java.lang.Object`                                              | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitAggregateOverMembersClause` method of the `SyntaxObjectVisitor` and passes that method this `AggregateOverMembersClause` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AggregateOverMembersClause

          public AggregateOverMembersClause(MdmPrimaryDimension dim,
                                            java.lang.String[] members)

      Creates an `AggregateOverMembersClause` that specifies members of a dimension as the `OVER` clause for an `AggregationFunctionExpression`.
      Parameters:
      `dim` - An `MdmPrimaryDimension`.

      `members` - An array of `String` objects that specify members of the dimension.

    <!-- -->

    - #### AggregateOverMembersClause

          public AggregateOverMembersClause(MdmPrimaryDimension dim,
                                            java.util.List<java.lang.String> members)

      Creates an `AggregateOverMembersClause` that specifies members of a dimension as the `OVER` clause for an `AggregationFunctionExpression`.
      Parameters:
      `dim` - An `MdmPrimaryDimension`.

      `members` - A `List` of `String` objects that specify members of the dimension.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitAggregateOverMembersClause` method of the `SyntaxObjectVisitor` and passes that method this `AggregateOverMembersClause` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitAggregateOverMembersClause` method.

    <!-- -->

    - #### getDimension

          public MdmPrimaryDimension getDimension()

      Gets the `MdmPrimaryDimension` that contains the members to use in the aggregation.
      Returns:
      The `MdmPrimaryDimension` that is associated with this `AggregateOverMembersClause`.

    <!-- -->

    - #### getDimensionID

          public java.lang.String getDimensionID()

      Gets the ID of the `MdmPrimaryDimension` that contains the members to use in the aggregation.
      Returns:
      A `String` that contains the ID of the dimension associated with this `AggregateOverMembersClause`.

    <!-- -->

    - #### getMembers

          public java.lang.String[] getMembers()

      Gets the dimension members to use in the aggregation.
      Returns:
      An array of `String` objects that contain the dimension members to use in the aggregation.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AggregateOverClause.md)
- [Next Class](AggregationCase.md)

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
