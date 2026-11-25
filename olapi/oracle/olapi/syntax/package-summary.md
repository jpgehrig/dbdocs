Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Package](../session/package-summary.md)
- [Next Package](../transaction/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.olapi.syntax

Contains classes that represent data types, functions, commands, and data objects.

See: Description

- **Interface Summary**

  | Interface                                           | Description                                                                                            |
  |-----------------------------------------------------|--------------------------------------------------------------------------------------------------------|
  | [Buildable](Buildable.md)                           | A marker interface for metadata objects that an application can specify when it creates a `BuildItem`. |
  | [ConsistentSolveCommand](ConsistentSolveCommand.md) | A marker interface implemented by some `SimpleCommand` classes.                                        |
  | [FunctionArgument](FunctionArgument.md)             | A marker interface for the `Expression` and other objects that can be function arguments.              |

- **Class Summary**

  | Class                                                                                     | Description                                                                                                                                                                                                              |
  |-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AggregateOverClause](AggregateOverClause.md)                                             | The base class for an object that specifies values for the `OVER` clause in an `AggregationFunctionExpression`.                                                                                                          |
  | [AggregateOverMembersClause](AggregateOverMembersClause.md)                               | An `AggregateOverClause` that specifies a list of dimension members as the `OVER` clause for an `AggregationFunctionExpression`.                                                                                         |
  | [AggregationCase](AggregationCase.md)                                                     | A `SyntaxObject` that represents an aggregation case for an `AggregationCommand`.                                                                                                                                        |
  | [AggregationCommand](AggregationCommand.md)                                               | A `SolveStepCommand` that represents an aggregation command in a `BuildSpecification`.                                                                                                                                   |
  | [AggregationFunctionExpression](AggregationFunctionExpression.md)                         | A `TypedExpression` that represents an aggregation function.                                                                                                                                                             |
  | [AnalyzeCommand](AnalyzeCommand.md)                                                       | A `SimpleCommand` that directs Oracle OLAP to analyze the procedures that a `BuildProcess` performs as it builds an `MdmCube` or an `MdmPrimaryDimension`.                                                               |
  | [AssignmentCommand](AssignmentCommand.md)                                                 | A `SimpleCommand` that represents the assignment of values for a measure of an `MdmCube` or an attribute of an `MdmPrimaryDimension` in a `BuildSpecification`.                                                          |
  | [BaseQuery](BaseQuery.md)                                                                 | A `Query` for an object that implements the `MdmQuery` interface, such as an `MdmCube` or an `MdmPrimaryDimension`.                                                                                                      |
  | [BetweenCondition](BetweenCondition.md)                                                   | A `Condition` that represents a `BETWEEN` condition, which determines whether a value is in a specific range of values.                                                                                                  |
  | [BinaryOperatorCondition](BinaryOperatorCondition.md)                                     | A `Condition` that represents a logical `AND` or `OR` condition that operates on two component `Condition` objects.                                                                                                      |
  | [BinaryOperatorExpression](BinaryOperatorExpression.md)                                   | A `RowExpression` that represents a binary operator and two expressions that are the operands of the expression.                                                                                                         |
  | [BuildCommand](BuildCommand.md)                                                           | An abstract base class that represents a command in a `BuildSpecification`.                                                                                                                                              |
  | [BuildItem](BuildItem.md)                                                                 | A `SyntaxObject` that specifies a `Buildable` object and optionally a `BuildSpecification`, or a system change number (SCN), or both.                                                                                    |
  | [BuildProcess](BuildProcess.md)                                                           | A `SyntaxObject` that contains one or more `BuildItem` objects, each of which specifies a database object to build and how to build it.                                                                                  |
  | [BuildSpecification](BuildSpecification.md)                                               | A `SyntaxObject` that contains commands that specify how to build a `BuildItem`.                                                                                                                                         |
  | [CaseExpression](CaseExpression.md)                                                       | A `RowExpression` that is the abstract base for classes that represent expressions that are similar to `CASE` expressions in SQL.                                                                                        |
  | [ClearCommand](ClearCommand.md)                                                           | A `SimpleCommand` that clears data from the measures of a cube during a build process.                                                                                                                                   |
  | [ColumnExpression](ColumnExpression.md)                                                   | A `TypedExpression` that represents a column in a relational table or view.                                                                                                                                              |
  | [ComparisonCondition](ComparisonCondition.md)                                             | An abstract base class for a `Condition` that represents a comparison condition, which compares one expression to another expression or to a list of expressions.                                                        |
  | [CompileCommand](CompileCommand.md)                                                       | A `SimpleCommand` that causes the build process to determine and validate relationships, such as the attributes of a dimension, and to store information about the relationships.                                        |
  | [Condition](Condition.md)                                                                 | An abstract base class for an `Expression` that represents a condition, which specifies a combination of one or more expressions and logical (Boolean) operators and evaluates to `true`, `false`, `null`, or `UNKNOWN`. |
  | [ConsistentSolveSpecification](ConsistentSolveSpecification.md)                           | A `SyntaxObject` that specifies how Oracle OLAP generates solved data for an `MdmBaseMeasure` or for all of the `MdmBaseMeasure` objects of an `MdmCube`.                                                                |
  | [DataObject](DataObject.md)                                                               | An abstract base class for `Query`, `Expression` and other classes.                                                                                                                                                      |
  | [DataType](DataType.md)                                                                   | An object that represents an Oracle Database data type without precision information.                                                                                                                                    |
  | [DateExpression](DateExpression.md)                                                       | A `LiteralExpression` that represents a date.                                                                                                                                                                            |
  | [DimensionArgument](DimensionArgument.md)                                                 | A `DataObject` that represents an `MdmDimension` as a function argument.                                                                                                                                                 |
  | [Expression](Expression.md)                                                               | An abstract base class for the `Condition` and `TypedExpression` classes.                                                                                                                                                |
  | [FromClause](FromClause.md)                                                               | A `DataObject` that represents a list of relational tables.                                                                                                                                                              |
  | [FromClauseElement](FromClauseElement.md)                                                 | A `DataObject` that contains a `Query` and is an element of a `FromClause`.                                                                                                                                              |
  | [FunctionCondition](FunctionCondition.md)                                                 | A `Condition` that represents a condition that evaluates a `FunctionArgument` that produces a Boolean value.                                                                                                             |
  | [FunctionDescriptor](FunctionDescriptor.md)                                               | An object that describes the structure of an `Expression` function.                                                                                                                                                      |
  | [FunctionDescriptorArgument](FunctionDescriptorArgument.md)                               | The abstract base for classes that represent descriptors for the arguments for a `FunctionDescriptor`.                                                                                                                   |
  | [FunctionDescriptorCatalog](FunctionDescriptorCatalog.md)                                 | A catalog of functions that are represented by `Expression` objects.                                                                                                                                                     |
  | [FunctionDescriptorChoiceArgument](FunctionDescriptorChoiceArgument.md)                   | A `FunctionDescriptorArgument` that represents arguments that are alternative choices for arguments to a function.                                                                                                       |
  | [FunctionDescriptorConditionArgument](FunctionDescriptorConditionArgument.md)             | A `FunctionDescriptorArgument` that represents an argument to a condition function.                                                                                                                                      |
  | [FunctionDescriptorDimensionArgument](FunctionDescriptorDimensionArgument.md)             | A `FunctionDescriptorArgument` for a function argument that is a `DimensionArgument`.                                                                                                                                    |
  | [FunctionDescriptorGroupArgument](FunctionDescriptorGroupArgument.md)                     | A `FunctionDescriptorArgument` that is a container for the `FunctionDescriptorArgument` objects for a function that takes a group of arguments.                                                                          |
  | [FunctionDescriptorIdentifierArgument](FunctionDescriptorIdentifierArgument.md)           | A `FunctionDescriptorArgument` for an function argument that is an `IdentifierArgument`.                                                                                                                                 |
  | [FunctionDescriptorKeywordArgument](FunctionDescriptorKeywordArgument.md)                 | A `FunctionDescriptorArgument` for an function argument that is a `KeywordArgument`.                                                                                                                                     |
  | [FunctionDescriptorTypedExpressionArgument](FunctionDescriptorTypedExpressionArgument.md) | A `FunctionDescriptorArgument` for a function that takes a `TypedExpression` as an argument.                                                                                                                             |
  | [GroupCommand](GroupCommand.md)                                                           | A `BuildCommand` that represents a group of `SimpleCommand` objects that operate on the specified `MdmBaseMeasure` objects when the condition specified by a `SymmetricCondition` is true.                               |
  | [HierarchicalCondition](HierarchicalCondition.md)                                         | A `Condition` that tests whether a member of a hierarchy has the specified hierarchical relationship to itself or to another member of the hierarchy.                                                                    |
  | [IdentifierArgument](IdentifierArgument.md)                                               | A `DataObject` that represents a `SQLDataType` as a function argument.                                                                                                                                                   |
  | [IntervalExpression](IntervalExpression.md)                                               | A `RowExpression` that represents an interval expression, which is similar to a SQL interval expression.                                                                                                                 |
  | [IntervalLiteralExpression](IntervalLiteralExpression.md)                                 | A `RowExpression` that represents an interval literal expression, which is similar to a SQL interval literal expression.                                                                                                 |
  | [IsCondition](IsCondition.md)                                                             | A `Condition` that represents a special condition.                                                                                                                                                                       |
  | [KeywordArgument](KeywordArgument.md)                                                     | A `DataObject` that represents a keyword as a function argument.                                                                                                                                                         |
  | [KeywordCatalog](KeywordCatalog.md)                                                       | A catalog of keywords that an application can use as arguments to `Expression` functions.                                                                                                                                |
  | [LikeCondition](LikeCondition.md)                                                         | A `Condition` that represents a pattern-matching condition that compares the values of `StringExpression` objects.                                                                                                       |
  | [ListComparisonCondition](ListComparisonCondition.md)                                     | A `ComparisonCondition` that represents a group comparison condition, which compares one expression to a list of expressions.                                                                                            |
  | [LiteralExpression](LiteralExpression.md)                                                 | A `TypedExpression` that is the abstract base for classes that represent a literal expression.                                                                                                                           |
  | [LoadCommand](LoadCommand.md)                                                             | A `SimpleCommand` that loads data into the dimensions or measures of an analytic workspace from relational source tables during a build.                                                                                 |
  | [ModelCommand](ModelCommand.md)                                                           | A `SimpleCommand` that represents an `MdmDimensionCalculationModel` in a `BuildSpecification`.                                                                                                                           |
  | [NotCondition](NotCondition.md)                                                           | A `Condition` that represents a `NOT` condition, which negates, or reverses, the Boolean value of the base condition.                                                                                                    |
  | [NullExpression](NullExpression.md)                                                       | A `LiteralExpression` that represents `null`.                                                                                                                                                                            |
  | [NumberExpression](NumberExpression.md)                                                   | A `LiteralExpression` that represents a number.                                                                                                                                                                          |
  | [OLAPDMLCommand](OLAPDMLCommand.md)                                                       | A `SimpleCommand` that represents an OLAP DML command in a `BuildSpecification`.                                                                                                                                         |
  | [OLAPDMLExpression](OLAPDMLExpression.md)                                                 | A `TypedExpression` that represents an Oracle OLAP DML expression.                                                                                                                                                       |
  | [OLAPFunctionExpression](OLAPFunctionExpression.md)                                       | A `TypedExpression` that represents an Oracle OLAP function.                                                                                                                                                             |
  | [OrderByClause](OrderByClause.md)                                                         | A `DataObject` that represents an ordering of the results of the evaluation of an `Expression`.                                                                                                                          |
  | [OrderByElement](OrderByElement.md)                                                       | A `DataObject` that represents an expression of an `OrderByClause`.                                                                                                                                                      |
  | [PlaceholderExpression](PlaceholderExpression.md)                                         | A `TypedExpression` that represents a placeholder for a measure value.                                                                                                                                                   |
  | [PLSQLCommand](PLSQLCommand.md)                                                           | A `SimpleCommand` that represents a PL/SQL command in a `BuildSpecification`.                                                                                                                                            |
  | [QDRExpression](QDRExpression.md)                                                         | A `TypedExpression` that represents a qualified data reference (QDR).                                                                                                                                                    |
  | [Qualifier](Qualifier.md)                                                                 | A `DataObject` that represents a dimension member for a `QDRExpression`.                                                                                                                                                 |
  | [Query](Query.md)                                                                         | A `DataObject` that represents a multirow, multicolumn result set that is similar to a relational table, a SQL `SELECT` statement, or an OLAP function.                                                                  |
  | [RowExpression](RowExpression.md)                                                         | A `TypedExpression` that is the abstract base for classes that represent a row-based expression.                                                                                                                         |
  | [RowFunctionExpression](RowFunctionExpression.md)                                         | A `RowExpression` that represents a row function, which is similar to a SQL single-row function.                                                                                                                         |
  | [SearchedCase](SearchedCase.md)                                                           | A `DataObject` that contains a `WHEN` condition and a `THEN` expression for a [`SearchedCaseExpression`](SearchedCaseExpression.md).                                                                                     |
  | [SearchedCaseExpression](SearchedCaseExpression.md)                                       | A `CaseExpression` that represents an expression that is similar to the searched case expression clause and the `ELSE` clause of a `CASE` expression in SQL.                                                             |
  | [SimpleCase](SimpleCase.md)                                                               | A `DataObject` that contains a pair of `WHEN` and `THEN` expressions for a [`SimpleCaseExpression`](SimpleCaseExpression.md).                                                                                            |
  | [SimpleCaseExpression](SimpleCaseExpression.md)                                           | A `CaseExpression` that represents an expression that is similar to the simple case expression and the `ELSE` clauses of a `CASE` expression in SQL.                                                                     |
  | [SimpleCommand](SimpleCommand.md)                                                         | An abstract base class for simple build commands.                                                                                                                                                                        |
  | [SolveCommand](SolveCommand.md)                                                           | A `SimpleCommand` that initiates the operations that calculate the data for the measures of an `MdmCube`.                                                                                                                |
  | [SolveStepCommand](SolveStepCommand.md)                                                   | An abstract `SimpleCommand` that specifes a function that is one step in the operations that calculate the data for the measures of an `MdmCube`.                                                                        |
  | [SQLDataType](SQLDataType.md)                                                             | An object that represents an Oracle Database data type with precision information.                                                                                                                                       |
  | [StarArgument](StarArgument.md)                                                           | A `DataObject` that represents a `*` (asterisk) argument.                                                                                                                                                                |
  | [StringExpression](StringExpression.md)                                                   | A `LiteralExpression` that represents a literal text expression.                                                                                                                                                         |
  | [SymmetricCondition](SymmetricCondition.md)                                               | A `SyntaxObject` that specifies a collection of the members one or more dimensions.                                                                                                                                      |
  | [SymmetricConditionElement](SymmetricConditionElement.md)                                 | A `SyntaxObject` that specifies a collection of the members of a dimension for a `SymmetricCondition`.                                                                                                                   |
  | [SyntaxObject](SyntaxObject.md)                                                           | An abstract base class for objects that specify tables or columns in an Oracle Database instance, and that represent selections of data and operations on the data.                                                      |
  | [SyntaxObjectVisitor](SyntaxObjectVisitor.md)                                             | A visitor class for the `SyntaxObject` class hierarchy.                                                                                                                                                                  |
  | [TimeZoneExpression](TimeZoneExpression.md)                                               | A `RowExpression` that represents a date with a time zone.                                                                                                                                                               |
  | [TypedExpression](TypedExpression.md)                                                     | An `Expression` that is a combination of one or more values, operators, and functions that evaluates to a value.                                                                                                         |
  | [UnaryOperatorExpression](UnaryOperatorExpression.md)                                     | A `RowExpression` that represents a unary operator and an operand.                                                                                                                                                       |
  | [UnresolvedDimensionArgument](UnresolvedDimensionArgument.md)                             | A `DimensionArgument` that represents an invalid or unresolvable identifier.                                                                                                                                             |
  | [UnresolvedExpression](UnresolvedExpression.md)                                           | A `TypedExpression` that represents an invalid or unresolvable identifier.                                                                                                                                               |
  | [UnresolvedQuery](UnresolvedQuery.md)                                                     | A `Query` that represents an invalid or unresolvable identifier.                                                                                                                                                         |
  | [ValueComparisonCondition](ValueComparisonCondition.md)                                   | A `ComparisonCondition` that represents a simple comparison condition, which compares one expression to another expression.                                                                                              |

- **Exception Summary**

  | Exception                             | Description                                                               |
  |---------------------------------------|---------------------------------------------------------------------------|
  | [SyntaxException](SyntaxException.md) | Indicates that part of the specification of an `SyntaxObject` is invalid. |

## Package oracle.olapi.syntax Description

Contains classes that represent data types, functions, commands, and data objects. Data objects include classes that represent arguments, conditions, and other expressions.

Subclasses of `SyntaxObject` have methods that convert the object to or from text in Oracle OLAP expression syntax. The text can be SQL statements, or PL/SQL or OLAP DML functions or commands.

An application uses instances of objects from this package in mapping metadata objects to data in the database. Some objects, such as subclasses of `Query` and `Expression`, have a `getSource` method that returns an `oracle.olapi.data.source.Source` for which an `oracle.olapi.data.cursor.Cursor` can retrieve data.

`BuildCommand` objects specify actions that affect an analytic workspace. An application associates a `BuildCommand` object with a `BuildItem` and a `BuildProcess`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../session/package-summary.md)
- [Next Package](../transaction/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)
