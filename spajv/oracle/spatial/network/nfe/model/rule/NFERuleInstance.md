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

- [Prev Class](NFELinePointRule.LPRuleSource.md)
- [Next Class](NFERuleInstanceRelation.md)

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

## Class NFERuleInstance

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - oracle.spatial.network.nfe.model.rule.NFERuleInstance

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  ------------------------------------------------------------------------



      public class NFERuleInstance
      extends NFEBasicModelObject

  Represents a materialization of a rule. A rule instance is created every time a rule is applied to a set of feature element.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                            |
    |--------------------------------------------------------|
    | `NFERuleInstance``()`<br>Allocates a new rule instance |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                         | Method and Description                                                                                                                                                      |
    |-------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                 | `addFeatureElementRelation``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Adds a relation to the feature element                                  |
    | `boolean`                                                                                 | `addRelation``(`[`NFERuleInstanceRelation`](NFERuleInstanceRelation.md)` relation)`<br>Adds a relation to a feature element.                                                |
    | `long`                                                                                    | `getId``()`<br>Gets the rule instance id                                                                                                                                    |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>`          | `getRelatedFeatureElements``()`<br>Gets all the feature elements currently related to this rule instance                                                                    |
    | `java.util.Collection<`[`NFERuleInstanceRelation`](NFERuleInstanceRelation.md)`>`         | `getRelations``()`<br>Gets all the feature element relations.                                                                                                               |
    | `int`                                                                                     | `getRelationsCount``()`<br>Gets the number of related feature elements                                                                                                      |
    | `long`                                                                                    | `getRuleId``()`<br>Gets the rule instance's rule id                                                                                                                         |
    | [`NFERulesModel`](NFERulesModel.md)                                                       | `getRulesModel``()`<br>Gets the current rules model                                                                                                                         |
    | [`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md) | `getRuleType``()`<br>Gets the rule instance's rule type                                                                                                                     |
    | `boolean`                                                                                 | `isRelatedToFeatureElement``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Tells whether the given feature element is related to the rule instance |
    | `boolean`                                                                                 | `removeFeatureElementRelation``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Removes the relation with the feature element                        |
    | `void`                                                                                    | `setId``(long id)`<br>Sets the rule instance id                                                                                                                             |
    | `void`                                                                                    | `setRuleId``(long ruleId)`<br>Sets the rule instance's rule id                                                                                                              |
    | `void`                                                                                    | `setRulesModel``(`[`NFERulesModel`](NFERulesModel.md)` rulesModel)`<br>Sets the current rules model instance                                                                |
    | `void`                                                                                    | `setRuleType``(`[`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md)` ruleType)`<br>Sets the rule instance's rule type                 |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFERuleInstance

          public NFERuleInstance()

      Allocates a new rule instance

  <!-- -->

  - ### Method Detail

    - #### getRulesModel

          public NFERulesModel getRulesModel()

      Gets the current rules model
      Returns:
      a rules model instance

    <!-- -->

    - #### setRulesModel

          public void setRulesModel(NFERulesModel rulesModel)

      Sets the current rules model instance
      Parameters:
      `rulesModel` - a rules model instance

    <!-- -->

    - #### getId

          public long getId()

      Gets the rule instance id
      Returns:
      a rule instance id

    <!-- -->

    - #### setId

          public void setId(long id)

      Sets the rule instance id
      Parameters:
      `id` - a rule instance id

    <!-- -->

    - #### getRuleId

          public long getRuleId()

      Gets the rule instance's rule id
      Returns:
      a rule id

    <!-- -->

    - #### setRuleId

          public void setRuleId(long ruleId)

      Sets the rule instance's rule id
      Parameters:
      `ruleId` - a rule id

    <!-- -->

    - #### getRuleType

          public NFEConnectivityRule.ConnectivityRuleType getRuleType()

      Gets the rule instance's rule type
      Returns:
      a connectivity rule type

    <!-- -->

    - #### setRuleType

          public void setRuleType(NFEConnectivityRule.ConnectivityRuleType ruleType)

      Sets the rule instance's rule type
      Parameters:
      `ruleType` - a connectivity rule type

    <!-- -->

    - #### addRelation

          public boolean addRelation(NFERuleInstanceRelation relation)

      Adds a relation to a feature element. This method is useful when an existing rule instance representation is created.
      Parameters:
      `relation` - an object defining the relationship between the rule instance and the feature element

      Returns:
      true if the relation was added

    <!-- -->

    - #### addFeatureElementRelation

          public boolean addFeatureElementRelation(NFEFeatureElement featElem)

      Adds a relation to the feature element
      Parameters:
      `featElem` - a feature element

      Returns:
      true if the relation was added

    <!-- -->

    - #### removeFeatureElementRelation

          public boolean removeFeatureElementRelation(NFEFeatureElement featElem)

      Removes the relation with the feature element
      Parameters:
      `featElem` - a feature element

      Returns:
      true if the relation was removed

    <!-- -->

    - #### getRelatedFeatureElements

          public java.util.Collection<NFEFeatureElement> getRelatedFeatureElements()

      Gets all the feature elements currently related to this rule instance
      Returns:
      a colleciton of feature elements

    <!-- -->

    - #### isRelatedToFeatureElement

          public boolean isRelatedToFeatureElement(NFEFeatureElement featElem)

      Tells whether the given feature element is related to the rule instance
      Parameters:
      `featElem` - a feature element

      Returns:
      true if the feature element is related to the rule instance

    <!-- -->

    - #### getRelations

          public java.util.Collection<NFERuleInstanceRelation> getRelations()

      Gets all the feature element relations.
      Returns:
      a collection of rule instance relation objects

    <!-- -->

    - #### getRelationsCount

          public int getRelationsCount()

      Gets the number of related feature elements
      Returns:
      the number of related feature elements

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

- [Prev Class](NFELinePointRule.LPRuleSource.md)
- [Next Class](NFERuleInstanceRelation.md)

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
