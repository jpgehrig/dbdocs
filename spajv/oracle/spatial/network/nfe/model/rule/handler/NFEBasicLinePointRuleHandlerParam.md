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

- [Prev Class](NFEBasicLinePointRuleHandler.md)
- [Next Class](NFELineLineRuleHandler.md)

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

## Class NFEBasicLinePointRuleHandlerParam

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.handler.NFEBasicLinePointRuleHandlerParam

<!-- -->

- All Implemented Interfaces:
  [NFELinePointRuleHandlerParam](NFELinePointRuleHandlerParam.md)

  ------------------------------------------------------------------------



      public class NFEBasicLinePointRuleHandlerParam
      extends java.lang.Object
      implements NFELinePointRuleHandlerParam

  The default implementation of [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                         |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEBasicLinePointRuleHandlerParam``(`[`Intersection`](../../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`> intersection, `[`NFELinePointRule`](../NFELinePointRule.md)` lpRule, java.util.Collection<java.lang.Long> matchingLineIds, java.util.Collection<java.lang.Long> matchingPointIds)`  |
    | `NFEBasicLinePointRuleHandlerParam``(`[`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)` llhParam, boolean leftHand, java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`> defaultCreatedPointFeatElems)`                                                                                                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                      | Method and Description                                                                                                                                                       |
    |----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Intersection`](../../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`             | `getIntersection``()`<br>Gets the intersection that is currently being processed.                                                                                            |
    | [`IntersectionMember`](../../spatial/interaction/IntersectionMember.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>` | `getIntersectionMember``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem)`<br>Gets the intersection member representation of the given feature element. |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getMatchingLineFeatureElements``()`<br>Gets all the line feature elements from the current intersection that matches the line operand of the current line-point rule        |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getMatchingPointFeatureElements``()`<br>Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule     |
    | [`NFELinePointRule`](../NFELinePointRule.md)                                                                                           | `getRule``()`<br>The line-point rule that has been triggered                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicLinePointRuleHandlerParam

          public NFEBasicLinePointRuleHandlerParam(Intersection<NFEFeatureElement> intersection,
                                                   NFELinePointRule lpRule,
                                                   java.util.Collection<java.lang.Long> matchingLineIds,
                                                   java.util.Collection<java.lang.Long> matchingPointIds)

    <!-- -->

    - #### NFEBasicLinePointRuleHandlerParam

          public NFEBasicLinePointRuleHandlerParam(NFELineLineRuleHandlerParam llhParam,
                                                   boolean leftHand,
                                                   java.util.Collection<NFEFeatureElement> defaultCreatedPointFeatElems)

  <!-- -->

  - ### Method Detail

    - #### getRule

          public NFELinePointRule getRule()

      Description copied from interface: [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)
      The line-point rule that has been triggered
      Specified by:
      [`getRule`](NFELinePointRuleHandlerParam.md) in interface [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)

      Returns:
      a line-point rule

    <!-- -->

    - #### getIntersection

          public Intersection<NFEFeatureElement> getIntersection()

      Description copied from interface: [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)
      Gets the intersection that is currently being processed. It contains all the intersecting feature elements.
      Specified by:
      [`getIntersection`](NFELinePointRuleHandlerParam.md) in interface [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)

      Returns:
      an intersection object

    <!-- -->

    - #### getIntersectionMember

          public IntersectionMember<NFEFeatureElement> getIntersectionMember(NFEFeatureElement featElem)

      Description copied from interface: [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)
      Gets the intersection member representation of the given feature element. The intersection member object describes how the feature element is intersected in the current intersection.
      Specified by:
      [`getIntersectionMember`](NFELinePointRuleHandlerParam.md) in interface [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)

      Parameters:
      `featElem` - a feature element

      Returns:
      the feature element as an intersection member or null if the feature element does not participates in the current intersection

    <!-- -->

    - #### getMatchingLineFeatureElements

          public java.util.Collection<NFEFeatureElement> getMatchingLineFeatureElements()

      Description copied from interface: [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)
      Gets all the line feature elements from the current intersection that matches the line operand of the current line-point rule
      Specified by:
      [`getMatchingLineFeatureElements`](NFELinePointRuleHandlerParam.md) in interface [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)

      Returns:
      a collection of line feature elements

    <!-- -->

    - #### getMatchingPointFeatureElements

          public java.util.Collection<NFEFeatureElement> getMatchingPointFeatureElements()

      Description copied from interface: [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)
      Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule
      Specified by:
      [`getMatchingPointFeatureElements`](NFELinePointRuleHandlerParam.md) in interface [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)

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

- [Prev Class](NFEBasicLinePointRuleHandler.md)
- [Next Class](NFELineLineRuleHandler.md)

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
