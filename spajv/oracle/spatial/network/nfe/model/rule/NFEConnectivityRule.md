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

- [Prev Class](NFECardinalityRule.md)
- [Next Class](NFEConnectivityRule.ConnectivityRuleType.md)

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

## Class NFEConnectivityRule

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.NFEConnectivityRule

<!-- -->

- Direct Known Subclasses:
  [NFELineLineRule](NFELineLineRule.md), [NFELinePointRule](NFELinePointRule.md)

  ------------------------------------------------------------------------



      public abstract class NFEConnectivityRule
      extends java.lang.Object

  Basic representation of a connectivity rule which defines the properties and methods common to all the NFE connectivity rules

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                        |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md)<br>Defines connectivity rule types |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                         |
    |-------------------|---------------------------------------------------------------|
    | `static long`     | `ANY_FEATURE_CLASS_ID`<br>Any feature class id                |
    | `static long`     | `ANY_FEATURE_LAYER_ID`<br>Any feature layer id                |
    | `static long`     | `DEFAULT_LL_HANDLER_ID`<br>Default line line-rule handler id  |
    | `static long`     | `DEFAULT_LP_HANDLER_ID`<br>Default line-point rule handler id |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description       |
    |-----------------------------------|
    | `NFEConnectivityRule``(long id)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                           |
    |------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                                                | `getExecutionOrder``()`<br>Gets the rule execution order                                                                         |
    | [`NFERuleHandler`](handler/NFERuleHandler.md)                                                        | `getHandler``()`<br>Gets the rule handler instance associated to the rule                                                        |
    | `java.lang.Class<? extends `[`NFERuleHandler`](handler/NFERuleHandler.md)`>`                         | `getHandlerClass``()`<br>Gets the class of rule handler associated to the rule                                                   |
    | `java.lang.String`                                                                                   | `getHandlerClassName``()`<br>Gets the name of the rule habdler's class associated to the rule                                    |
    | `long`                                                                                               | `getHandlerId``()`<br>Gets the id of the rule handler associated to the rule                                                     |
    | `long`                                                                                               | `getId``()`<br>Gets the rule id                                                                                                  |
    | `java.lang.String`                                                                                   | `getKey``()`<br>Gets the rule key which is used to uniquely identify the rule across other types of connectivity rules           |
    | `abstract `[`NFEConnectivityRule.ConnectivityRuleType`](NFEConnectivityRule.ConnectivityRuleType.md) | `getType``()`<br>Gets the actual connectivity rule type                                                                          |
    | `void`                                                                                               | `setExecutionOrder``(int executionOrder)`<br>Sets the rule execution order                                                       |
    | `void`                                                                                               | `setHandler``(`[`NFERuleHandler`](handler/NFERuleHandler.md)` handler)`<br>Sets the rule handler instance associated to the rule |
    | `void`                                                                                               | `setHandlerClass``(java.lang.Class<? extends `[`NFERuleHandler`](handler/NFERuleHandler.md)`> handlerClass)`                     |
    | `void`                                                                                               | `setHandlerClassName``(java.lang.String handlerClassName)`<br>Sets the name of the rule habdler's class associated to the rule   |
    | `void`                                                                                               | `setHandlerId``(long handlerId)`<br>Sets the id of the rule handler associated to the rule                                       |
    | `void`                                                                                               | `setId``(long id)`<br>Sets the rule id                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ANY_FEATURE_LAYER_ID

          public static final long ANY_FEATURE_LAYER_ID

      Any feature layer id
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### ANY_FEATURE_CLASS_ID

          public static final long ANY_FEATURE_CLASS_ID

      Any feature class id
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_LP_HANDLER_ID

          public static final long DEFAULT_LP_HANDLER_ID

      Default line-point rule handler id
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_LL_HANDLER_ID

          public static final long DEFAULT_LL_HANDLER_ID

      Default line line-rule handler id
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFEConnectivityRule

          public NFEConnectivityRule(long id)

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Gets the rule id
      Returns:
      the rule id

    <!-- -->

    - #### setId

          public void setId(long id)

      Sets the rule id
      Parameters:
      `id` - the rule id

    <!-- -->

    - #### getExecutionOrder

          public int getExecutionOrder()

      Gets the rule execution order
      Returns:
      the rule execution order

    <!-- -->

    - #### setExecutionOrder

          public void setExecutionOrder(int executionOrder)

      Sets the rule execution order
      Parameters:
      `executionOrder` - the rule execution order

    <!-- -->

    - #### getHandlerClass

          public java.lang.Class<? extends NFERuleHandler> getHandlerClass()

      Gets the class of rule handler associated to the rule
      Returns:
      the rule handler class

    <!-- -->

    - #### setHandlerClass

          public void setHandlerClass(java.lang.Class<? extends NFERuleHandler> handlerClass)

    <!-- -->

    - #### getHandler

          public NFERuleHandler getHandler()

      Gets the rule handler instance associated to the rule
      Returns:
      the rule handler instance

    <!-- -->

    - #### setHandler

          public void setHandler(NFERuleHandler handler)

      Sets the rule handler instance associated to the rule
      Parameters:
      `handler` - the rule handler instance

    <!-- -->

    - #### getHandlerId

          public long getHandlerId()

      Gets the id of the rule handler associated to the rule
      Returns:
      a rule handler id

    <!-- -->

    - #### setHandlerId

          public void setHandlerId(long handlerId)

      Sets the id of the rule handler associated to the rule
      Parameters:
      `handlerId` - a rule handler id

    <!-- -->

    - #### getKey

          public java.lang.String getKey()

      Gets the rule key which is used to uniquely identify the rule across other types of connectivity rules
      Returns:
      the rule key

    <!-- -->

    - #### getHandlerClassName

          public java.lang.String getHandlerClassName()

      Gets the name of the rule habdler's class associated to the rule
      Returns:
      a rule handler's class name

    <!-- -->

    - #### setHandlerClassName

          public void setHandlerClassName(java.lang.String handlerClassName)

      Sets the name of the rule habdler's class associated to the rule
      Parameters:
      `handlerClassName` - a rule handler's class name

    <!-- -->

    - #### getType

          public abstract NFEConnectivityRule.ConnectivityRuleType getType()

      Gets the actual connectivity rule type
      Returns:
      a connectivity rule type

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

- [Prev Class](NFECardinalityRule.md)
- [Next Class](NFEConnectivityRule.ConnectivityRuleType.md)

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
