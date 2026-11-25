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

- Prev Class
- [Next Class](NFEBasicLineLineRuleHandlerParam.md)

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

oracle.spatial.network.nfe.model.rule.handler

## Class NFEBasicLineLineRuleHandler

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.handler.NFEBasicLineLineRuleHandler

<!-- -->

- All Implemented Interfaces:
  [NFELineLineRuleHandler](NFELineLineRuleHandler.md), [NFERuleHandler](NFERuleHandler.md)

  ------------------------------------------------------------------------



      public class NFEBasicLineLineRuleHandler
      extends java.lang.Object
      implements NFELineLineRuleHandler

  The default implementation of [`NFELineLineRuleHandler`](NFELineLineRuleHandler.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description        |
    |------------------------------------|
    | `NFEBasicLineLineRuleHandler``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                                                                                               | Method and Description                                                                                                                                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List<`[`NFEConnectionDescriptor`](../../edit/NFEConnectionDescriptor.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`,`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>>` | `getConnectionDescriptors``(`[`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)` param)`<br>Gets a list connection descriptors which define how and which of the elements given the parameter, are going to be connected. |
    | [`NFERuleHandlerContext`](NFERuleHandlerContext.md)                                                                                                                                                             | `getContext``()`<br>Gets the handler's context                                                                                                                                                                                         |
    | `void`                                                                                                                                                                                                          | `setContext``(`[`NFERuleHandlerContext`](NFERuleHandlerContext.md)` context)`<br>Sets the handler's context                                                                                                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicLineLineRuleHandler

          public NFEBasicLineLineRuleHandler()

  <!-- -->

  - ### Method Detail

    - #### getContext

          public NFERuleHandlerContext getContext()

      Description copied from interface: [`NFERuleHandler`](NFERuleHandler.md)
      Gets the handler's context
      Specified by:
      [`getContext`](NFERuleHandler.md) in interface [`NFERuleHandler`](NFERuleHandler.md)

      Returns:
      a rule handler context object

    <!-- -->

    - #### setContext

          public void setContext(NFERuleHandlerContext context)

      Description copied from interface: [`NFERuleHandler`](NFERuleHandler.md)
      Sets the handler's context
      Specified by:
      [`setContext`](NFERuleHandler.md) in interface [`NFERuleHandler`](NFERuleHandler.md)

      Parameters:
      `context` - a rule handler context object

    <!-- -->

    - #### getConnectionDescriptors

          public java.util.List<NFEConnectionDescriptor<NFEFeatureElement,NFEFeatureElement>> getConnectionDescriptors(NFELineLineRuleHandlerParam param)

      Description copied from interface: [`NFELineLineRuleHandler`](NFELineLineRuleHandler.md)
      Gets a list connection descriptors which define how and which of the elements given the parameter, are going to be connected.
      Specified by:
      [`getConnectionDescriptors`](NFELineLineRuleHandler.md) in interface [`NFELineLineRuleHandler`](NFELineLineRuleHandler.md)

      Parameters:
      `param` - contains all the elements intersecting in one point. Additionally, it also specifies which elements match the current rule.

      Returns:
      a list of connection descriptors

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

- Prev Class
- [Next Class](NFEBasicLineLineRuleHandlerParam.md)

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
