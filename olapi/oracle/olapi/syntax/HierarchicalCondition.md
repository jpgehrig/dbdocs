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

- [Prev Class](GroupCommand.md)
- [Next Class](IdentifierArgument.md)

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

## Class HierarchicalCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - oracle.olapi.syntax.HierarchicalCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class HierarchicalCondition
      extends Condition

  A `Condition` that tests whether a member of a hierarchy has the specified hierarchical relationship to itself or to another member of the hierarchy.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                  |
    |---------------------------|----------------------------------------------------------------------------------------|
    | `static java.lang.String` | `ANCESTOR`<br>A constant that indicates an ancestor relationship.                      |
    | `static java.lang.String` | `CHILD`<br>A constant that indicates a child relationship.                             |
    | `static java.lang.String` | `DESCENDANT`<br>A constant that indicates a descendant relationship.                   |
    | `static java.lang.String` | `LEAF_DESCENDANT`<br>A constant that indicates a lowest-level descendant relationship. |
    | `static java.lang.String` | `PARENT`<br>A constant that indicates a parent relationship.                           |
    | `static java.lang.String` | `RELATIVE`<br>A constant that indicates a relative relationship.                       |
    | `static java.lang.String` | `ROOT_ANCESTOR`<br>A constant that indicates a top-level ancestor relationship.        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `HierarchicalCondition``(`[`TypedExpression`](TypedExpression.md)` baseExpression, java.lang.String relationship, `[`TypedExpression`](TypedExpression.md)` referenceExpression, `[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)` hierarchy)`<br>Creates a `HierarchicalCondition` that evaluates to `true` if the `baseExpression` member of the `hierarchy` has the specified `relationship` to the `referenceExpression` member.                                      |
    | `HierarchicalCondition``(`[`TypedExpression`](TypedExpression.md)` baseExpression, java.lang.String relationship, `[`TypedExpression`](TypedExpression.md)` referenceExpression, `[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)` hierarchy, boolean negate)`<br>Creates a `HierarchicalCondition` that evaluates to `true` if the `baseExpression` member of the `hierarchy` has the specified `relationship` to the `referenceExpression` member.                      |
    | `HierarchicalCondition``(`[`TypedExpression`](TypedExpression.md)` baseExpression, java.lang.String relationship, `[`TypedExpression`](TypedExpression.md)` referenceExpression, `[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)` hierarchy, boolean negate, boolean includeSelf)`<br>Creates a `HierarchicalCondition` that evaluates to `true` if the `baseExpression` member of the `hierarchy` has the specified `relationship` to the `referenceExpression` member. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                            |
    |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md)           | `getBaseExpression``()`<br>Gets the `TypedExpression` that evaluates to the member of the hierarchy that is the base of the condition test.                                                                                                       |
    | [`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md) | `getHierarchy``()`<br>Gets the `MdmHierarchy` that contains the base and referenced members to test for the relationship.                                                                                                                         |
    | `java.lang.String`                                | `getHierarchyID``()`<br>Gets the ID of the `MdmHierarchy` that contains the base and referenced members to test for the hierarchical relationship.                                                                                                |
    | [`TypedExpression`](TypedExpression.md)           | `getReferenceExpression``()`<br>Gets the `TypedExpression` that evaluates to the member of the hierarchy that is the reference of the condition test.                                                                                             |
    | `java.lang.String`                                | `getRelationship``()`<br>Gets the hieararchical relationship for which this `HierarchicalCondition` tests.                                                                                                                                        |
    | `boolean`                                         | `includeSelf``()`<br>Indicates whether or not the base member is included in the members that have the specified relationship.                                                                                                                    |
    | `boolean`                                         | `isNegated``()`<br>Indicates whether this `HierarchicalCondition` tests for the negation of hierarchical relationship.                                                                                                                            |
    | `java.lang.Object`                                | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitHierarchicalCondition` method of the `SyntaxObjectVisitor` and passes that method this `HierarchicalCondition` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[Condition](Condition.md)

      [`and`](Condition.md)`, `[`isCompositeObject`](Condition.md)`, `[`not`](Condition.md)`, `[`or`](Condition.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PARENT

          public static final java.lang.String PARENT

      A constant that indicates a parent relationship.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CHILD

          public static final java.lang.String CHILD

      A constant that indicates a child relationship.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ANCESTOR

          public static final java.lang.String ANCESTOR

      A constant that indicates an ancestor relationship.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ROOT_ANCESTOR

          public static final java.lang.String ROOT_ANCESTOR

      A constant that indicates a top-level ancestor relationship.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DESCENDANT

          public static final java.lang.String DESCENDANT

      A constant that indicates a descendant relationship.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LEAF_DESCENDANT

          public static final java.lang.String LEAF_DESCENDANT

      A constant that indicates a lowest-level descendant relationship.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RELATIVE

          public static final java.lang.String RELATIVE

      A constant that indicates a relative relationship.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### HierarchicalCondition

          public HierarchicalCondition(TypedExpression baseExpression,
                                       java.lang.String relationship,
                                       TypedExpression referenceExpression,
                                       MdmHierarchy hierarchy,
                                       boolean negate,
                                       boolean includeSelf)

      Creates a `HierarchicalCondition` that evaluates to `true` if the `baseExpression` member of the `hierarchy` has the specified `relationship` to the `referenceExpression` member. If the `includeSelf` parameter is `true`, then the condition evaluates to `true` if the `baseExpression` member and the `referenceExpression` member are the same. If the `negate` parameter is `true`, then the condition evaluates to `true` if the `baseExpression` member does not have the specified relationship with the `referenceExpression` member.
      Parameters:
      `baseExpression` - A `TypedExpression` that evaluates to a member of a dimension hierarchy.

      `relationship` - The value of one of the constants of this class that indicates the relationship to test.

      `referenceExpression` - A `TypedExpression` that evaluates to a member of the dimension hierarchy.

      `hierarchy` - The `MdmHierarchy` that contains the members of the hierarchy.

      `negate` - A `boolean` that if `true` causes the `HierarchicalCondition` to evaluate to `true` if the base member does not have the specified relationship to the referenced member; if this parameter is `false`, then the condition evaluates to `true` if the base member does have the specified relationship to the referenced member.

      `includeSelf` - A `boolean` that specifies whether or not to include the `baseExpression` member as a `referenceExpression` member that has the specified `relationship`.

    <!-- -->

    - #### HierarchicalCondition

          public HierarchicalCondition(TypedExpression baseExpression,
                                       java.lang.String relationship,
                                       TypedExpression referenceExpression,
                                       MdmHierarchy hierarchy,
                                       boolean negate)

      Creates a `HierarchicalCondition` that evaluates to `true` if the `baseExpression` member of the `hierarchy` has the specified `relationship` to the `referenceExpression` member. If the `negate` parameter is `true`, then the condition evaluates to `true` if the `baseExpression` member does not have the specified relationship with the `referenceExpression` member.
      Parameters:
      `baseExpression` - A `TypedExpression` that evaluates to a member of a dimension hierarchy.

      `relationship` - The value of one of the constants of this class that indicates the relationship to test.

      `referenceExpression` - A `TypedExpression` that evaluates to another member of the dimension hierarchy.

      `hierarchy` - The `MdmHierarchy` that contains the members of the hierarchy.

      `negate` - A `boolean` that if `true` causes the `HierarchicalCondition` to evaluate to `true` if the base member does not have the specified relationship to the referenced member; if this parameter is `false`, then the condition evaluates to `true` if the base member does have the specified relationship to the referenced member.

    <!-- -->

    - #### HierarchicalCondition

          public HierarchicalCondition(TypedExpression baseExpression,
                                       java.lang.String relationship,
                                       TypedExpression referenceExpression,
                                       MdmHierarchy hierarchy)

      Creates a `HierarchicalCondition` that evaluates to `true` if the `baseExpression` member of the `hierarchy` has the specified `relationship` to the `referenceExpression` member.
      Parameters:
      `baseExpression` - A `TypedExpression` that evaluates to a member of a dimension hierarchy.

      `relationship` - The value of one of the constants of this class that indicates the relationship to test.

      `referenceExpression` - A `TypedExpression` that evaluates to another member of the dimension hierarchy.

      `hierarchy` - The `MdmHierarchy` that contains the members of the hierarchy.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitHierarchicalCondition` method of the `SyntaxObjectVisitor` and passes that method this `HierarchicalCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitHierarchicalCondition` method.

    <!-- -->

    - #### getBaseExpression

          public TypedExpression getBaseExpression()

      Gets the `TypedExpression` that evaluates to the member of the hierarchy that is the base of the condition test.
      Returns:
      A `TypedExpression` that evaluates to the base of the condition.

    <!-- -->

    - #### getReferenceExpression

          public TypedExpression getReferenceExpression()

      Gets the `TypedExpression` that evaluates to the member of the hierarchy that is the reference of the condition test.
      Returns:
      A `TypedExpression` that evaluates to the reference of the condition.

    <!-- -->

    - #### getHierarchy

          public MdmHierarchy getHierarchy()

      Gets the `MdmHierarchy` that contains the base and referenced members to test for the relationship.
      Returns:
      A `MdmHierarchy` that contains the members to test.

    <!-- -->

    - #### getHierarchyID

          public java.lang.String getHierarchyID()

      Gets the ID of the `MdmHierarchy` that contains the base and referenced members to test for the hierarchical relationship.
      Returns:
      A `String` that contains the ID of the `MdmHierarchy` that contains the members to test.

    <!-- -->

    - #### getRelationship

          public java.lang.String getRelationship()

      Gets the hieararchical relationship for which this `HierarchicalCondition` tests. The relationships are represented by the constants of this class, such as `PARENT` and `ANCESTOR`.
      Returns:
      A `String` that has the value of one of the constants of this class.

    <!-- -->

    - #### isNegated

          public boolean isNegated()

      Indicates whether this `HierarchicalCondition` tests for the negation of hierarchical relationship. For example, if this method returns `true`, then the `HierarchicalCondition` evaluates to `true` if the base expression does not have the specified relationship to the reference expression.
      Returns:
      A `boolean` that indicates whether this `HierarchicalCondition` tests for the negation of the condition.

    <!-- -->

    - #### includeSelf

          public boolean includeSelf()

      Indicates whether or not the base member is included in the members that have the specified relationship.
      Returns:
      A `boolean` that is `true` if the condition includes the base member as a member that has the specified relationship or `false` if it excludes the base member.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](GroupCommand.md)
- [Next Class](IdentifierArgument.md)

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
