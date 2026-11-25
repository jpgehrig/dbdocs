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

- [Prev Class](NFELineLineRuleHandler.md)
- [Next Class](NFELinePointRuleHandler.md)

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

## Interface NFELineLineRuleHandlerParam

- All Known Implementing Classes:
  [NFEBasicLineLineRuleHandlerParam](NFEBasicLineLineRuleHandlerParam.md)

  ------------------------------------------------------------------------



      public interface NFELineLineRuleHandlerParam

  Line-line rule handler parameter. Contains information regarding the triggered rule, the intersection that triggered the rule and which elements of the intersection currently match the rule's conditions.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                                      | Method and Description                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Intersection`](../../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`             | `getIntersection``()`<br>Gets the intersection that is currently being processed.                                                                                                                 |
    | [`IntersectionMember`](../../spatial/interaction/IntersectionMember.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>` | `getIntersectionMember``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem)`<br>Gets the feature element as an intersection member of the current intersection.                |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getMatchingPointFeatureElements``()`<br>Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule                          |
    | [`NFELineLineRule`](../NFELineLineRule.md)                                                                                             | `getRule``()`<br>The line-point rule that has been triggered                                                                                                                                      |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getRuleLeftHandMatchingLineFeatureElements``()`<br>Gets all the line feature elements from the current intersection that matches the left hand side line operand of the current line-line rule   |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getRuleRightHandMatchingLineFeatureElements``()`<br>Gets all the line feature elements from the current intersection that matches the right hand side line operand of the current line-line rule |

<!-- -->

- - ### Method Detail

    - #### getRule

          NFELineLineRule getRule()

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

      Gets the feature element as an intersection member of the current intersection. The intersection member object describes how the feature element is intersected in the current intersection group.
      Parameters:
      `featElem` - a feature element

      Returns:
      the feature element as an intersection member or null if the feature element does not participates in the current intersection

    <!-- -->

    - #### getRuleLeftHandMatchingLineFeatureElements

          java.util.Collection<NFEFeatureElement> getRuleLeftHandMatchingLineFeatureElements()

      Gets all the line feature elements from the current intersection that matches the left hand side line operand of the current line-line rule
      Returns:
      a collection of line feature elements

    <!-- -->

    - #### getRuleRightHandMatchingLineFeatureElements

          java.util.Collection<NFEFeatureElement> getRuleRightHandMatchingLineFeatureElements()

      Gets all the line feature elements from the current intersection that matches the right hand side line operand of the current line-line rule
      Returns:
      a collection of line feature elements

    <!-- -->

    - #### getMatchingPointFeatureElements

          java.util.Collection<NFEFeatureElement> getMatchingPointFeatureElements()

      Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule
      Returns:
      a collection of point feature elements.

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

- [Prev Class](NFELineLineRuleHandler.md)
- [Next Class](NFELinePointRuleHandler.md)

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
