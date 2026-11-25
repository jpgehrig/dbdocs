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

- [Prev Class](NFEBasicLineLineRuleHandlerParam.md)
- [Next Class](NFEBasicLinePointRuleHandlerParam.md)

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

## Class NFEBasicLinePointRuleHandler

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.handler.NFEBasicLinePointRuleHandler

<!-- -->

- All Implemented Interfaces:
  [NFELinePointRuleHandler](NFELinePointRuleHandler.md), [NFERuleHandler](NFERuleHandler.md)

  ------------------------------------------------------------------------



      public class NFEBasicLinePointRuleHandler
      extends java.lang.Object
      implements NFELinePointRuleHandler

  The default implementation of [`NFELinePointRuleHandler`](NFELinePointRuleHandler.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description         |
    |-------------------------------------|
    | `NFEBasicLinePointRuleHandler``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                                                                                               | Method and Description                                                                                                                                                                                                                   |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List<`[`NFEConnectionDescriptor`](../../edit/NFEConnectionDescriptor.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`,`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>>` | `getConnectionDescriptors``(`[`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)` param)`<br>Gets a list connection descriptors which define how and which of the elements given the parameter, are going to be connected. |
    | [`NFERuleHandlerContext`](NFERuleHandlerContext.md)                                                                                                                                                             | `getContext``()`<br>Gets the handler's context                                                                                                                                                                                           |
    | `void`                                                                                                                                                                                                          | `setContext``(`[`NFERuleHandlerContext`](NFERuleHandlerContext.md)` context)`<br>Sets the handler's context                                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicLinePointRuleHandler

          public NFEBasicLinePointRuleHandler()

  <!-- -->

  - ### Method Detail

    - #### getConnectionDescriptors

          public java.util.List<NFEConnectionDescriptor<NFEFeatureElement,NFEFeatureElement>> getConnectionDescriptors(NFELinePointRuleHandlerParam param)

      Description copied from interface: [`NFELinePointRuleHandler`](NFELinePointRuleHandler.md)
      Gets a list connection descriptors which define how and which of the elements given the parameter, are going to be connected.
      Specified by:
      [`getConnectionDescriptors`](NFELinePointRuleHandler.md) in interface [`NFELinePointRuleHandler`](NFELinePointRuleHandler.md)

      Parameters:
      `param` - contains all the elements intersecting in one point. Additionally, it also specifies which elements match the current rule.

      Returns:
      a list of connection descriptors

    <!-- -->

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

- [Prev Class](NFEBasicLineLineRuleHandlerParam.md)
- [Next Class](NFEBasicLinePointRuleHandlerParam.md)

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
