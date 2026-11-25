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

- [Prev Class](NFELinePointRuleHandler.md)
- [Next Class](NFEMemoryRuleHandlerContext.md)

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

## Interface NFELinePointRuleHandlerParam

- All Known Implementing Classes:
  [NFEBasicLinePointRuleHandlerParam](NFEBasicLinePointRuleHandlerParam.md)

  ------------------------------------------------------------------------



      public interface NFELinePointRuleHandlerParam

  Line-point rule handler parameter. Contains information regarding the triggered rule, the intersection that triggered the rule and which elements of the intersection currently match the rule's conditions.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                                      | Method and Description                                                                                                                                                       |
    |----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Intersection`](../../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`             | `getIntersection``()`<br>Gets the intersection that is currently being processed.                                                                                            |
    | [`IntersectionMember`](../../spatial/interaction/IntersectionMember.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>` | `getIntersectionMember``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem)`<br>Gets the intersection member representation of the given feature element. |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getMatchingLineFeatureElements``()`<br>Gets all the line feature elements from the current intersection that matches the line operand of the current line-point rule        |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getMatchingPointFeatureElements``()`<br>Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule     |
    | [`NFELinePointRule`](../NFELinePointRule.md)                                                                                           | `getRule``()`<br>The line-point rule that has been triggered                                                                                                                 |

<!-- -->

- - ### Method Detail

    - #### getRule

          NFELinePointRule getRule()

      The line-point rule that has been triggered
      Returns:
      a line-point rule

    <!-- -->

    - #### getIntersection

          Intersection<NFEFeatureElement> getIntersection()

      Gets the intersection that is currently being processed. It contains all the intersecting feature elements.
      Returns:
      an intersection object

    <!-- -->

    - #### getIntersectionMember

          IntersectionMember<NFEFeatureElement> getIntersectionMember(NFEFeatureElement featElem)

      Gets the intersection member representation of the given feature element. The intersection member object describes how the feature element is intersected in the current intersection.
      Parameters:
      `featElem` - a feature element

      Returns:
      the feature element as an intersection member or null if the feature element does not participates in the current intersection

    <!-- -->

    - #### getMatchingLineFeatureElements

          java.util.Collection<NFEFeatureElement> getMatchingLineFeatureElements()

      Gets all the line feature elements from the current intersection that matches the line operand of the current line-point rule
      Returns:
      a collection of line feature elements

    <!-- -->

    - #### getMatchingPointFeatureElements

          java.util.Collection<NFEFeatureElement> getMatchingPointFeatureElements()

      Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule
      Returns:
      a collection of point feature elements

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

- [Prev Class](NFELinePointRuleHandler.md)
- [Next Class](NFEMemoryRuleHandlerContext.md)

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
