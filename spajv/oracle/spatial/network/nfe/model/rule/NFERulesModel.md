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

- [Prev Class](NFERulesEngine.md)
- Next Class

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

## Class NFERulesModel

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.NFERulesModel

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, [NFEModelListener](../event/NFEModelListener.md)

  ------------------------------------------------------------------------



      public class NFERulesModel
      extends java.lang.Object
      implements NFEModelListener

  NFE component used as a holder and manager of rules. Components interested on events related to rules instances should be subscribed to the NFERulesModels as NFEModelListeners.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.event.[NFEModelListener](../event/NFEModelListener.md)

      [`METHOD_MODEL_OBJECT_ADDED`](../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECT_REMOVED`](../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_ADDED`](../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_REMOVED`](../event/NFEModelListener.md)`, `[`METHOD_PROPERTY_CHANGED`](../event/NFEModelListener.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                        |
    |----------------------------------------------------------------------------------------------------|
    | `NFERulesModel``(`[`NFEModel`](../NFEModel.md)` model)`<br>Creates a new instance of NFERulesModel |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                              | Method and Description                                                                                                                                                                                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                         | `addCardinalityRule``(`[`NFECardinalityRule`](NFECardinalityRule.md)` cardRule)`<br>Adds a cardinality rule to the rules model                                                                                                                                                                                            |
    | `void`                                                                                                         | `addCardinalityRules``(java.util.Collection<`[`NFECardinalityRule`](NFECardinalityRule.md)`> cardRules)`<br>Adds all the cardinality rules to the rules model                                                                                                                                                             |
    | `void`                                                                                                         | `addConnectivityRules``(java.util.Collection<? extends `[`NFEConnectivityRule`](NFEConnectivityRule.md)`> rules)`<br>Adds all the connectivity rules to the rules model.                                                                                                                                                  |
    | `void`                                                                                                         | `addLineLineRule``(`[`NFELineLineRule`](NFELineLineRule.md)` llRule)`<br>Adds a line-line rule to the rules model                                                                                                                                                                                                         |
    | `void`                                                                                                         | `addLinePointRule``(`[`NFELinePointRule`](NFELinePointRule.md)` lpRule)`<br>Adds a line-point rule to the rules model                                                                                                                                                                                                     |
    | `void`                                                                                                         | `addModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`<br>Subscribes a model listener to receive events about rule instances                                                                                                                                                                 |
    | `boolean`                                                                                                      | `addRuleInstance``(`[`NFERuleInstance`](NFERuleInstance.md)` ruleInstance)`<br>Adds a new rule instance to the rule model                                                                                                                                                                                                 |
    | [`NFECardinalityRule`](NFECardinalityRule.md)                                                                  | `getCardinalityRule``(`[`NFEFeatureClass`](../feature/NFEFeatureClass.md)` featClass)`<br>Gets cardinality rule applicable for the given feature class                                                                                                                                                                    |
    | `java.util.Collection<`[`NFECardinalityRule`](NFECardinalityRule.md)`>`                                        | `getCardinalityRules``()`<br>Gets all the cardinality rules contained in the rules model                                                                                                                                                                                                                                  |
    | [`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`>` | `getEventDispatcher``()`                                                                                                                                                                                                                                                                                                  |
    | `java.util.Collection<`[`NFELineLineRule`](NFELineLineRule.md)`>`                                              | `getLineLineRules``()`<br>Gets all the line-line rules contained in the rules model                                                                                                                                                                                                                                       |
    | `java.util.Collection<`[`NFELinePointRule`](NFELinePointRule.md)`>`                                            | `getLinePointRules``()`<br>Gets all the line-point rules contained in the rules model                                                                                                                                                                                                                                     |
    | [`NFEModel`](../NFEModel.md)                                                                                   | `getModel``()`<br>Gets the NFE model associated to the rules model                                                                                                                                                                                                                                                        |
    | [`NFERuleInstance`](NFERuleInstance.md)                                                                        | `getRuleInstance``(long ruleInstanceId)`<br>Gets the rule instance identified by the given id                                                                                                                                                                                                                             |
    | `java.util.Collection<`[`NFERuleInstance`](NFERuleInstance.md)`>`                                              | `getRuleInstances``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Gets all the rule instances associated to the given feature element                                                                                                                                                            |
    | `java.util.Collection<`[`NFERuleInstance`](NFERuleInstance.md)`>`                                              | `getRuleInstances``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem, `[`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md)` type)`<br>Gets all the rule instances associated to the given feature element and created by a connectivity rule of the specified type |
    | `void`                                                                                                         | `modelObjectAdded``(`[`NFEModelObjectEvent`](../event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                                                                                                                                                      |
    | `void`                                                                                                         | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](../event/NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed                                                                                                                                 |
    | `void`                                                                                                         | `modelObjectRemoved``(`[`NFEModelObjectEvent`](../event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                                                                                                                                                  |
    | `void`                                                                                                         | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](../event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                                                                                                                                                       |
    | `void`                                                                                                         | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](../event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                                                                                                                                                   |
    | `boolean`                                                                                                      | `removeCardinalityRule``(`[`NFECardinalityRule`](NFECardinalityRule.md)` cardRule)`<br>Removes a cardinality rule from the model                                                                                                                                                                                          |
    | `boolean`                                                                                                      | `removeLineLineRule``(`[`NFELineLineRule`](NFELineLineRule.md)` llRule)`<br>Removes the given line-line rule                                                                                                                                                                                                              |
    | `boolean`                                                                                                      | `removeLinePointRule``(`[`NFELinePointRule`](NFELinePointRule.md)` lpRule)`<br>Removes the given line-point rule from the model                                                                                                                                                                                           |
    | `void`                                                                                                         | `removeModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`<br>Removes a model listener                                                                                                                                                                                                        |
    | [`NFERuleInstance`](NFERuleInstance.md)                                                                        | `removeRuleInstance``(long ruleInstanceId)`<br>Removes from the rules model the rule instance identified by the given id                                                                                                                                                                                                  |
    | `void`                                                                                                         | `setEventDispatcher``(`[`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`> eventDispatcher)`                                                                                                                                                                    |
    | `void`                                                                                                         | `transferRuleInstances``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` srcFeatElem, `[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` dstFeatElem)`<br>Associates to dstFeatElem all the rule instances associated to srcFeatElem.                                                                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFERulesModel

          public NFERulesModel(NFEModel model)

      Creates a new instance of NFERulesModel
      Parameters:
      `model` - the current NFE model

  <!-- -->

  - ### Method Detail

    - #### getModel

          public NFEModel getModel()

      Gets the NFE model associated to the rules model
      Returns:
      an NFE model instance

    <!-- -->

    - #### addConnectivityRules

          public void addConnectivityRules(java.util.Collection<? extends NFEConnectivityRule> rules)

      Adds all the connectivity rules to the rules model.
      Parameters:
      `rules` - a collection containing connectivity rule implementations

    <!-- -->

    - #### addLinePointRule

          public void addLinePointRule(NFELinePointRule lpRule)

      Adds a line-point rule to the rules model
      Parameters:
      `lpRule` - a line-point rule

    <!-- -->

    - #### removeLinePointRule

          public boolean removeLinePointRule(NFELinePointRule lpRule)

      Removes the given line-point rule from the model
      Parameters:
      `lpRule` - a line-point rule

      Returns:
      true if the rule could be removed

    <!-- -->

    - #### getLinePointRules

          public java.util.Collection<NFELinePointRule> getLinePointRules()

      Gets all the line-point rules contained in the rules model
      Returns:
      a collection containing line-point rules

    <!-- -->

    - #### addLineLineRule

          public void addLineLineRule(NFELineLineRule llRule)

      Adds a line-line rule to the rules model
      Parameters:
      `llRule` - a line-line rule

    <!-- -->

    - #### getLineLineRules

          public java.util.Collection<NFELineLineRule> getLineLineRules()

      Gets all the line-line rules contained in the rules model
      Returns:
      a line-line rule

    <!-- -->

    - #### removeLineLineRule

          public boolean removeLineLineRule(NFELineLineRule llRule)

      Removes the given line-line rule
      Parameters:
      `llRule` - a line-line rule from the model

      Returns:
      true if the rule could be removed

    <!-- -->

    - #### addCardinalityRules

          public void addCardinalityRules(java.util.Collection<NFECardinalityRule> cardRules)

      Adds all the cardinality rules to the rules model
      Parameters:
      `cardRules` - a collection containing cardinality rules

    <!-- -->

    - #### addCardinalityRule

          public void addCardinalityRule(NFECardinalityRule cardRule)

      Adds a cardinality rule to the rules model
      Parameters:
      `cardRule` - a cardinality rule

    <!-- -->

    - #### getCardinalityRules

          public java.util.Collection<NFECardinalityRule> getCardinalityRules()

      Gets all the cardinality rules contained in the rules model
      Returns:
      a collection containing cardinality rules

    <!-- -->

    - #### getCardinalityRule

          public NFECardinalityRule getCardinalityRule(NFEFeatureClass featClass)

      Gets cardinality rule applicable for the given feature class
      Parameters:
      `featClass` - a feature class

      Returns:
      a cardinality rule or null if the feature class does not have any cardinality rule

    <!-- -->

    - #### removeCardinalityRule

          public boolean removeCardinalityRule(NFECardinalityRule cardRule)

      Removes a cardinality rule from the model
      Parameters:
      `cardRule` - a cardinality rule

      Returns:
      true if the rule could be removed

    <!-- -->

    - #### addRuleInstance

          public boolean addRuleInstance(NFERuleInstance ruleInstance)

      Adds a new rule instance to the rule model
      Parameters:
      `ruleInstance` - a rule instance

      Returns:
      true if the rule could be added to the model

    <!-- -->

    - #### removeRuleInstance

          public NFERuleInstance removeRuleInstance(long ruleInstanceId)

      Removes from the rules model the rule instance identified by the given id
      Parameters:
      `ruleInstanceId` - a rule instance id

      Returns:
      true if the rule instance could be removed

    <!-- -->

    - #### getRuleInstance

          public NFERuleInstance getRuleInstance(long ruleInstanceId)

      Gets the rule instance identified by the given id
      Parameters:
      `ruleInstanceId` - a rule instance id

      Returns:
      a rule instance

    <!-- -->

    - #### getRuleInstances

          public java.util.Collection<NFERuleInstance> getRuleInstances(NFEFeatureElement featElem)

      Gets all the rule instances associated to the given feature element
      Parameters:
      `featElem` - a feature element

      Returns:
      a collection of rule instances

    <!-- -->

    - #### getRuleInstances

          public java.util.Collection<NFERuleInstance> getRuleInstances(NFEFeatureElement featElem,
                                                                        NFEConnectivityRule.ConnectivityRuleType type)

      Gets all the rule instances associated to the given feature element and created by a connectivity rule of the specified type
      Parameters:
      `featElem` - a feature element

      `type` - a connectivity rule type

      Returns:
      a collection of rule instances

    <!-- -->

    - #### addModelListener

          public void addModelListener(NFEModelListener listener)

      Subscribes a model listener to receive events about rule instances
      Parameters:
      `listener` - a model listener implementation

    <!-- -->

    - #### removeModelListener

          public void removeModelListener(NFEModelListener listener)

      Removes a model listener
      Parameters:
      `listener` - a model listener implementation

    <!-- -->

    - #### setEventDispatcher

          public void setEventDispatcher(NFEEventDispatcher<NFEModelListener> eventDispatcher)

    <!-- -->

    - #### getEventDispatcher

          public NFEEventDispatcher<NFEModelListener> getEventDispatcher()

    <!-- -->

    - #### modelObjectAdded

          public void modelObjectAdded(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when a model object has been added
      Specified by:
      [`modelObjectAdded`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been added

    <!-- -->

    - #### modelObjectsAdded

          public void modelObjectsAdded(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when one or more model objects have been added
      Specified by:
      [`modelObjectsAdded`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been added

    <!-- -->

    - #### modelObjectRemoved

          public void modelObjectRemoved(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when a model object has been removed
      Specified by:
      [`modelObjectRemoved`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been removed

    <!-- -->

    - #### modelObjectsRemoved

          public void modelObjectsRemoved(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when one or more model objects have been removed
      Specified by:
      [`modelObjectsRemoved`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been removed

    <!-- -->

    - #### modelObjectPropertyChanged

          public void modelObjectPropertyChanged(NFEModelObjectPropertyChangedEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when a model object's property has been changed
      Specified by:
      [`modelObjectPropertyChanged`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model objects which property has been changed and the name and previous value of the changed property

    <!-- -->

    - #### transferRuleInstances

          public void transferRuleInstances(NFEFeatureElement srcFeatElem,
                                            NFEFeatureElement dstFeatElem)

      Associates to dstFeatElem all the rule instances associated to srcFeatElem. Also removes the associations with srcFeatElem
      Parameters:
      `srcFeatElem` - the feature element from which the rule instances want to be moved

      `dstFeatElem` - the feature element which will be associated to the rule instances

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

- [Prev Class](NFERulesEngine.md)
- Next Class

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
