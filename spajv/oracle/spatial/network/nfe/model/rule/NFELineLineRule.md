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

- [Prev Class](NFEConnectivityRule.ConnectivityRuleType.md)
- [Next Class](NFELinePointRule.md)

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

## Class NFELineLineRule

- java.lang.Object

- - [oracle.spatial.network.nfe.model.rule.NFEConnectivityRule](NFEConnectivityRule.md)

  - - oracle.spatial.network.nfe.model.rule.NFELineLineRule

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFELineLineRule
      extends NFEConnectivityRule

  A representation of an NFE line-line connectivity rule

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.spatial.network.nfe.model.rule.[NFEConnectivityRule](NFEConnectivityRule.md)

      [`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md)

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class oracle.spatial.network.nfe.model.rule.[NFEConnectivityRule](NFEConnectivityRule.md)

      [`ANY_FEATURE_CLASS_ID`](NFEConnectivityRule.md)`, `[`ANY_FEATURE_LAYER_ID`](NFEConnectivityRule.md)`, `[`DEFAULT_LL_HANDLER_ID`](NFEConnectivityRule.md)`, `[`DEFAULT_LP_HANDLER_ID`](NFEConnectivityRule.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                    |
    |----------------------------------------------------------------|
    | `NFELineLineRule``(long id)`<br>Allocates a new line-line rule |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                         | Method and Description                                                                                                                                                                |
    |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                    | `addDefaultPointInitValue``(java.lang.String attrName, java.lang.Object value)`<br>Adds an attribute value for initializing a point when it is automatically created by the rule      |
    | `NFELineLineRule`                                                                         | `createCopy``()`<br>Returns a copy of the rule.                                                                                                                                       |
    | `java.util.Map<java.lang.String,java.lang.Object>`                                        | `getDefaultPointInitValues``()`<br>Gets a map containing all the point feature attributes and its initialization values                                                               |
    | [`BinaryInteraction`](../spatial/interaction/BinaryInteraction.md)                        | `getInteraction``()`<br>Gets the binary interaction which triggers this rule                                                                                                          |
    | [`NFELinePointRule`](NFELinePointRule.md)                                                 | `getLeftHandSideLinePointRule``()`<br>Gets the line-point rule that corresponds to the left hand side operand of the line-line rule                                                   |
    | `long`                                                                                    | `getPointFeatureClassId``()`<br>Gets the feature class id of the point connecting both lines of the rule.                                                                             |
    | `long`                                                                                    | `getPointFeatureLayerId``()`<br>Gets the feature layer id of the point connecting both lines of the rule.                                                                             |
    | [`NFELinePointRule`](NFELinePointRule.md)                                                 | `getRightHandSideLinePointRule``()`<br>Gets the line-point rule that corresponds to the right hand side operand of the line-line rule                                                 |
    | [`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md) | `getType``()`<br>Gets the actual connectivity rule type                                                                                                                               |
    | `boolean`                                                                                 | `isCreatePoint``()`<br>Tells whether the rule creates a point automatically if it does not exist                                                                                      |
    | `boolean`                                                                                 | `removeDefaultPointInitValue``(java.lang.String attrName)`<br>Removes an point feature's initialization attribute value                                                               |
    | `void`                                                                                    | `setCreatePoint``(boolean createPoint)`<br>Sets whether the rule creates a point automatically if it does not exist                                                                   |
    | `void`                                                                                    | `setInteraction``(`[`BinaryInteraction`](../spatial/interaction/BinaryInteraction.md)` interaction)`<br>Sets the binary interaction which triggers this rule                          |
    | `void`                                                                                    | `setLeftHandSideLinePointRule``(`[`NFELinePointRule`](NFELinePointRule.md)` llpr)`<br>Sets the line-point rule that corresponds to the left hand side operand of the line-line rule   |
    | `void`                                                                                    | `setRightHandSideLinePointRule``(`[`NFELinePointRule`](NFELinePointRule.md)` rlpr)`<br>Sets the line-point rule that corresponds to the right hand side operand of the line-line rule |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.rule.[NFEConnectivityRule](NFEConnectivityRule.md)

      [`getExecutionOrder`](NFEConnectivityRule.md)`, `[`getHandler`](NFEConnectivityRule.md)`, `[`getHandlerClass`](NFEConnectivityRule.md)`, `[`getHandlerClassName`](NFEConnectivityRule.md)`, `[`getHandlerId`](NFEConnectivityRule.md)`, `[`getId`](NFEConnectivityRule.md)`, `[`getKey`](NFEConnectivityRule.md)`, `[`setExecutionOrder`](NFEConnectivityRule.md)`, `[`setHandler`](NFEConnectivityRule.md)`, `[`setHandlerClass`](NFEConnectivityRule.md)`, `[`setHandlerClassName`](NFEConnectivityRule.md)`, `[`setHandlerId`](NFEConnectivityRule.md)`, `[`setId`](NFEConnectivityRule.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFELineLineRule

          public NFELineLineRule(long id)

      Allocates a new line-line rule
      Parameters:
      `id` - the line-line rule id

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

    - #### getInteraction

          public BinaryInteraction getInteraction()

      Gets the binary interaction which triggers this rule
      Returns:
      a binary interaction

    <!-- -->

    - #### setInteraction

          public void setInteraction(BinaryInteraction interaction)

      Sets the binary interaction which triggers this rule
      Parameters:
      `interaction` - a binary interaction

    <!-- -->

    - #### isCreatePoint

          public boolean isCreatePoint()

      Tells whether the rule creates a point automatically if it does not exist
      Returns:
      true if the rule creates a point

    <!-- -->

    - #### setCreatePoint

          public void setCreatePoint(boolean createPoint)

      Sets whether the rule creates a point automatically if it does not exist
      Parameters:
      `createPoint` - true if the rule creates a point

    <!-- -->

    - #### getLeftHandSideLinePointRule

          public NFELinePointRule getLeftHandSideLinePointRule()

      Gets the line-point rule that corresponds to the left hand side operand of the line-line rule
      Returns:
      a line-point rule

    <!-- -->

    - #### setLeftHandSideLinePointRule

          public void setLeftHandSideLinePointRule(NFELinePointRule llpr)

      Sets the line-point rule that corresponds to the left hand side operand of the line-line rule
      Parameters:
      `llpr` - a line-point rule

    <!-- -->

    - #### getRightHandSideLinePointRule

          public NFELinePointRule getRightHandSideLinePointRule()

      Gets the line-point rule that corresponds to the right hand side operand of the line-line rule
      Returns:
      a line-point rule

    <!-- -->

    - #### setRightHandSideLinePointRule

          public void setRightHandSideLinePointRule(NFELinePointRule rlpr)

      Sets the line-point rule that corresponds to the right hand side operand of the line-line rule
      Parameters:
      `rlpr` -

    <!-- -->

    - #### getPointFeatureLayerId

          public long getPointFeatureLayerId()

      Gets the feature layer id of the point connecting both lines of the rule. It is a short hand for get(Right/Left)HandSideLinePointRule().getPointFeatureLayerId()
      Returns:
      a point feature layer id

    <!-- -->

    - #### getPointFeatureClassId

          public long getPointFeatureClassId()

      Gets the feature class id of the point connecting both lines of the rule. get(Right/Left)HandSideLinePointRule().getPointFeatureClassId()
      Returns:
      a point feature class id

    <!-- -->

    - #### addDefaultPointInitValue

          public void addDefaultPointInitValue(java.lang.String attrName,
                                               java.lang.Object value)

      Adds an attribute value for initializing a point when it is automatically created by the rule
      Parameters:
      `attrName` - a point feature attribute name

      `value` - the point feature attribute value

    <!-- -->

    - #### removeDefaultPointInitValue

          public boolean removeDefaultPointInitValue(java.lang.String attrName)

      Removes an point feature's initialization attribute value
      Parameters:
      `attrName` - a point feature attribute name

      Returns:
      true if the value could be removed

    <!-- -->

    - #### getDefaultPointInitValues

          public java.util.Map<java.lang.String,java.lang.Object> getDefaultPointInitValues()

      Gets a map containing all the point feature attributes and its initialization values
      Returns:
      a map of the form attribute name - initialization value

    <!-- -->

    - #### createCopy

          public NFELineLineRule createCopy()

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

- [Prev Class](NFEConnectivityRule.ConnectivityRuleType.md)
- [Next Class](NFELinePointRule.md)

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
