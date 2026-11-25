Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](InvalidExpressionException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.expression

## Class ExpressionLexicalAnalyzer

- java.lang.Object

- - oracle.spatial.network.nfe.expression.ExpressionLexicalAnalyzer

<!-- -->

- All Implemented Interfaces:
  [NFEExpressionAnalyzer](NFEExpressionAnalyzer.md)

  ------------------------------------------------------------------------



      public class ExpressionLexicalAnalyzer
      extends java.lang.Object
      implements NFEExpressionAnalyzer

  Default implementation for NFEExpressionAnalyzer.
  The supported operators are AND, OR, AND NOT, OR NOT, =, !=, \>, \<,\>=, \<=, \*, , +, -, (, )

  If you want to get as result a double us only \*, /, +, -, (, ) and numbers. The most common case is when evaluating an attribute expression to apply a customized cost based on numerical attributes.

  Examples of valid expressions that will return a double, COST is an attribute of the feature used to build the expression:

       1) COST*5/4
       2) 8*(4-3)


  You may want to get a boolean as returned value. The most common case is when evaluating NFE rules attributes expressions. Note that any string has to be quoted.

  Examples of valid expression that will return a boolean, LENGTH and NAME are attributes of the feature used to build the expression:

        1) LENGTH = 1
        2) (LENGTH + 2) = 5 AND (NAME = 'Peter' OR NAME = 'John')


<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                        |
    |---------------------------|--------------------------------------------------------------|
    | `static java.lang.String` | `AND`<br>AND operator.                                       |
    | `static java.lang.String` | `AND_NOT`<br>AND NOT operator.                               |
    | `static java.lang.String` | `BIGGER_OR_EQUALS_THAN`<br>BIGGER OR EQUALS THAN operator.   |
    | `static java.lang.String` | `BIGGER_THAN`<br>BIGGER THAN operator.                       |
    | `static java.lang.String` | `DIVISION`<br>DIVISION operator.                             |
    | `static java.lang.String` | `EQUALS`<br>EQUALS operator.                                 |
    | `static java.lang.String` | `MINUS`<br>MINUS operator.                                   |
    | `static java.lang.String` | `MULTIPLICITY`<br>MULTIPLICITY operator.                     |
    | `static java.lang.String` | `NOT_EQUALS`<br>NOT EQUALS operator.                         |
    | `static java.lang.String` | `OR`<br>OR operator.                                         |
    | `static java.lang.String` | `OR_NOT`<br>OR NOT operator.                                 |
    | `static java.lang.String` | `PLUS`<br>PLUS operator.                                     |
    | `static java.lang.String` | `SMALLER_OR_EQUALS_THAN`<br>SMALLER OR EQUALS THAN operator. |
    | `static java.lang.String` | `SMALLER_THAN`<br>SMALLER THAN operator.                     |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description      |
    |----------------------------------|
    | `ExpressionLexicalAnalyzer``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                                        |
    |---------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | [`ReturnValue`](ReturnValue.md) | `build``(`[`NFEFeature`](../model/feature/NFEFeature.md)` feature)`<br>Builds the expression and return the expression value. |
    | `java.lang.String`              | `getExpression``()`<br>Returns the expression                                                                                 |
    | `void`                          | `setExpression``(java.lang.String expression)`<br>Sets the expression to analyze.                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### AND

          public static java.lang.String AND

      AND operator.

    <!-- -->

    - #### OR

          public static java.lang.String OR

      OR operator.

    <!-- -->

    - #### AND_NOT

          public static java.lang.String AND_NOT

      AND NOT operator.

    <!-- -->

    - #### OR_NOT

          public static java.lang.String OR_NOT

      OR NOT operator.

    <!-- -->

    - #### EQUALS

          public static java.lang.String EQUALS

      EQUALS operator.

    <!-- -->

    - #### NOT_EQUALS

          public static java.lang.String NOT_EQUALS

      NOT EQUALS operator.

    <!-- -->

    - #### BIGGER_THAN

          public static java.lang.String BIGGER_THAN

      BIGGER THAN operator.

    <!-- -->

    - #### SMALLER_THAN

          public static java.lang.String SMALLER_THAN

      SMALLER THAN operator.

    <!-- -->

    - #### BIGGER_OR_EQUALS_THAN

          public static java.lang.String BIGGER_OR_EQUALS_THAN

      BIGGER OR EQUALS THAN operator.

    <!-- -->

    - #### SMALLER_OR_EQUALS_THAN

          public static java.lang.String SMALLER_OR_EQUALS_THAN

      SMALLER OR EQUALS THAN operator.

    <!-- -->

    - #### MULTIPLICITY

          public static java.lang.String MULTIPLICITY

      MULTIPLICITY operator.

    <!-- -->

    - #### DIVISION

          public static java.lang.String DIVISION

      DIVISION operator.

    <!-- -->

    - #### PLUS

          public static java.lang.String PLUS

      PLUS operator.

    <!-- -->

    - #### MINUS

          public static java.lang.String MINUS

      MINUS operator.

  <!-- -->

  - ### Constructor Detail

    - #### ExpressionLexicalAnalyzer

          public ExpressionLexicalAnalyzer()

  <!-- -->

  - ### Method Detail

    - #### getExpression

          public java.lang.String getExpression()

      Returns the expression
      Returns:
      expression

    <!-- -->

    - #### setExpression

          public void setExpression(java.lang.String expression)

      Description copied from interface: [`NFEExpressionAnalyzer`](NFEExpressionAnalyzer.md)
      Sets the expression to analyze.
      Specified by:
      [`setExpression`](NFEExpressionAnalyzer.md) in interface [`NFEExpressionAnalyzer`](NFEExpressionAnalyzer.md)

      Parameters:
      `expression` - expression

    <!-- -->

    - #### build

          public ReturnValue build(NFEFeature feature)
                            throws InvalidExpressionException

      Description copied from interface: [`NFEExpressionAnalyzer`](NFEExpressionAnalyzer.md)
      Builds the expression and return the expression value.
      Specified by:
      [`build`](NFEExpressionAnalyzer.md) in interface [`NFEExpressionAnalyzer`](NFEExpressionAnalyzer.md)

      Parameters:
      `feature` - feature to use in the expression.

      Returns:
      return value, the value can be a boolean or a double.

      Throws:
      [`InvalidExpressionException`](InvalidExpressionException.md) - if the expression is not valid

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](InvalidExpressionException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
