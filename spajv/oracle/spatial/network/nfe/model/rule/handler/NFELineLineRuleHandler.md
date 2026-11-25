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

- [Prev Class](NFEBasicLinePointRuleHandlerParam.md)
- [Next Class](NFELineLineRuleHandlerParam.md)

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

## Interface NFELineLineRuleHandler

- All Superinterfaces:
  [NFERuleHandler](NFERuleHandler.md)

  <!-- -->

  All Known Implementing Classes:
  [NFEBasicLineLineRuleHandler](NFEBasicLineLineRuleHandler.md)

  ------------------------------------------------------------------------



      public interface NFELineLineRuleHandler
      extends NFERuleHandler

  Defines a line-line rule handler. A handler of this type is assigned to a line-line rule and is fired when the rule is triggered. A rule handler is responsible of specifying which elements will be connected when a line-point rule is applicable. The rule handler receives information about which elements are applicable for a rule.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                                                                                                               | Method and Description                                                                                                                                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List<`[`NFEConnectionDescriptor`](../../edit/NFEConnectionDescriptor.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`,`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>>` | `getConnectionDescriptors``(`[`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)` param)`<br>Gets a list connection descriptors which define how and which of the elements given the parameter, are going to be connected. |

    - ### Methods inherited from interface oracle.spatial.network.nfe.model.rule.handler.[NFERuleHandler](NFERuleHandler.md)

      [`getContext`](NFERuleHandler.md)`, `[`setContext`](NFERuleHandler.md)

<!-- -->

- - ### Method Detail

    - #### getConnectionDescriptors

          java.util.List<NFEConnectionDescriptor<NFEFeatureElement,NFEFeatureElement>> getConnectionDescriptors(NFELineLineRuleHandlerParam param)

      Gets a list connection descriptors which define how and which of the elements given the parameter, are going to be connected.
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

- [Prev Class](NFEBasicLinePointRuleHandlerParam.md)
- [Next Class](NFELineLineRuleHandlerParam.md)

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
