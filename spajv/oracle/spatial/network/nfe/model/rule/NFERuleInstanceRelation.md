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

- [Prev Class](NFERuleInstance.md)
- [Next Class](NFERulesEngine.md)

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

## Class NFERuleInstanceRelation

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - oracle.spatial.network.nfe.model.rule.NFERuleInstanceRelation

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  ------------------------------------------------------------------------



      public class NFERuleInstanceRelation
      extends NFEBasicModelObject

  Represents a relationship between a rule instance and a feature element to which the rule instance's rule was applied.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFERuleInstanceRelation``(`[`NFERuleInstance`](NFERuleInstance.md)` ruleInstance, `[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Allocates a new rule instance relation |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                  |
    |--------------------------------------------------------|-----------------------------------------------------------------------------------------|
    | `boolean`                                              | `equals``(java.lang.Object obj)`                                                        |
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md) | `getFeatureElement``()`<br>Gets the related feature element                             |
    | `java.lang.String`                                     | `getKey``()`<br>Gets the relation's key which is used to uniquely identify the relation |
    | [`NFERuleInstance`](NFERuleInstance.md)                | `getRuleInstance``()`<br>Gets the rule instance object                                  |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFERuleInstanceRelation

          public NFERuleInstanceRelation(NFERuleInstance ruleInstance,
                                         NFEFeatureElement featElem)

      Allocates a new rule instance relation
      Parameters:
      `ruleInstance` - a rule instance object

      `featElem` - a feature element

  <!-- -->

  - ### Method Detail

    - #### getRuleInstance

          public NFERuleInstance getRuleInstance()

      Gets the rule instance object
      Returns:
      a rule instance object

    <!-- -->

    - #### getFeatureElement

          public NFEFeatureElement getFeatureElement()

      Gets the related feature element
      Returns:
      a feature element

    <!-- -->

    - #### getKey

          public java.lang.String getKey()

      Gets the relation's key which is used to uniquely identify the relation
      Returns:

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

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

- [Prev Class](NFERuleInstance.md)
- [Next Class](NFERulesEngine.md)

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
