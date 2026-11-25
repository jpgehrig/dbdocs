Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFERuleInstanceRelation.md)
- [Next Class](NFERulesModel.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.rule

## Class NFERulesEngine

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.NFERulesEngine

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFERulesEngine
      extends java.lang.Object

  NFE component in charge of enforcing connectivity and cardinality rules. It performs the process of determining if some rule is applicable for an interaction between feature elements and apply such rule.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                 |
    |-------------------------------------------------------------------------------------------------------------|
    | `NFERulesEngine``(`[`NFERulesModel`](NFERulesModel.md)` rulesModel)`<br>Creates a new rules engine instance |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                                                                                                                                                               |
    |----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                               | `applyConnectivityRules``(`[`Intersection`](../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`> intersection)`<br>Runs the rule applicability process for the given intersection of feature elements                                                  |
    | `void`                                                               | `applyConnectivityRules``(java.util.List<`[`Intersection`](../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>> intersections)`<br>Runs the rule applicability process over the given intersections of feature elements                               |
    | [`NFEExpressionAnalyzer`](../../expression/NFEExpressionAnalyzer.md) | `getExpressionAnalyzer``()`<br>Gets the current expression analyzer instance                                                                                                                                                                                                                         |
    | [`NFERuleHandler`](handler/NFERuleHandler.md)                        | `getHandler``(`[`NFEConnectivityRule`](NFEConnectivityRule.md)` rule)`<br>Gets the appropriate handler for the given rule                                                                                                                                                                            |
    | `boolean`                                                            | `isMatchingType``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem, long ruleFeatLayerId, long ruleFeatClassId, java.lang.String ruleAttrCond)`<br>Tells whether a feature element matches the predicate of a rule.                                                                 |
    | `void`                                                               | `lineLineConnectionPerformed``(long lineLineRuleId, java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`> featElems)`<br>Method called to notify the rules engine when a connection between the specified feature elements was performed using the given line-line rule.    |
    | `void`                                                               | `linePointConnectionPerformed``(long linePointRuleId, java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`> featElems)`<br>Method called to notify the rules engine when a connection between the specified feature elements was performed using the given line-point rule. |
    | `void`                                                               | `setExpressionAnalyzer``(`[`NFEExpressionAnalyzer`](../../expression/NFEExpressionAnalyzer.md)` exprAnalyzer)`<br>Sets the expression analyzer implementation to be used                                                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFERulesEngine

          public NFERulesEngine(NFERulesModel rulesModel)

      Creates a new rules engine instance
      Parameters:
      `rulesModel` - the current rules model. The rules model must belong already to an NFE model.

  <!-- -->

  - ### Method Detail

    - #### getExpressionAnalyzer

          public NFEExpressionAnalyzer getExpressionAnalyzer()

      Gets the current expression analyzer instance
      Returns:
      an expression analyzer object

    <!-- -->

    - #### setExpressionAnalyzer

          public void setExpressionAnalyzer(NFEExpressionAnalyzer exprAnalyzer)

      Sets the expression analyzer implementation to be used
      Parameters:
      `exprAnalyzer` - an expression analyzer object

    <!-- -->

    - #### applyConnectivityRules

          public void applyConnectivityRules(java.util.List<Intersection<NFEFeatureElement>> intersections)

      Runs the rule applicability process over the given intersections of feature elements
      Parameters:
      `intersections` - a list of feature elements intersections

    <!-- -->

    - #### applyConnectivityRules

          public void applyConnectivityRules(Intersection<NFEFeatureElement> intersection)

      Runs the rule applicability process for the given intersection of feature elements
      Parameters:
      `intersection` - a feature elements intersection

    <!-- -->

    - #### isMatchingType

          public boolean isMatchingType(NFEFeatureElement featElem,
                                        long ruleFeatLayerId,
                                        long ruleFeatClassId,
                                        java.lang.String ruleAttrCond)

      Tells whether a feature element matches the predicate of a rule. The rule's predicate is given by one of its operands and it is formed by a feature layer id, a feature class id and a boolean expression which performs comparisons between attribute values.
      Parameters:
      `featElem` - the feature element which will be compared

      `ruleFeatLayerId` - a feature layer id defined in a rule's operand

      `ruleFeatClassId` - a feature class id defined in a rule's operand

      `ruleAttrCond` - an attribute condition expression defined in a rule's operand

      Returns:
      true if the feature element matches the given rule's predicate

    <!-- -->

    - #### getHandler

          public NFERuleHandler getHandler(NFEConnectivityRule rule)

      Gets the appropriate handler for the given rule
      Parameters:
      `rule` - a connectivity rule objet (line-point or line-line)

      Returns:
      a rule handler object

    <!-- -->

    - #### linePointConnectionPerformed

          public void linePointConnectionPerformed(long linePointRuleId,
                                                   java.util.Collection<NFEFeatureElement> featElems)

      Method called to notify the rules engine when a connection between the specified feature elements was performed using the given line-point rule. The rules engine eventually will create the rule instance and notify the rules model.
      Parameters:
      `linePointRuleId` - a line-point rule id that allows the connection

      `featElems` - a collection of connected feature elements

    <!-- -->

    - #### lineLineConnectionPerformed

          public void lineLineConnectionPerformed(long lineLineRuleId,
                                                  java.util.Collection<NFEFeatureElement> featElems)

      Method called to notify the rules engine when a connection between the specified feature elements was performed using the given line-line rule. The rules engine eventually will create the rule instance and notify the rules model.
      Parameters:
      `lineLineRuleId` - a line-line rule id that allows the connection

      `featElems` - a collection of connected feature elements

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFERuleInstanceRelation.md)
- [Next Class](NFERulesModel.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
