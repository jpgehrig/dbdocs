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

- [Prev Class](NFEMemoryRuleHandlerContext.md)
- [Next Class](NFERuleHandlerContext.md)

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

## Interface NFERuleHandler

- All Known Subinterfaces:
  [NFELineLineRuleHandler](NFELineLineRuleHandler.md), [NFELinePointRuleHandler](NFELinePointRuleHandler.md)

  <!-- -->

  All Known Implementing Classes:
  [NFEBasicLineLineRuleHandler](NFEBasicLineLineRuleHandler.md), [NFEBasicLinePointRuleHandler](NFEBasicLinePointRuleHandler.md)

  ------------------------------------------------------------------------



      public interface NFERuleHandler

  Common interface for rule handlers. It only specifies the handler context which every rule handler must contain.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                   | Method and Description                                                                                      |
    |-----------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
    | [`NFERuleHandlerContext`](NFERuleHandlerContext.md) | `getContext``()`<br>Gets the handler's context                                                              |
    | `void`                                              | `setContext``(`[`NFERuleHandlerContext`](NFERuleHandlerContext.md)` context)`<br>Sets the handler's context |

<!-- -->

- - ### Method Detail

    - #### getContext

          NFERuleHandlerContext getContext()

      Gets the handler's context
      Returns:
      a rule handler context object

    <!-- -->

    - #### setContext

          void setContext(NFERuleHandlerContext context)

      Sets the handler's context
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

- [Prev Class](NFEMemoryRuleHandlerContext.md)
- [Next Class](NFERuleHandlerContext.md)

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
