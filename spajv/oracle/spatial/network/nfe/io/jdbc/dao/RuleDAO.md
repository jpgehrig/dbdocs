Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkDAO.md)
- [Next Class](SpatialDAO.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.jdbc.dao

## Class RuleDAO

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.dao.AbstractDAO](AbstractDAO.md)

  - - oracle.spatial.network.nfe.io.jdbc.dao.RuleDAO

<!-- -->

-

  ------------------------------------------------------------------------



      public class RuleDAO
      extends AbstractDAO

  The RuleDAO data access object provides methods to load, create and manage the NFE rules. It is not recommended to use the data access objects methods, instead use the NFE services.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `RuleDAO``(java.sql.Connection conn, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Creates a RuleDAO with the specified connection and model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                     | Method and Description                                                                                                                                                                                                                                |
    |---------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                | `deleteDanglingRuleFeatureRel``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` metadata)`<br>Deletes the rules elements that are not referencing existing features from the specified feature layer.                |
    | `void`                                                                                | `deletePointDefaultAttributes``(`[`NFELineLineRule`](../../../model/rule/NFELineLineRule.md)` llRule)`                                                                                                                                                |
    | `void`                                                                                | `deleteRuleInstanceRelations``(java.util.Collection<`[`NFERuleInstanceRelation`](../../../model/rule/NFERuleInstanceRelation.md)`> ruleInstanceRelations)`<br>Deletes the specified feature rule relations from the tables FT_RULE_REL\_\[model_id\]. |
    | `void`                                                                                | `deleteRuleInstances``(java.util.Collection<`[`NFERuleInstance`](../../../model/rule/NFERuleInstance.md)`> ruleInstances)`<br>Deletes the specified rule instances from the tables RULE_INSTANCE\_\[model_id\].                                       |
    | `void`                                                                                | `deleteRules``(java.util.Collection<? extends `[`NFEConnectivityRule`](../../../model/rule/NFEConnectivityRule.md)`> rules)`<br>Deletes the specified rules from the tables LINE_LINE_RULE\_\[model_id\] and LINE_POINT_RULE\_\[model_id\].           |
    | `java.util.List<`[`NFECardinalityRule`](../../../model/rule/NFECardinalityRule.md)`>` | `getCardinalityRules``()`<br>Returns the model's cardinality rules from the table POINT_CARD_RULE\_\[model_id\].                                                                                                                                      |
    | `java.util.List<`[`NFELineLineRule`](../../../model/rule/NFELineLineRule.md)`>`       | `getLineLineRules``(java.util.Collection<`[`NFELinePointRule`](../../../model/rule/NFELinePointRule.md)`> linePointRules)`<br>Returns the model's line line rules from the table LINE_LINE_RULE\_\[model_id\].                                        |
    | `java.util.List<`[`NFELinePointRule`](../../../model/rule/NFELinePointRule.md)`>`     | `getLinePointRules``()`<br>Returns the model's line point rules from the table LINE_POINT_RULE\_\[model_id\].                                                                                                                                         |
    | `boolean`                                                                             | `hasAnyRuleInstanceAssociated``(`[`NFEConnectivityRule`](../../../model/rule/NFEConnectivityRule.md)` rule)`<br>Returns true if any rule instance is related to the specified rule in the table RULE_INSTANCE\_\[model_id\], false otherwise.         |
    | `long`                                                                                | `registerRuleHandler``(java.lang.String handlerFQClassName, `[`NFEConnectivityRule.ConnectivityRuleType`](../../../model/rule/NFEConnectivityRule.ConnectivityRuleType.md)` ruleType)`<br>Saves the rule handler for the specified rule.              |
    | `void`                                                                                | `saveRuleInstances``(java.util.Collection<`[`NFERuleInstance`](../../../model/rule/NFERuleInstance.md)`> ruleInstances)`<br>Persists the new rule instances in the table RULE_INSTANCE\_\[model_id\].                                                 |
    | `void`                                                                                | `saveRuleInstancesRelations``(java.util.Collection<`[`NFERuleInstanceRelation`](../../../model/rule/NFERuleInstanceRelation.md)`> ruleInstanceRelations)`<br>Persists the new feature rule relations in the table FT_RULE_REL\_\[model_id\].          |
    | `void`                                                                                | `saveRules``(java.util.Collection<? extends `[`NFEConnectivityRule`](../../../model/rule/NFEConnectivityRule.md)`> rules)`<br>Persists the new rules in the tables LINE_LINE_RULE\_\[model_id\] and LINE_POINT_RULE\_\[model_id\].                    |
    | `void`                                                                                | `updateRules``(java.util.Collection<? extends `[`NFEConnectivityRule`](../../../model/rule/NFEConnectivityRule.md)`> rules)`<br>Updates the specified rules in the tables LINE_LINE_RULE\_\[model_id\] and LINE_POINT_RULE\_\[model_id\].             |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.dao.[AbstractDAO](AbstractDAO.md)

      [`getConnection`](AbstractDAO.md)`, `[`getModel`](AbstractDAO.md)`, `[`getSQLValidator`](AbstractDAO.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### RuleDAO

          public RuleDAO(java.sql.Connection conn,
                         NFEModel model)

      Creates a RuleDAO with the specified connection and model.
      Parameters:
      `conn` - connection

      `model` - model

  <!-- -->

  - ### Method Detail

    - #### saveRules

          public void saveRules(java.util.Collection<? extends NFEConnectivityRule> rules)
                         throws NFEIOException

      Persists the new rules in the tables LINE_LINE_RULE\_\[model_id\] and LINE_POINT_RULE\_\[model_id\].
      Parameters:
      `rules` - new rules to persist

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deletePointDefaultAttributes

          public void deletePointDefaultAttributes(NFELineLineRule llRule)
                                            throws NFEIOException

      Throws:
      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### updateRules

          public void updateRules(java.util.Collection<? extends NFEConnectivityRule> rules)
                           throws NFEIOException

      Updates the specified rules in the tables LINE_LINE_RULE\_\[model_id\] and LINE_POINT_RULE\_\[model_id\].
      Parameters:
      `rules` - rules to update

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteRules

          public void deleteRules(java.util.Collection<? extends NFEConnectivityRule> rules)
                           throws NFEIOException

      Deletes the specified rules from the tables LINE_LINE_RULE\_\[model_id\] and LINE_POINT_RULE\_\[model_id\].
      Parameters:
      `rules` - rules to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getLinePointRules

          public java.util.List<NFELinePointRule> getLinePointRules()
                                                             throws NFEIOException

      Returns the model's line point rules from the table LINE_POINT_RULE\_\[model_id\].
      Returns:
      the model's line point rules

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getLineLineRules

          public java.util.List<NFELineLineRule> getLineLineRules(java.util.Collection<NFELinePointRule> linePointRules)
                                                           throws NFEIOException

      Returns the model's line line rules from the table LINE_LINE_RULE\_\[model_id\].
      Parameters:
      `linePointRules` - the model line point rules. Those rules will be set to the line line rules.

      Returns:
      the model's line line rules

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### hasAnyRuleInstanceAssociated

          public boolean hasAnyRuleInstanceAssociated(NFEConnectivityRule rule)
                                               throws NFEIOException

      Returns true if any rule instance is related to the specified rule in the table RULE_INSTANCE\_\[model_id\], false otherwise.
      Parameters:
      `rule` - rule

      Returns:
      true if any rule instance is related to the specified rule in the table RULE_INSTANCE\_\[model_id\], false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getCardinalityRules

          public java.util.List<NFECardinalityRule> getCardinalityRules()
                                                                 throws NFEIOException

      Returns the model's cardinality rules from the table POINT_CARD_RULE\_\[model_id\].
      Returns:
      the model's cardinality rules from the table POINT_CARD_RULE\_\[model_id\]

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteDanglingRuleFeatureRel

          public void deleteDanglingRuleFeatureRel(NFEFeatureLayerMetadata metadata)
                                            throws NFEIOException

      Deletes the rules elements that are not referencing existing features from the specified feature layer.
      Parameters:
      `metadata` - feature layer metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteRuleInstanceRelations

          public void deleteRuleInstanceRelations(java.util.Collection<NFERuleInstanceRelation> ruleInstanceRelations)
                                           throws NFEIOException

      Deletes the specified feature rule relations from the tables FT_RULE_REL\_\[model_id\].
      Parameters:
      `ruleInstanceRelations` - feature rule relations to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveRuleInstancesRelations

          public void saveRuleInstancesRelations(java.util.Collection<NFERuleInstanceRelation> ruleInstanceRelations)
                                          throws NFEIOException

      Persists the new feature rule relations in the table FT_RULE_REL\_\[model_id\].
      Parameters:
      `ruleInstanceRelations` - new feature rule relations to persist

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveRuleInstances

          public void saveRuleInstances(java.util.Collection<NFERuleInstance> ruleInstances)
                                 throws NFEIOException

      Persists the new rule instances in the table RULE_INSTANCE\_\[model_id\].
      Parameters:
      `ruleInstances` - new rule instances to persist

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### registerRuleHandler

          public long registerRuleHandler(java.lang.String handlerFQClassName,
                                          NFEConnectivityRule.ConnectivityRuleType ruleType)
                                   throws NFEIOException

      Saves the rule handler for the specified rule.
      Parameters:
      `handlerFQClassName` - rule handler full qualified class name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteRuleInstances

          public void deleteRuleInstances(java.util.Collection<NFERuleInstance> ruleInstances)
                                   throws NFEIOException

      Deletes the specified rule instances from the tables RULE_INSTANCE\_\[model_id\].
      Parameters:
      `ruleInstances` - rule instances to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkDAO.md)
- [Next Class](SpatialDAO.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
