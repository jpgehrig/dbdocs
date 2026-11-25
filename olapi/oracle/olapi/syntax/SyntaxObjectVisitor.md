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

- [Prev Class](SyntaxObject.md)
- [Next Class](TimeZoneExpression.md)

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

## Class SyntaxObjectVisitor

- java.lang.Object

- - oracle.olapi.syntax.SyntaxObjectVisitor

<!-- -->

-

  ------------------------------------------------------------------------



      public class SyntaxObjectVisitor
      extends java.lang.Object

  A visitor class for the `SyntaxObject` class hierarchy.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                       |
    |-------------------------------------------------------------------|
    | `SyntaxObjectVisitor``()`<br>Creates a new `SyntaxObjectVisitor`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                  |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visitAggregateOverClause``(`[`AggregateOverClause`](AggregateOverClause.md)` object, java.lang.Object context)`<br>Executes operations on the specified `AggregateOverClause`.                                         |
    | `java.lang.Object` | `visitAggregateOverMembersClause``(`[`AggregateOverMembersClause`](AggregateOverMembersClause.md)` object, java.lang.Object context)`<br>Executes operations on the specified `AggregateOverMembersClause`.             |
    | `java.lang.Object` | `visitAggregationCase``(`[`AggregationCase`](AggregationCase.md)` object, java.lang.Object context)`<br>Executes operations on the specified `AggregationCase`.                                                         |
    | `java.lang.Object` | `visitAggregationCommand``(`[`AggregationCommand`](AggregationCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `AggregationCommand`.                                             |
    | `java.lang.Object` | `visitAggregationFunctionExpression``(`[`AggregationFunctionExpression`](AggregationFunctionExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `AggregationFunctionExpression`. |
    | `java.lang.Object` | `visitAnalyzeCommand``(`[`AnalyzeCommand`](AnalyzeCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `AnalyzeCommand`.                                                             |
    | `java.lang.Object` | `visitAssignmentCommand``(`[`AssignmentCommand`](AssignmentCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `AssignmentCommand`.                                                 |
    | `java.lang.Object` | `visitBaseQuery``(`[`BaseQuery`](BaseQuery.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BaseQuery`.                                                                                 |
    | `java.lang.Object` | `visitBetweenCondition``(`[`BetweenCondition`](BetweenCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BetweenCondition`.                                                     |
    | `java.lang.Object` | `visitBinaryOperatorCondition``(`[`BinaryOperatorCondition`](BinaryOperatorCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BinaryOperatorCondition`.                         |
    | `java.lang.Object` | `visitBinaryOperatorExpression``(`[`BinaryOperatorExpression`](BinaryOperatorExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BinaryOperatorExpression`.                     |
    | `java.lang.Object` | `visitBuildCommand``(`[`BuildCommand`](BuildCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BuildCommand`.                                                                     |
    | `java.lang.Object` | `visitBuildItem``(`[`BuildItem`](BuildItem.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BuildItem`.                                                                                 |
    | `java.lang.Object` | `visitBuildProcess``(`[`BuildProcess`](BuildProcess.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BuildProcess`.                                                                     |
    | `java.lang.Object` | `visitBuildSpecification``(`[`BuildSpecification`](BuildSpecification.md)` object, java.lang.Object context)`<br>Executes operations on the specified `BuildSpecification`.                                             |
    | `java.lang.Object` | `visitCaseExpression``(`[`CaseExpression`](CaseExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `CaseExpression`.                                                             |
    | `java.lang.Object` | `visitClearCommand``(`[`ClearCommand`](ClearCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `ClearCommand`.                                                                     |
    | `java.lang.Object` | `visitColumnExpression``(`[`ColumnExpression`](ColumnExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `ColumnExpression`.                                                     |
    | `java.lang.Object` | `visitComparisonCondition``(`[`ComparisonCondition`](ComparisonCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `ComparisonCondition`.                                         |
    | `java.lang.Object` | `visitCompileCommand``(`[`CompileCommand`](CompileCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `CompileCommand`.                                                             |
    | `java.lang.Object` | `visitCondition``(`[`Condition`](Condition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `Condition`.                                                                                 |
    | `java.lang.Object` | `visitConsistentSolveSpecification``(`[`ConsistentSolveSpecification`](ConsistentSolveSpecification.md)` object, java.lang.Object context)`<br>Executes operations on the specified `ConsistentSolveSpecification`.     |
    | `java.lang.Object` | `visitDataObject``(`[`DataObject`](DataObject.md)` object, java.lang.Object context)`<br>Executes operations on the specified `DataObject`.                                                                             |
    | `java.lang.Object` | `visitDateExpression``(`[`DateExpression`](DateExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `DateExpression`.                                                             |
    | `java.lang.Object` | `visitDimensionArgument``(`[`DimensionArgument`](DimensionArgument.md)` object, java.lang.Object context)`<br>Executes operations on the specified `DimensionArgument`.                                                 |
    | `java.lang.Object` | `visitExpression``(`[`Expression`](Expression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `Expression`.                                                                             |
    | `java.lang.Object` | `visitFromClause``(`[`FromClause`](FromClause.md)` object, java.lang.Object context)`<br>Executes operations on the specified `FromClause`.                                                                             |
    | `java.lang.Object` | `visitFromClauseElement``(`[`FromClauseElement`](FromClauseElement.md)` object, java.lang.Object context)`<br>Executes operations on the specified `FromClauseElement`.                                                 |
    | `java.lang.Object` | `visitFunctionCondition``(`[`FunctionCondition`](FunctionCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `FunctionCondition`.                                                 |
    | `java.lang.Object` | `visitGroupCommand``(`[`GroupCommand`](GroupCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `GroupCommand`.                                                                     |
    | `java.lang.Object` | `visitHierarchicalCondition``(`[`HierarchicalCondition`](HierarchicalCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `HierarchicalCondition`.                                 |
    | `java.lang.Object` | `visitIdentifierArgument``(`[`IdentifierArgument`](IdentifierArgument.md)` object, java.lang.Object context)`<br>Executes operations on the specified `IdentifierArgument`.                                             |
    | `java.lang.Object` | `visitIntervalExpression``(`[`IntervalExpression`](IntervalExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `IntervalExpression`.                                             |
    | `java.lang.Object` | `visitIntervalLiteralExpression``(`[`IntervalLiteralExpression`](IntervalLiteralExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `IntervalLiteralExpression`.                 |
    | `java.lang.Object` | `visitIsCondition``(`[`IsCondition`](IsCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `IsCondition`.                                                                         |
    | `java.lang.Object` | `visitKeywordArgument``(`[`KeywordArgument`](KeywordArgument.md)` object, java.lang.Object context)`<br>Executes operations on the specified `KeywordArgument`.                                                         |
    | `java.lang.Object` | `visitLikeCondition``(`[`LikeCondition`](LikeCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `LikeCondition`.                                                                 |
    | `java.lang.Object` | `visitListComparisonCondition``(`[`ListComparisonCondition`](ListComparisonCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `ListComparisonCondition`.                         |
    | `java.lang.Object` | `visitLiteralExpression``(`[`LiteralExpression`](LiteralExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `LiteralExpression`.                                                 |
    | `java.lang.Object` | `visitLoadCommand``(`[`LoadCommand`](LoadCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `LoadCommand`.                                                                         |
    | `java.lang.Object` | `visitModelCommand``(`[`ModelCommand`](ModelCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `ModelCommand`.                                                                     |
    | `java.lang.Object` | `visitNotCondition``(`[`NotCondition`](NotCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `NotCondition`.                                                                     |
    | `java.lang.Object` | `visitNullExpression``(`[`NullExpression`](NullExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `NullExpression`.                                                             |
    | `java.lang.Object` | `visitNumberExpression``(`[`NumberExpression`](NumberExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `NumberExpression`.                                                     |
    | `java.lang.Object` | `visitOLAPDMLCommand``(`[`OLAPDMLCommand`](OLAPDMLCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `OLAPDMLCommand`.                                                             |
    | `java.lang.Object` | `visitOLAPDMLExpression``(`[`OLAPDMLExpression`](OLAPDMLExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `OLAPDMLExpression`.                                                 |
    | `java.lang.Object` | `visitOLAPFunctionExpression``(`[`OLAPFunctionExpression`](OLAPFunctionExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `OLAPFunctionExpression`.                             |
    | `java.lang.Object` | `visitOrderByClause``(`[`OrderByClause`](OrderByClause.md)` object, java.lang.Object context)`<br>Executes operations on the specified `OrderByClause`.                                                                 |
    | `java.lang.Object` | `visitOrderByElement``(`[`OrderByElement`](OrderByElement.md)` object, java.lang.Object context)`<br>Executes operations on the specified `OrderByElement`.                                                             |
    | `java.lang.Object` | `visitPlaceholderExpression``(`[`PlaceholderExpression`](PlaceholderExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `PlaceholderExpression`.                                 |
    | `java.lang.Object` | `visitPLSQLCommand``(`[`PLSQLCommand`](PLSQLCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `PLSQLCommand`.                                                                     |
    | `java.lang.Object` | `visitQDRExpression``(`[`QDRExpression`](QDRExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `QDRExpression`.                                                                 |
    | `java.lang.Object` | `visitQualifier``(`[`Qualifier`](Qualifier.md)` object, java.lang.Object context)`<br>Executes operations on the specified `Qualifier`.                                                                                 |
    | `java.lang.Object` | `visitQuery``(`[`Query`](Query.md)` object, java.lang.Object context)`<br>Executes operations on the specified `Query`.                                                                                                 |
    | `java.lang.Object` | `visitRowExpression``(`[`RowExpression`](RowExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `RowExpression`.                                                                 |
    | `java.lang.Object` | `visitRowFunctionExpression``(`[`RowFunctionExpression`](RowFunctionExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `RowFunctionExpression`.                                 |
    | `java.lang.Object` | `visitSearchedCase``(`[`SearchedCase`](SearchedCase.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SearchedCase`.                                                                     |
    | `java.lang.Object` | `visitSearchedCaseExpression``(`[`SearchedCaseExpression`](SearchedCaseExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SearchedCaseExpression`.                             |
    | `java.lang.Object` | `visitSimpleCase``(`[`SimpleCase`](SimpleCase.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SimpleCase`.                                                                             |
    | `java.lang.Object` | `visitSimpleCaseExpression``(`[`SimpleCaseExpression`](SimpleCaseExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SimpleCaseExpression`.                                     |
    | `java.lang.Object` | `visitSimpleCommand``(`[`SimpleCommand`](SimpleCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SimpleCommand`.                                                                 |
    | `java.lang.Object` | `visitSolveCommand``(`[`SolveCommand`](SolveCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SolveCommand`.                                                                     |
    | `java.lang.Object` | `visitSolveStepCommand``(`[`SolveStepCommand`](SolveStepCommand.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SolveStepCommand`.                                                     |
    | `java.lang.Object` | `visitSQLDataType``(`[`SQLDataType`](SQLDataType.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SQLDataType`.                                                                         |
    | `java.lang.Object` | `visitStarArgument``(`[`StarArgument`](StarArgument.md)` object, java.lang.Object context)`<br>Executes operations on the specified `StarArgument`.                                                                     |
    | `java.lang.Object` | `visitStringExpression``(`[`StringExpression`](StringExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `StringExpression`.                                                     |
    | `java.lang.Object` | `visitSymmetricCondition``(`[`SymmetricCondition`](SymmetricCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SymmetricCondition`.                                             |
    | `java.lang.Object` | `visitSymmetricConditionElement``(`[`SymmetricConditionElement`](SymmetricConditionElement.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SymmetricConditionElement`.                 |
    | `java.lang.Object` | `visitSyntaxObject``(`[`SyntaxObject`](SyntaxObject.md)` object, java.lang.Object context)`<br>Executes operations on the specified `SyntaxObject`.                                                                     |
    | `java.lang.Object` | `visitTimeZoneExpression``(`[`TimeZoneExpression`](TimeZoneExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `TimeZoneExpression`.                                             |
    | `java.lang.Object` | `visitTypedExpression``(`[`TypedExpression`](TypedExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `TypedExpression`.                                                         |
    | `java.lang.Object` | `visitUnaryOperatorExpression``(`[`UnaryOperatorExpression`](UnaryOperatorExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `UnaryOperatorExpression`.                         |
    | `java.lang.Object` | `visitUnresolvedDimensionArgument``(`[`DimensionArgument`](DimensionArgument.md)` object, java.lang.Object context)`<br>Executes operations on the specified `UnresolvedDimensionArgument`.                             |
    | `java.lang.Object` | `visitUnresolvedExpression``(`[`UnresolvedExpression`](UnresolvedExpression.md)` object, java.lang.Object context)`<br>Executes operations on the specified `UnresolvedExpression`.                                     |
    | `java.lang.Object` | `visitUnresolvedQuery``(`[`UnresolvedQuery`](UnresolvedQuery.md)` object, java.lang.Object context)`<br>Executes operations on the specified `UnresolvedQuery`.                                                         |
    | `java.lang.Object` | `visitValueComparisonCondition``(`[`ValueComparisonCondition`](ValueComparisonCondition.md)` object, java.lang.Object context)`<br>Executes operations on the specified `ValueComparisonCondition`.                     |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SyntaxObjectVisitor

          public SyntaxObjectVisitor()

      Creates a new `SyntaxObjectVisitor`.

  <!-- -->

  - ### Method Detail

    - #### visitAggregateOverClause

          public java.lang.Object visitAggregateOverClause(AggregateOverClause object,
                                                           java.lang.Object context)

      Executes operations on the specified `AggregateOverClause`.
      Parameters:
      `object` - An `AggregateOverClause`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitAggregateOverMembersClause

          public java.lang.Object visitAggregateOverMembersClause(AggregateOverMembersClause object,
                                                                  java.lang.Object context)

      Executes operations on the specified `AggregateOverMembersClause`.
      Parameters:
      `object` - An `AggregateOverMembersClause`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitAggregationCase

          public java.lang.Object visitAggregationCase(AggregationCase object,
                                                       java.lang.Object context)

      Executes operations on the specified `AggregationCase`.
      Parameters:
      `object` - An `AggregationCase`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitAggregationCommand

          public java.lang.Object visitAggregationCommand(AggregationCommand object,
                                                          java.lang.Object context)

      Executes operations on the specified `AggregationCommand`.
      Parameters:
      `object` - An `AggregationCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitAggregationFunctionExpression

          public java.lang.Object visitAggregationFunctionExpression(AggregationFunctionExpression object,
                                                                     java.lang.Object context)

      Executes operations on the specified `AggregationFunctionExpression`.
      Parameters:
      `object` - An `AggregationFunctionExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitAnalyzeCommand

          public java.lang.Object visitAnalyzeCommand(AnalyzeCommand object,
                                                      java.lang.Object context)

      Executes operations on the specified `AnalyzeCommand`.
      Parameters:
      `object` - An `AnalyzeCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitAssignmentCommand

          public java.lang.Object visitAssignmentCommand(AssignmentCommand object,
                                                         java.lang.Object context)

      Executes operations on the specified `AssignmentCommand`.
      Parameters:
      `object` - An `AssignmentCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBaseQuery

          public java.lang.Object visitBaseQuery(BaseQuery object,
                                                 java.lang.Object context)

      Executes operations on the specified `BaseQuery`.
      Parameters:
      `object` - A `BaseQuery`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBetweenCondition

          public java.lang.Object visitBetweenCondition(BetweenCondition object,
                                                        java.lang.Object context)

      Executes operations on the specified `BetweenCondition`.
      Parameters:
      `object` - A `BetweenCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBinaryOperatorCondition

          public java.lang.Object visitBinaryOperatorCondition(BinaryOperatorCondition object,
                                                               java.lang.Object context)

      Executes operations on the specified `BinaryOperatorCondition`.
      Parameters:
      `object` - A `BinaryOperatorCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBinaryOperatorExpression

          public java.lang.Object visitBinaryOperatorExpression(BinaryOperatorExpression object,
                                                                java.lang.Object context)

      Executes operations on the specified `BinaryOperatorExpression`.
      Parameters:
      `object` - A `BinaryOperatorExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBuildItem

          public java.lang.Object visitBuildItem(BuildItem object,
                                                 java.lang.Object context)

      Executes operations on the specified `BuildItem`.
      Parameters:
      `object` - A `BuildItem`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBuildProcess

          public java.lang.Object visitBuildProcess(BuildProcess object,
                                                    java.lang.Object context)

      Executes operations on the specified `BuildProcess`.
      Parameters:
      `object` - A `BuildProcess`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBuildSpecification

          public java.lang.Object visitBuildSpecification(BuildSpecification object,
                                                          java.lang.Object context)

      Executes operations on the specified `BuildSpecification`.
      Parameters:
      `object` - A `BuildSpecification`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitColumnExpression

          public java.lang.Object visitColumnExpression(ColumnExpression object,
                                                        java.lang.Object context)

      Executes operations on the specified `ColumnExpression`.
      Parameters:
      `object` - A `ColumnExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitCaseExpression

          public java.lang.Object visitCaseExpression(CaseExpression object,
                                                      java.lang.Object context)

      Executes operations on the specified `CaseExpression`.
      Parameters:
      `object` - A `CaseExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitBuildCommand

          public java.lang.Object visitBuildCommand(BuildCommand object,
                                                    java.lang.Object context)

      Executes operations on the specified `BuildCommand`.
      Parameters:
      `object` - A `BuildCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitComparisonCondition

          public java.lang.Object visitComparisonCondition(ComparisonCondition object,
                                                           java.lang.Object context)

      Executes operations on the specified `ComparisonCondition`.
      Parameters:
      `object` - A `ComparisonCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitCompileCommand

          public java.lang.Object visitCompileCommand(CompileCommand object,
                                                      java.lang.Object context)

      Executes operations on the specified `CompileCommand`.
      Parameters:
      `object` - A `CompileCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitCondition

          public java.lang.Object visitCondition(Condition object,
                                                 java.lang.Object context)

      Executes operations on the specified `Condition`.
      Parameters:
      `object` - A `Condition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitConsistentSolveSpecification

          public java.lang.Object visitConsistentSolveSpecification(ConsistentSolveSpecification object,
                                                                    java.lang.Object context)

      Executes operations on the specified `ConsistentSolveSpecification`.
      Parameters:
      `object` - A `ConsistentSolveSpecification`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitDataObject

          public java.lang.Object visitDataObject(DataObject object,
                                                  java.lang.Object context)

      Executes operations on the specified `DataObject`.
      Parameters:
      `object` - A `DataObject`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitDateExpression

          public java.lang.Object visitDateExpression(DateExpression object,
                                                      java.lang.Object context)

      Executes operations on the specified `DateExpression`.
      Parameters:
      `object` - A `DateExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitUnresolvedDimensionArgument

          public java.lang.Object visitUnresolvedDimensionArgument(DimensionArgument object,
                                                                   java.lang.Object context)

      Executes operations on the specified `UnresolvedDimensionArgument`.
      Parameters:
      `object` - A `UnresolvedDimensionArgument`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitDimensionArgument

          public java.lang.Object visitDimensionArgument(DimensionArgument object,
                                                         java.lang.Object context)

      Executes operations on the specified `DimensionArgument`.
      Parameters:
      `object` - A `DimensionArgument`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitExpression

          public java.lang.Object visitExpression(Expression object,
                                                  java.lang.Object context)

      Executes operations on the specified `Expression`.
      Parameters:
      `object` - A `Expression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitFunctionCondition

          public java.lang.Object visitFunctionCondition(FunctionCondition object,
                                                         java.lang.Object context)

      Executes operations on the specified `FunctionCondition`.
      Parameters:
      `object` - A `FunctionCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitGroupCommand

          public java.lang.Object visitGroupCommand(GroupCommand object,
                                                    java.lang.Object context)

      Executes operations on the specified `GroupCommand`.
      Parameters:
      `object` - A `GroupCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitHierarchicalCondition

          public java.lang.Object visitHierarchicalCondition(HierarchicalCondition object,
                                                             java.lang.Object context)

      Executes operations on the specified `HierarchicalCondition`.
      Parameters:
      `object` - A `HierarchicalCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitIdentifierArgument

          public java.lang.Object visitIdentifierArgument(IdentifierArgument object,
                                                          java.lang.Object context)

      Executes operations on the specified `IdentifierArgument`.
      Parameters:
      `object` - An `IdentifierArgument`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitIntervalExpression

          public java.lang.Object visitIntervalExpression(IntervalExpression object,
                                                          java.lang.Object context)

      Executes operations on the specified `IntervalExpression`.
      Parameters:
      `object` - An `IntervalExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitIntervalLiteralExpression

          public java.lang.Object visitIntervalLiteralExpression(IntervalLiteralExpression object,
                                                                 java.lang.Object context)

      Executes operations on the specified `IntervalLiteralExpression`.
      Parameters:
      `object` - An `IntervalLiteralExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitIsCondition

          public java.lang.Object visitIsCondition(IsCondition object,
                                                   java.lang.Object context)

      Executes operations on the specified `IsCondition`.
      Parameters:
      `object` - An `IsCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitKeywordArgument

          public java.lang.Object visitKeywordArgument(KeywordArgument object,
                                                       java.lang.Object context)

      Executes operations on the specified `KeywordArgument`.
      Parameters:
      `object` - A `KeywordArgument`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitLikeCondition

          public java.lang.Object visitLikeCondition(LikeCondition object,
                                                     java.lang.Object context)

      Executes operations on the specified `LikeCondition`.
      Parameters:
      `object` - A `LikeCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitListComparisonCondition

          public java.lang.Object visitListComparisonCondition(ListComparisonCondition object,
                                                               java.lang.Object context)

      Executes operations on the specified `ListComparisonCondition`.
      Parameters:
      `object` - A `ListComparisonCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitLiteralExpression

          public java.lang.Object visitLiteralExpression(LiteralExpression object,
                                                         java.lang.Object context)

      Executes operations on the specified `LiteralExpression`.
      Parameters:
      `object` - A `LiteralExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitModelCommand

          public java.lang.Object visitModelCommand(ModelCommand object,
                                                    java.lang.Object context)

      Executes operations on the specified `ModelCommand`.
      Parameters:
      `object` - A `ModelCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitNotCondition

          public java.lang.Object visitNotCondition(NotCondition object,
                                                    java.lang.Object context)

      Executes operations on the specified `NotCondition`.
      Parameters:
      `object` - A `NotCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitNullExpression

          public java.lang.Object visitNullExpression(NullExpression object,
                                                      java.lang.Object context)

      Executes operations on the specified `NullExpression`.
      Parameters:
      `object` - A `NullExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitNumberExpression

          public java.lang.Object visitNumberExpression(NumberExpression object,
                                                        java.lang.Object context)

      Executes operations on the specified `NumberExpression`.
      Parameters:
      `object` - A `NumberExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitOLAPDMLExpression

          public java.lang.Object visitOLAPDMLExpression(OLAPDMLExpression object,
                                                         java.lang.Object context)

      Executes operations on the specified `OLAPDMLExpression`.
      Parameters:
      `object` - An `OLAPDMLExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitOLAPFunctionExpression

          public java.lang.Object visitOLAPFunctionExpression(OLAPFunctionExpression object,
                                                              java.lang.Object context)

      Executes operations on the specified `OLAPFunctionExpression`.
      Parameters:
      `object` - An `OLAPFunctionExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitOrderByClause

          public java.lang.Object visitOrderByClause(OrderByClause object,
                                                     java.lang.Object context)

      Executes operations on the specified `OrderByClause`.
      Parameters:
      `object` - An `OrderByClause`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitOrderByElement

          public java.lang.Object visitOrderByElement(OrderByElement object,
                                                      java.lang.Object context)

      Executes operations on the specified `OrderByElement`.
      Parameters:
      `object` - An `OrderByElement`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitPlaceholderExpression

          public java.lang.Object visitPlaceholderExpression(PlaceholderExpression object,
                                                             java.lang.Object context)

      Executes operations on the specified `PlaceholderExpression`.
      Parameters:
      `object` - A `PlaceholderExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitQualifier

          public java.lang.Object visitQualifier(Qualifier object,
                                                 java.lang.Object context)

      Executes operations on the specified `Qualifier`.
      Parameters:
      `object` - A `Qualifier`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitQDRExpression

          public java.lang.Object visitQDRExpression(QDRExpression object,
                                                     java.lang.Object context)

      Executes operations on the specified `QDRExpression`.
      Parameters:
      `object` - A `QDRExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitRowExpression

          public java.lang.Object visitRowExpression(RowExpression object,
                                                     java.lang.Object context)

      Executes operations on the specified `RowExpression`.
      Parameters:
      `object` - A `RowExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitRowFunctionExpression

          public java.lang.Object visitRowFunctionExpression(RowFunctionExpression object,
                                                             java.lang.Object context)

      Executes operations on the specified `RowFunctionExpression`.
      Parameters:
      `object` - A `RowFunctionExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSearchedCase

          public java.lang.Object visitSearchedCase(SearchedCase object,
                                                    java.lang.Object context)

      Executes operations on the specified `SearchedCase`.
      Parameters:
      `object` - A `SearchedCase`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSearchedCaseExpression

          public java.lang.Object visitSearchedCaseExpression(SearchedCaseExpression object,
                                                              java.lang.Object context)

      Executes operations on the specified `SearchedCaseExpression`.
      Parameters:
      `object` - A `SearchedCaseExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitClearCommand

          public java.lang.Object visitClearCommand(ClearCommand object,
                                                    java.lang.Object context)

      Executes operations on the specified `ClearCommand`.
      Parameters:
      `object` - A `ClearCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSimpleCase

          public java.lang.Object visitSimpleCase(SimpleCase object,
                                                  java.lang.Object context)

      Executes operations on the specified `SimpleCase`.
      Parameters:
      `object` - A `SimpleCase`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSimpleCaseExpression

          public java.lang.Object visitSimpleCaseExpression(SimpleCaseExpression object,
                                                            java.lang.Object context)

      Executes operations on the specified `SimpleCaseExpression`.
      Parameters:
      `object` - A `SimpleCaseExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitStarArgument

          public java.lang.Object visitStarArgument(StarArgument object,
                                                    java.lang.Object context)

      Executes operations on the specified `StarArgument`.
      Parameters:
      `object` - An `StarArgument`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitStringExpression

          public java.lang.Object visitStringExpression(StringExpression object,
                                                        java.lang.Object context)

      Executes operations on the specified `StringExpression`.
      Parameters:
      `object` - A `StringExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSymmetricCondition

          public java.lang.Object visitSymmetricCondition(SymmetricCondition object,
                                                          java.lang.Object context)

      Executes operations on the specified `SymmetricCondition`.
      Parameters:
      `object` - A `SymmetricCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSymmetricConditionElement

          public java.lang.Object visitSymmetricConditionElement(SymmetricConditionElement object,
                                                                 java.lang.Object context)

      Executes operations on the specified `SymmetricConditionElement`.
      Parameters:
      `object` - A `SymmetricConditionElement`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitTimeZoneExpression

          public java.lang.Object visitTimeZoneExpression(TimeZoneExpression object,
                                                          java.lang.Object context)

      Executes operations on the specified `TimeZoneExpression`.
      Parameters:
      `object` - A `TimeZoneExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitTypedExpression

          public java.lang.Object visitTypedExpression(TypedExpression object,
                                                       java.lang.Object context)

      Executes operations on the specified `TypedExpression`.
      Parameters:
      `object` - A `TypedExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitUnaryOperatorExpression

          public java.lang.Object visitUnaryOperatorExpression(UnaryOperatorExpression object,
                                                               java.lang.Object context)

      Executes operations on the specified `UnaryOperatorExpression`.
      Parameters:
      `object` - A `UnaryOperatorExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitValueComparisonCondition

          public java.lang.Object visitValueComparisonCondition(ValueComparisonCondition object,
                                                                java.lang.Object context)

      Executes operations on the specified `ValueComparisonCondition`.
      Parameters:
      `object` - A `ValueComparisonCondition`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitOLAPDMLCommand

          public java.lang.Object visitOLAPDMLCommand(OLAPDMLCommand object,
                                                      java.lang.Object context)

      Executes operations on the specified `OLAPDMLCommand`.
      Parameters:
      `object` - An `OLAPDMLCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitPLSQLCommand

          public java.lang.Object visitPLSQLCommand(PLSQLCommand object,
                                                    java.lang.Object context)

      Executes operations on the specified `PLSQLCommand`.
      Parameters:
      `object` - A `PLSQLCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitLoadCommand

          public java.lang.Object visitLoadCommand(LoadCommand object,
                                                   java.lang.Object context)

      Executes operations on the specified `LoadCommand`.
      Parameters:
      `object` - A `LoadCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSimpleCommand

          public java.lang.Object visitSimpleCommand(SimpleCommand object,
                                                     java.lang.Object context)

      Executes operations on the specified `SimpleCommand`.
      Parameters:
      `object` - A `SimpleCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSolveCommand

          public java.lang.Object visitSolveCommand(SolveCommand object,
                                                    java.lang.Object context)

      Executes operations on the specified `SolveCommand`.
      Parameters:
      `object` - A `SolveCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSQLDataType

          public java.lang.Object visitSQLDataType(SQLDataType object,
                                                   java.lang.Object context)

      Executes operations on the specified `SQLDataType`.
      Parameters:
      `object` - A `SQLDataType`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSolveStepCommand

          public java.lang.Object visitSolveStepCommand(SolveStepCommand object,
                                                        java.lang.Object context)

      Executes operations on the specified `SolveStepCommand`.
      Parameters:
      `object` - A `SolveStepCommand`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitSyntaxObject

          public java.lang.Object visitSyntaxObject(SyntaxObject object,
                                                    java.lang.Object context)

      Executes operations on the specified `SyntaxObject`.
      Parameters:
      `object` - A `SyntaxObject`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitUnresolvedExpression

          public java.lang.Object visitUnresolvedExpression(UnresolvedExpression object,
                                                            java.lang.Object context)

      Executes operations on the specified `UnresolvedExpression`.
      Parameters:
      `object` - A `UnresolvedExpression`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitUnresolvedQuery

          public java.lang.Object visitUnresolvedQuery(UnresolvedQuery object,
                                                       java.lang.Object context)

      Executes operations on the specified `UnresolvedQuery`.
      Parameters:
      `object` - A `UnresolvedQuery`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitQuery

          public java.lang.Object visitQuery(Query object,
                                             java.lang.Object context)

      Executes operations on the specified `Query`.
      Parameters:
      `object` - A `Query`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitFromClause

          public java.lang.Object visitFromClause(FromClause object,
                                                  java.lang.Object context)

      Executes operations on the specified `FromClause`.
      Parameters:
      `object` - A `FromClause`.

      `context` - An `Object`.

      Returns:
      An `Object`.

    <!-- -->

    - #### visitFromClauseElement

          public java.lang.Object visitFromClauseElement(FromClauseElement object,
                                                         java.lang.Object context)

      Executes operations on the specified `FromClauseElement`.
      Parameters:
      `object` - A `FromClauseElement`.

      `context` - An `Object`.

      Returns:
      An `Object`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SyntaxObject.md)
- [Next Class](TimeZoneExpression.md)

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
