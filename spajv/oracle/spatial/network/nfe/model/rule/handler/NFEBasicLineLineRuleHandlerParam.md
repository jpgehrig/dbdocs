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

- [Prev Class](NFEBasicLineLineRuleHandler.md)
- [Next Class](NFEBasicLinePointRuleHandler.md)

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

## Class NFEBasicLineLineRuleHandlerParam

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.handler.NFEBasicLineLineRuleHandlerParam

<!-- -->

- All Implemented Interfaces:
  [NFELineLineRuleHandlerParam](NFELineLineRuleHandlerParam.md)

  ------------------------------------------------------------------------



      public class NFEBasicLineLineRuleHandlerParam
      extends java.lang.Object
      implements NFELineLineRuleHandlerParam

  The default implementation of [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEBasicLineLineRuleHandlerParam``(`[`Intersection`](../../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`> intersection, `[`NFELineLineRule`](../NFELineLineRule.md)` llRule, java.util.Collection<java.lang.Long> matchingLHLineIds, java.util.Collection<java.lang.Long> matchingRHLineIds, java.util.Collection<java.lang.Long> matchingPointIds)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                      | Method and Description                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Intersection`](../../spatial/interaction/Intersection.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`             | `getIntersection``()`<br>Gets the intersection that is currently being processed.                                                                                                                 |
    | [`IntersectionMember`](../../spatial/interaction/IntersectionMember.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>` | `getIntersectionMember``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem)`<br>Gets the feature element as an intersection member of the current intersection.                |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getMatchingPointFeatureElements``()`<br>Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule                          |
    | [`NFELineLineRule`](../NFELineLineRule.md)                                                                                             | `getRule``()`<br>The line-point rule that has been triggered                                                                                                                                      |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getRuleLeftHandMatchingLineFeatureElements``()`<br>Gets all the line feature elements from the current intersection that matches the left hand side line operand of the current line-line rule   |
    | `java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                    | `getRuleRightHandMatchingLineFeatureElements``()`<br>Gets all the line feature elements from the current intersection that matches the right hand side line operand of the current line-line rule |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicLineLineRuleHandlerParam

          public NFEBasicLineLineRuleHandlerParam(Intersection<NFEFeatureElement> intersection,
                                                  NFELineLineRule llRule,
                                                  java.util.Collection<java.lang.Long> matchingLHLineIds,
                                                  java.util.Collection<java.lang.Long> matchingRHLineIds,
                                                  java.util.Collection<java.lang.Long> matchingPointIds)

  <!-- -->

  - ### Method Detail

    - #### getRule

          public NFELineLineRule getRule()

      Description copied from interface: [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)
      The line-point rule that has been triggered
      Specified by:
      [`getRule`](NFELineLineRuleHandlerParam.md) in interface [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)

      Returns:
      a line-point rule

    <!-- -->

    - #### getIntersection

          public Intersection<NFEFeatureElement> getIntersection()

      Description copied from interface: [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)
      Gets the intersection that is currently being processed. It contains all the intersecting feature elements.
      Specified by:
      [`getIntersection`](NFELineLineRuleHandlerParam.md) in interface [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)

      Returns:
      an intersection object

    <!-- -->

    - #### getIntersectionMember

          public IntersectionMember<NFEFeatureElement> getIntersectionMember(NFEFeatureElement featElem)

      Description copied from interface: [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)
      Gets the feature element as an intersection member of the current intersection. The intersection member object describes how the feature element is intersected in the current intersection group.
      Specified by:
      [`getIntersectionMember`](NFELineLineRuleHandlerParam.md) in interface [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)

      Parameters:
      `featElem` - a feature element

      Returns:
      the feature element as an intersection member or null if the feature element does not participates in the current intersection

    <!-- -->

    - #### getRuleLeftHandMatchingLineFeatureElements

          public java.util.Collection<NFEFeatureElement> getRuleLeftHandMatchingLineFeatureElements()

      Description copied from interface: [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)
      Gets all the line feature elements from the current intersection that matches the left hand side line operand of the current line-line rule
      Specified by:
      [`getRuleLeftHandMatchingLineFeatureElements`](NFELineLineRuleHandlerParam.md) in interface [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)

      Returns:
      a collection of line feature elements

    <!-- -->

    - #### getRuleRightHandMatchingLineFeatureElements

          public java.util.Collection<NFEFeatureElement> getRuleRightHandMatchingLineFeatureElements()

      Description copied from interface: [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)
      Gets all the line feature elements from the current intersection that matches the right hand side line operand of the current line-line rule
      Specified by:
      [`getRuleRightHandMatchingLineFeatureElements`](NFELineLineRuleHandlerParam.md) in interface [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)

      Returns:
      a collection of line feature elements

    <!-- -->

    - #### getMatchingPointFeatureElements

          public java.util.Collection<NFEFeatureElement> getMatchingPointFeatureElements()

      Description copied from interface: [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)
      Gets all the point feature elements from the current intersection that matches the point operand of the current line-point rule
      Specified by:
      [`getMatchingPointFeatureElements`](NFELineLineRuleHandlerParam.md) in interface [`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)

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

- [Prev Class](NFEBasicLineLineRuleHandler.md)
- [Next Class](NFEBasicLinePointRuleHandler.md)

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
