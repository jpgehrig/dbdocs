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

- [Prev Class](InvalidExpressionException.md)
- [Next Class](ReturnValue.md)

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

## Interface NFEExpressionAnalyzer

- All Known Implementing Classes:
  [ExpressionLexicalAnalyzer](ExpressionLexicalAnalyzer.md)

  ------------------------------------------------------------------------



      public interface NFEExpressionAnalyzer

  This interface defines the methods to set an expression and build it.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                                                        |
    |---------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | [`ReturnValue`](ReturnValue.md) | `build``(`[`NFEFeature`](../model/feature/NFEFeature.md)` feature)`<br>Builds the expression and return the expression value. |
    | `void`                          | `setExpression``(java.lang.String expression)`<br>Sets the expression to analyze.                                             |

<!-- -->

- - ### Method Detail

    - #### build

          ReturnValue build(NFEFeature feature)
                     throws InvalidExpressionException

      Builds the expression and return the expression value.
      Parameters:
      `feature` - feature to use in the expression.

      Returns:
      return value, the value can be a boolean or a double.

      Throws:
      [`InvalidExpressionException`](InvalidExpressionException.md) - if the expression is not valid

    <!-- -->

    - #### setExpression

          void setExpression(java.lang.String expression)

      Sets the expression to analyze.
      Parameters:
      `expression` - expression

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

- [Prev Class](InvalidExpressionException.md)
- [Next Class](ReturnValue.md)

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
