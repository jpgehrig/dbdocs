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

- [Prev Class](NFELineLineRule.md)
- [Next Class](NFELinePointRule.LPRuleSource.md)

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

## Class NFELinePointRule

- java.lang.Object

- - [oracle.spatial.network.nfe.model.rule.NFEConnectivityRule](NFEConnectivityRule.md)

  - - oracle.spatial.network.nfe.model.rule.NFELinePointRule

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFELinePointRule
      extends NFEConnectivityRule

  A representation of an NFE line-point connectivity rule

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`NFELinePointRule.LPRuleSource`](NFELinePointRule.LPRuleSource.md)<br>Defines different sources where a line-point could be created |

    - ### Nested classes/interfaces inherited from class oracle.spatial.network.nfe.model.rule.[NFEConnectivityRule](NFEConnectivityRule.md)

      [`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md)

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class oracle.spatial.network.nfe.model.rule.[NFEConnectivityRule](NFEConnectivityRule.md)

      [`ANY_FEATURE_CLASS_ID`](NFEConnectivityRule.md)`, `[`ANY_FEATURE_LAYER_ID`](NFEConnectivityRule.md)`, `[`DEFAULT_LL_HANDLER_ID`](NFEConnectivityRule.md)`, `[`DEFAULT_LP_HANDLER_ID`](NFEConnectivityRule.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                      |
    |------------------------------------------------------------------|
    | `NFELinePointRule``(long id)`<br>Allocates a new line-point rule |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                         | Method and Description                                                                                                                                                                      |
    |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFELinePointRule`                                                                        | `createCopy``()`<br>Returns a copy of the rule.                                                                                                                                             |
    | `java.lang.String`                                                                        | `getLineAttrCondition``()`<br>Gets the rule's line attribute condition.                                                                                                                     |
    | `long`                                                                                    | `getLineFeatureClassId``()`<br>Gets the rule's line feature class id                                                                                                                        |
    | `long`                                                                                    | `getLineFeatureLayerId``()`<br>Gets the rule's line feature layer id                                                                                                                        |
    | `int`                                                                                     | `getMaxInConnections``()`<br>Gets the maximum number of incoming lines of the rule's line type allowed for the rule's point                                                                 |
    | `int`                                                                                     | `getMaxOutConnections``()`<br>Gets the maximum number of outgoing lines of the rule's line type allowed for the rule's point                                                                |
    | `java.lang.String`                                                                        | `getPointAttrCondition``()`<br>Gets the rule's point attribute condition.                                                                                                                   |
    | `long`                                                                                    | `getPointFeatureClassId``()`<br>Gets the rule's point feature class id                                                                                                                      |
    | `long`                                                                                    | `getPointFeatureLayerId``()`<br>Gets the rule's point feature layer id                                                                                                                      |
    | [`NFELinePointRule.LPRuleSource`](NFELinePointRule.LPRuleSource.md)                       | `getSource``()`<br>Gets a value indicating where the rule was created                                                                                                                       |
    | [`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md) | `getType``()`<br>Gets the actual connectivity rule type                                                                                                                                     |
    | `void`                                                                                    | `setLineAttrCondition``(java.lang.String lineAttrCond)`<br>Sets the rule's line attribute condition.                                                                                        |
    | `void`                                                                                    | `setLineFeatureClassId``(long lineFeatClassId)`<br>Sets the rule's line feature class id                                                                                                    |
    | `void`                                                                                    | `setLineFeatureLayerId``(long lineFeatLayerId)`<br>Sets the rule's line feature layer id                                                                                                    |
    | `void`                                                                                    | `setMaxInConnections``(int maxInConn)`<br>Sets the maximum number of incoming lines of the rule's line type allowed for the rule's point maxInConn the maximum number of in connections     |
    | `void`                                                                                    | `setMaxOutConnections``(int maxOutConn)`<br>Gets the maximum number of outgoing lines of the rule's line type allowed for the rule's point maxOutConn the maximum number of out connections |
    | `void`                                                                                    | `setPointAttrCondition``(java.lang.String pointAttrCond)`<br>Sets the rule's point attribute condition.                                                                                     |
    | `void`                                                                                    | `setPointFeatureClassId``(long pointFeatClassId)`<br>Sets the rule's point feature class id                                                                                                 |
    | `void`                                                                                    | `setPointFeatureLayerId``(long pointFeatLayerId)`<br>Sets the rule's point feature layer id                                                                                                 |
    | `void`                                                                                    | `setSource``(`[`NFELinePointRule.LPRuleSource`](NFELinePointRule.LPRuleSource.md)` source)`<br>Sets a value indicating where the rule was created                                           |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.rule.[NFEConnectivityRule](NFEConnectivityRule.md)

      [`getExecutionOrder`](NFEConnectivityRule.md)`, `[`getHandler`](NFEConnectivityRule.md)`, `[`getHandlerClass`](NFEConnectivityRule.md)`, `[`getHandlerClassName`](NFEConnectivityRule.md)`, `[`getHandlerId`](NFEConnectivityRule.md)`, `[`getId`](NFEConnectivityRule.md)`, `[`getKey`](NFEConnectivityRule.md)`, `[`setExecutionOrder`](NFEConnectivityRule.md)`, `[`setHandler`](NFEConnectivityRule.md)`, `[`setHandlerClass`](NFEConnectivityRule.md)`, `[`setHandlerClassName`](NFEConnectivityRule.md)`, `[`setHandlerId`](NFEConnectivityRule.md)`, `[`setId`](NFEConnectivityRule.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFELinePointRule

          public NFELinePointRule(long id)

      Allocates a new line-point rule
      Parameters:
      `id` - the rule id

  <!-- -->

  - ### Method Detail

    - #### getType

          public NFEConnectivityRule.ConnectivityRuleType getType()

      Description copied from class: [`NFEConnectivityRule`](NFEConnectivityRule.md)
      Gets the actual connectivity rule type
      Specified by:
      [`getType`](NFEConnectivityRule.md) in class [`NFEConnectivityRule`](NFEConnectivityRule.md)

      Returns:
      a connectivity rule type

    <!-- -->

    - #### getLineAttrCondition

          public java.lang.String getLineAttrCondition()

      Gets the rule's line attribute condition. The condition will be evaluated by the expression analyzer that can be found in the model's rules engine: model.getManipulator().getRulesEngine(). By default the expression analyzer will be oracle.spatial.network.nfe.expression.ExpressionLexicalAnalyzer.
      Returns:
      the line attribute condition as a boolean expression

    <!-- -->

    - #### setLineAttrCondition

          public void setLineAttrCondition(java.lang.String lineAttrCond)

      Sets the rule's line attribute condition. The condition will be evaluated by the expression analyzer that can be found in the model's rules engine: model.getManipulator().getRulesEngine(). By default the expression analyzer will be oracle.spatial.network.nfe.expression.ExpressionLexicalAnalyzer.
      Parameters:
      `lineAttrCond` - the line attribute condition as a boolean expression

    <!-- -->

    - #### getPointAttrCondition

          public java.lang.String getPointAttrCondition()

      Gets the rule's point attribute condition. The condition will be evaluated by the expression analyzer that can be found in the model's rules engine: model.getManipulator().getRulesEngine(). By default the expression analyzer will be oracle.spatial.network.nfe.expression.ExpressionLexicalAnalyzer.
      Returns:
      the point attribute condition as a boolean expression

    <!-- -->

    - #### setPointAttrCondition

          public void setPointAttrCondition(java.lang.String pointAttrCond)

      Sets the rule's point attribute condition. The condition will be evaluated by the expression analyzer that can be found in the model's rules engine: model.getManipulator().getRulesEngine(). By default the expression analyzer will be oracle.spatial.network.nfe.expression.ExpressionLexicalAnalyzer.
      Parameters:
      `pointAttrCond` - the point attribute condition as a boolean expression

    <!-- -->

    - #### getSource

          public NFELinePointRule.LPRuleSource getSource()

      Gets a value indicating where the rule was created
      Returns:
      a line-point source type

    <!-- -->

    - #### setSource

          public void setSource(NFELinePointRule.LPRuleSource source)

      Sets a value indicating where the rule was created
      Parameters:
      `source` - a line-point source type

    <!-- -->

    - #### getMaxInConnections

          public int getMaxInConnections()

      Gets the maximum number of incoming lines of the rule's line type allowed for the rule's point
      Returns:
      the maximum number of in connections. If unbounded it returns `NFECardinalityRule.CARDINALITY_UNBOUNDED`

    <!-- -->

    - #### setMaxInConnections

          public void setMaxInConnections(int maxInConn)

      Sets the maximum number of incoming lines of the rule's line type allowed for the rule's point maxInConn the maximum number of in connections

    <!-- -->

    - #### getMaxOutConnections

          public int getMaxOutConnections()

      Gets the maximum number of outgoing lines of the rule's line type allowed for the rule's point
      Returns:
      the maximum number of out connections. If unbounded it returns `NFECardinalityRule.CARDINALITY_UNBOUNDED`

    <!-- -->

    - #### setMaxOutConnections

          public void setMaxOutConnections(int maxOutConn)

      Gets the maximum number of outgoing lines of the rule's line type allowed for the rule's point maxOutConn the maximum number of out connections

    <!-- -->

    - #### getLineFeatureLayerId

          public long getLineFeatureLayerId()

      Gets the rule's line feature layer id
      Returns:
      a line feature layer id or `NFEConnectivityRule.ANY_FEATURE_LAYER_ID` indicating the rule applies for all the line feature layers

    <!-- -->

    - #### setLineFeatureLayerId

          public void setLineFeatureLayerId(long lineFeatLayerId)

      Sets the rule's line feature layer id
      Parameters:
      `lineFeatLayerId` - a line feature layer id or `NFEConnectivityRule.ANY_FEATURE_LAYER_ID` for any line feature layer id

    <!-- -->

    - #### getPointFeatureLayerId

          public long getPointFeatureLayerId()

      Gets the rule's point feature layer id
      Returns:
      a point feature layer id or `NFEConnectivityRule.ANY_FEATURE_LAYER_ID` indicating the rule applies for all the point feature layers

    <!-- -->

    - #### setPointFeatureLayerId

          public void setPointFeatureLayerId(long pointFeatLayerId)

      Sets the rule's point feature layer id
      Parameters:
      `pointFeatLayerId` - a point feature layer id or `NFEConnectivityRule.ANY_FEATURE_LAYER_ID` for any point feature layer id

    <!-- -->

    - #### getLineFeatureClassId

          public long getLineFeatureClassId()

      Gets the rule's line feature class id
      Returns:
      a line feature class id or `NFEConnectivityRule.ANY_FEATURE_CLASS_ID` indicating the rule applies for all the line feature classes

    <!-- -->

    - #### setLineFeatureClassId

          public void setLineFeatureClassId(long lineFeatClassId)

      Sets the rule's line feature class id
      Parameters:
      `lineFeatClassId` - a line feature class id or `NFEConnectivityRule.ANY_FEATURE_CLASS_ID` for any line feature class id

    <!-- -->

    - #### getPointFeatureClassId

          public long getPointFeatureClassId()

      Gets the rule's point feature class id
      Returns:
      a point feature class id or `NFEConnectivityRule.ANY_FEATURE_CLASS_ID` indicating the rule applies for all the point feature classes

    <!-- -->

    - #### setPointFeatureClassId

          public void setPointFeatureClassId(long pointFeatClassId)

      Sets the rule's point feature class id
      Parameters:
      `pointFeatClassId` - a point feature class id or `NFEConnectivityRule.ANY_FEATURE_CLASS_ID` for any point feature class id

    <!-- -->

    - #### createCopy

          public NFELinePointRule createCopy()

      Returns a copy of the rule.
      Returns:
      copy of the rule

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

- [Prev Class](NFELineLineRule.md)
- [Next Class](NFELinePointRule.LPRuleSource.md)

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
