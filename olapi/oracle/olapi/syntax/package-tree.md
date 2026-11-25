Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev](../session/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.olapi.syntax

Package Hierarchies:

- [All Packages](../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.olapi.syntax.[DataType](DataType.md)
  - oracle.olapi.syntax.[FunctionDescriptor](FunctionDescriptor.md)
  - oracle.olapi.syntax.[FunctionDescriptorArgument](FunctionDescriptorArgument.md)
    - oracle.olapi.syntax.[FunctionDescriptorChoiceArgument](FunctionDescriptorChoiceArgument.md)
    - oracle.olapi.syntax.[FunctionDescriptorConditionArgument](FunctionDescriptorConditionArgument.md)
    - oracle.olapi.syntax.[FunctionDescriptorDimensionArgument](FunctionDescriptorDimensionArgument.md)
    - oracle.olapi.syntax.[FunctionDescriptorGroupArgument](FunctionDescriptorGroupArgument.md)
    - oracle.olapi.syntax.[FunctionDescriptorIdentifierArgument](FunctionDescriptorIdentifierArgument.md)
    - oracle.olapi.syntax.[FunctionDescriptorKeywordArgument](FunctionDescriptorKeywordArgument.md)
    - oracle.olapi.syntax.[FunctionDescriptorTypedExpressionArgument](FunctionDescriptorTypedExpressionArgument.md)
  - oracle.olapi.syntax.[FunctionDescriptorCatalog](FunctionDescriptorCatalog.md)
  - oracle.olapi.syntax.[KeywordCatalog](KeywordCatalog.md)
  - oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)
    - oracle.olapi.syntax.[AggregateOverClause](AggregateOverClause.md)
      - oracle.olapi.syntax.[AggregateOverMembersClause](AggregateOverMembersClause.md)
    - oracle.olapi.syntax.[AggregationCase](AggregationCase.md)
    - oracle.olapi.syntax.[BuildCommand](BuildCommand.md)
      - oracle.olapi.syntax.[GroupCommand](GroupCommand.md)
      - oracle.olapi.syntax.[SimpleCommand](SimpleCommand.md)
        - oracle.olapi.syntax.[AnalyzeCommand](AnalyzeCommand.md)
        - oracle.olapi.syntax.[AssignmentCommand](AssignmentCommand.md)
        - oracle.olapi.syntax.[ClearCommand](ClearCommand.md)
        - oracle.olapi.syntax.[CompileCommand](CompileCommand.md)
        - oracle.olapi.syntax.[LoadCommand](LoadCommand.md)
        - oracle.olapi.syntax.[ModelCommand](ModelCommand.md) (implements oracle.olapi.syntax.[ConsistentSolveCommand](ConsistentSolveCommand.md))
        - oracle.olapi.syntax.[OLAPDMLCommand](OLAPDMLCommand.md)
        - oracle.olapi.syntax.[PLSQLCommand](PLSQLCommand.md)
        - oracle.olapi.syntax.[SolveCommand](SolveCommand.md)
        - oracle.olapi.syntax.[SolveStepCommand](SolveStepCommand.md)
          - oracle.olapi.syntax.[AggregationCommand](AggregationCommand.md) (implements oracle.olapi.syntax.[ConsistentSolveCommand](ConsistentSolveCommand.md))
    - oracle.olapi.syntax.[BuildItem](BuildItem.md)
    - oracle.olapi.syntax.[BuildProcess](BuildProcess.md)
    - oracle.olapi.syntax.[BuildSpecification](BuildSpecification.md)
    - oracle.olapi.syntax.[ConsistentSolveSpecification](ConsistentSolveSpecification.md)
    - oracle.olapi.syntax.[DataObject](DataObject.md)
      - oracle.olapi.syntax.[DimensionArgument](DimensionArgument.md) (implements oracle.olapi.syntax.[FunctionArgument](FunctionArgument.md))
        - oracle.olapi.syntax.[UnresolvedDimensionArgument](UnresolvedDimensionArgument.md)
      - oracle.olapi.syntax.[Expression](Expression.md) (implements oracle.olapi.syntax.[FunctionArgument](FunctionArgument.md))
        - oracle.olapi.syntax.[Condition](Condition.md)
          - oracle.olapi.syntax.[BetweenCondition](BetweenCondition.md)
          - oracle.olapi.syntax.[BinaryOperatorCondition](BinaryOperatorCondition.md)
          - oracle.olapi.syntax.[ComparisonCondition](ComparisonCondition.md)
            - oracle.olapi.syntax.[ListComparisonCondition](ListComparisonCondition.md)
            - oracle.olapi.syntax.[ValueComparisonCondition](ValueComparisonCondition.md)
          - oracle.olapi.syntax.[FunctionCondition](FunctionCondition.md)
          - oracle.olapi.syntax.[HierarchicalCondition](HierarchicalCondition.md)
          - oracle.olapi.syntax.[IsCondition](IsCondition.md)
          - oracle.olapi.syntax.[LikeCondition](LikeCondition.md)
          - oracle.olapi.syntax.[NotCondition](NotCondition.md)
        - oracle.olapi.syntax.[TypedExpression](TypedExpression.md)
          - oracle.olapi.syntax.[AggregationFunctionExpression](AggregationFunctionExpression.md)
          - oracle.olapi.syntax.[ColumnExpression](ColumnExpression.md)
          - oracle.olapi.syntax.[LiteralExpression](LiteralExpression.md)
            - oracle.olapi.syntax.[DateExpression](DateExpression.md)
            - oracle.olapi.syntax.[NullExpression](NullExpression.md)
            - oracle.olapi.syntax.[NumberExpression](NumberExpression.md)
            - oracle.olapi.syntax.[StringExpression](StringExpression.md)
          - oracle.olapi.syntax.[OLAPDMLExpression](OLAPDMLExpression.md)
          - oracle.olapi.syntax.[OLAPFunctionExpression](OLAPFunctionExpression.md)
          - oracle.olapi.syntax.[PlaceholderExpression](PlaceholderExpression.md)
          - oracle.olapi.syntax.[QDRExpression](QDRExpression.md)
          - oracle.olapi.syntax.[RowExpression](RowExpression.md)
            - oracle.olapi.syntax.[BinaryOperatorExpression](BinaryOperatorExpression.md)
            - oracle.olapi.syntax.[CaseExpression](CaseExpression.md)
              - oracle.olapi.syntax.[SearchedCaseExpression](SearchedCaseExpression.md)
              - oracle.olapi.syntax.[SimpleCaseExpression](SimpleCaseExpression.md)
            - oracle.olapi.syntax.[IntervalExpression](IntervalExpression.md)
            - oracle.olapi.syntax.[IntervalLiteralExpression](IntervalLiteralExpression.md)
            - oracle.olapi.syntax.[RowFunctionExpression](RowFunctionExpression.md)
            - oracle.olapi.syntax.[TimeZoneExpression](TimeZoneExpression.md)
            - oracle.olapi.syntax.[UnaryOperatorExpression](UnaryOperatorExpression.md)
          - oracle.olapi.syntax.[UnresolvedExpression](UnresolvedExpression.md)
      - oracle.olapi.syntax.[FromClause](FromClause.md)
      - oracle.olapi.syntax.[FromClauseElement](FromClauseElement.md)
      - oracle.olapi.syntax.[IdentifierArgument](IdentifierArgument.md) (implements oracle.olapi.syntax.[FunctionArgument](FunctionArgument.md))
      - oracle.olapi.syntax.[KeywordArgument](KeywordArgument.md) (implements oracle.olapi.syntax.[FunctionArgument](FunctionArgument.md))
      - oracle.olapi.syntax.[OrderByClause](OrderByClause.md)
      - oracle.olapi.syntax.[OrderByElement](OrderByElement.md)
      - oracle.olapi.syntax.[Qualifier](Qualifier.md)
      - oracle.olapi.syntax.[Query](Query.md)
        - oracle.olapi.syntax.[BaseQuery](BaseQuery.md)
        - oracle.olapi.syntax.[UnresolvedQuery](UnresolvedQuery.md)
      - oracle.olapi.syntax.[SearchedCase](SearchedCase.md)
      - oracle.olapi.syntax.[SimpleCase](SimpleCase.md)
      - oracle.olapi.syntax.[StarArgument](StarArgument.md) (implements oracle.olapi.syntax.[FunctionArgument](FunctionArgument.md))
    - oracle.olapi.syntax.[SQLDataType](SQLDataType.md)
    - oracle.olapi.syntax.[SymmetricCondition](SymmetricCondition.md)
    - oracle.olapi.syntax.[SymmetricConditionElement](SymmetricConditionElement.md)
  - oracle.olapi.syntax.[SyntaxObjectVisitor](SyntaxObjectVisitor.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - java.lang.RuntimeException
        - oracle.olapi.[OLAPIRuntimeException](../OLAPIRuntimeException.md) (implements oracle.olapi.[HasLocalizedMessage](../HasLocalizedMessage.md))
          - oracle.olapi.syntax.[SyntaxException](SyntaxException.md)

## Interface Hierarchy

- oracle.olapi.syntax.[Buildable](Buildable.md)
- oracle.olapi.syntax.[ConsistentSolveCommand](ConsistentSolveCommand.md)
- oracle.olapi.syntax.[FunctionArgument](FunctionArgument.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev](../session/package-tree.md)
-

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)
