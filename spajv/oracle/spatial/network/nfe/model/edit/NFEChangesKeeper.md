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

- [Prev Class](NFEBasicModelManipulator.md)
- [Next Class](NFEConnectableEdge.md)

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

oracle.spatial.network.nfe.model.edit

## Class NFEChangesKeeper

- java.lang.Object

- - oracle.spatial.network.nfe.model.edit.NFEChangesKeeper

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEChangesKeeper
      extends java.lang.Object

  This class is meant to keep the references to the edited objects (network elements and features) in a project session, in order to keep the tracking of the changes performed and then save them into the DB when desired. The references kept belong to objects in the Model Manager (`NFEModelManager`), specifically to the `network` and `featureLayers` maps.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEChangesKeeper``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                   | Method and Description                                                                                                                                  |
    |-------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                           | `canSave``()`<br>Returns true if changes are register, false otherwise.                                                                                 |
    | `void`                                                                              | `clearChanges``()`<br>Clear changes.                                                                                                                    |
    | `void`                                                                              | `featureAdded``(`[`NFEFeature`](../feature/NFEFeature.md)` feature)`<br>Register the add feature change.                                                |
    | `void`                                                                              | `featureDeleted``(`[`NFEFeature`](../feature/NFEFeature.md)` feature)`<br>Register the delete feature change.                                           |
    | `void`                                                                              | `featureElementAdded``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featureElement)`<br>Register the add feature element change.            |
    | `void`                                                                              | `featureElementDeleted``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featureElement)`<br>Register the delete feature element change.       |
    | `void`                                                                              | `featureElementModified``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featureElement)`<br>Register the modify feature element change.      |
    | `void`                                                                              | `featureModified``(`[`NFEFeature`](../feature/NFEFeature.md)` feature)`<br>Register the modify feature change.                                          |
    | `java.util.List<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>`          | `getDeletedFeatureElements``()`<br>Returns the deleted feature elements.                                                                                |
    | `java.util.List<`[`NFEFeature`](../feature/NFEFeature.md)`>`                        | `getDeletedFeatures``()`<br>Returns the deleted features.                                                                                               |
    | `java.util.List<`[`NFELink`](../network/NFELink.md)`>`                              | `getDeletedLinks``()`<br>Returns the deleted links.                                                                                                     |
    | `java.util.List<`[`NFENode`](../network/NFENode.md)`>`                              | `getDeletedNodes``()`<br>Returns the deleted nodes.                                                                                                     |
    | `java.util.List<`[`NFERuleInstanceRelation`](../rule/NFERuleInstanceRelation.md)`>` | `getDeletedRuleInstanceRelations``()`<br>Returns the deleted rule instance relations.                                                                   |
    | `java.util.List<`[`NFERuleInstance`](../rule/NFERuleInstance.md)`>`                 | `getDeletedRuleInstances``()`<br>Returns the deleted rule instances.                                                                                    |
    | `java.util.List<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>`          | `getModifiedFeatureElements``()`<br>Returns the modified feature elements.                                                                              |
    | `java.util.List<`[`NFEFeature`](../feature/NFEFeature.md)`>`                        | `getModifiedFeatures``()`<br>Returns the modified features.                                                                                             |
    | `java.util.List<`[`NFELink`](../network/NFELink.md)`>`                              | `getModifiedLinks``()`<br>Returns the modified links.                                                                                                   |
    | `java.util.List<`[`NFENode`](../network/NFENode.md)`>`                              | `getModifiedNodes``()`<br>Returns the modified nodes.                                                                                                   |
    | `java.util.List<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>`          | `getNewFeatureElements``()`<br>Returns the new feature elements.                                                                                        |
    | `java.util.List<`[`NFEFeature`](../feature/NFEFeature.md)`>`                        | `getNewFeatures``()`<br>Returns the new features.                                                                                                       |
    | `java.util.List<`[`NFELink`](../network/NFELink.md)`>`                              | `getNewLinks``()`<br>Returns the new links.                                                                                                             |
    | `java.util.List<`[`NFENode`](../network/NFENode.md)`>`                              | `getNewNodes``()`<br>Returns the new nodes                                                                                                              |
    | `java.util.List<`[`NFERuleInstanceRelation`](../rule/NFERuleInstanceRelation.md)`>` | `getNewRuleInstanceRelations``()`<br>Returns the new rule instance relations.                                                                           |
    | `java.util.List<`[`NFERuleInstance`](../rule/NFERuleInstance.md)`>`                 | `getNewRuleInstances``()`<br>Returns the new rule instances.                                                                                            |
    | `void`                                                                              | `linkAdded``(`[`NFELink`](../network/NFELink.md)` link)`<br>Register the add link change.                                                               |
    | `void`                                                                              | `linkDeleted``(`[`NFELink`](../network/NFELink.md)` link)`<br>Register the delete link change.                                                          |
    | `void`                                                                              | `linkModified``(`[`NFELink`](../network/NFELink.md)` link)`<br>Register the modify link change.                                                         |
    | `void`                                                                              | `nodeAdded``(`[`NFENode`](../network/NFENode.md)` node)`<br>Register the add node change.                                                               |
    | `void`                                                                              | `nodeDeleted``(`[`NFENode`](../network/NFENode.md)` node)`<br>Register the delete node change.                                                          |
    | `void`                                                                              | `nodeModified``(`[`NFENode`](../network/NFENode.md)` node)`<br>Register the modify node change.                                                         |
    | `void`                                                                              | `ruleInstanceAdded``(`[`NFERuleInstance`](../rule/NFERuleInstance.md)` ri)`<br>Register the add rule instance change.                                   |
    | `void`                                                                              | `ruleInstanceRelAdded``(`[`NFERuleInstanceRelation`](../rule/NFERuleInstanceRelation.md)` rir)`<br>Register the add rule instance relation change.      |
    | `void`                                                                              | `ruleInstanceRelRemoved``(`[`NFERuleInstanceRelation`](../rule/NFERuleInstanceRelation.md)` rir)`<br>Register the remove rule instance relation change. |
    | `void`                                                                              | `ruleInstanceRemoved``(`[`NFERuleInstance`](../rule/NFERuleInstance.md)` ri)`<br>Register the remove rule instance change.                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEChangesKeeper

          public NFEChangesKeeper()

  <!-- -->

  - ### Method Detail

    - #### canSave

          public boolean canSave()

      Returns true if changes are register, false otherwise.
      Returns:
      true if changes are register, false otherwise

    <!-- -->

    - #### featureAdded

          public void featureAdded(NFEFeature feature)

      Register the add feature change.
      Parameters:
      `feature` - added feature

    <!-- -->

    - #### featureModified

          public void featureModified(NFEFeature feature)

      Register the modify feature change.
      Parameters:
      `feature` - modified feature

    <!-- -->

    - #### featureDeleted

          public void featureDeleted(NFEFeature feature)

      Register the delete feature change.
      Parameters:
      `feature` - deleted feature

    <!-- -->

    - #### featureElementAdded

          public void featureElementAdded(NFEFeatureElement featureElement)

      Register the add feature element change.
      Parameters:
      `featureElement` - added feature element

    <!-- -->

    - #### featureElementModified

          public void featureElementModified(NFEFeatureElement featureElement)

      Register the modify feature element change.
      Parameters:
      `featureElement` - modified feature element

    <!-- -->

    - #### featureElementDeleted

          public void featureElementDeleted(NFEFeatureElement featureElement)

      Register the delete feature element change.
      Parameters:
      `featureElement` - deleted feature element

    <!-- -->

    - #### nodeAdded

          public void nodeAdded(NFENode node)

      Register the add node change.
      Parameters:
      `node` - added node

    <!-- -->

    - #### nodeModified

          public void nodeModified(NFENode node)

      Register the modify node change.
      Parameters:
      `node` - modified node

    <!-- -->

    - #### nodeDeleted

          public void nodeDeleted(NFENode node)

      Register the delete node change.
      Parameters:
      `node` - deleted node

    <!-- -->

    - #### linkAdded

          public void linkAdded(NFELink link)

      Register the add link change.
      Parameters:
      `link` - added link

    <!-- -->

    - #### linkModified

          public void linkModified(NFELink link)

      Register the modify link change.
      Parameters:
      `link` - modified link

    <!-- -->

    - #### linkDeleted

          public void linkDeleted(NFELink link)

      Register the delete link change.
      Parameters:
      `link` - deleted link

    <!-- -->

    - #### ruleInstanceAdded

          public void ruleInstanceAdded(NFERuleInstance ri)

      Register the add rule instance change.
      Parameters:
      `ri` - added rule instance

    <!-- -->

    - #### ruleInstanceRemoved

          public void ruleInstanceRemoved(NFERuleInstance ri)

      Register the remove rule instance change.
      Parameters:
      `ri` - removed rule instance

    <!-- -->

    - #### ruleInstanceRelAdded

          public void ruleInstanceRelAdded(NFERuleInstanceRelation rir)

      Register the add rule instance relation change.
      Parameters:
      `rir` - added rule instance relation

    <!-- -->

    - #### ruleInstanceRelRemoved

          public void ruleInstanceRelRemoved(NFERuleInstanceRelation rir)

      Register the remove rule instance relation change.
      Parameters:
      `rir` - removed rule instance relation

    <!-- -->

    - #### getNewFeatures

          public java.util.List<NFEFeature> getNewFeatures()

      Returns the new features.
      Returns:
      new features

    <!-- -->

    - #### getModifiedFeatures

          public java.util.List<NFEFeature> getModifiedFeatures()

      Returns the modified features.
      Returns:
      modified features

    <!-- -->

    - #### getDeletedFeatures

          public java.util.List<NFEFeature> getDeletedFeatures()

      Returns the deleted features.
      Returns:
      deleted features

    <!-- -->

    - #### getNewFeatureElements

          public java.util.List<NFEFeatureElement> getNewFeatureElements()

      Returns the new feature elements.
      Returns:
      new feature elements

    <!-- -->

    - #### getModifiedFeatureElements

          public java.util.List<NFEFeatureElement> getModifiedFeatureElements()

      Returns the modified feature elements.
      Returns:
      modified feature elements

    <!-- -->

    - #### getDeletedFeatureElements

          public java.util.List<NFEFeatureElement> getDeletedFeatureElements()

      Returns the deleted feature elements.
      Returns:
      deleted feature elements

    <!-- -->

    - #### getNewNodes

          public java.util.List<NFENode> getNewNodes()

      Returns the new nodes
      Returns:
      new nodes

    <!-- -->

    - #### getModifiedNodes

          public java.util.List<NFENode> getModifiedNodes()

      Returns the modified nodes.
      Returns:
      modified nodes

    <!-- -->

    - #### getDeletedNodes

          public java.util.List<NFENode> getDeletedNodes()

      Returns the deleted nodes.
      Returns:
      deleted nodes

    <!-- -->

    - #### getNewLinks

          public java.util.List<NFELink> getNewLinks()

      Returns the new links.
      Returns:
      new links

    <!-- -->

    - #### getModifiedLinks

          public java.util.List<NFELink> getModifiedLinks()

      Returns the modified links.
      Returns:
      modified links

    <!-- -->

    - #### getDeletedLinks

          public java.util.List<NFELink> getDeletedLinks()

      Returns the deleted links.
      Returns:
      deleted links

    <!-- -->

    - #### getNewRuleInstances

          public java.util.List<NFERuleInstance> getNewRuleInstances()

      Returns the new rule instances.
      Returns:
      new rule instances

    <!-- -->

    - #### getDeletedRuleInstances

          public java.util.List<NFERuleInstance> getDeletedRuleInstances()

      Returns the deleted rule instances.
      Returns:
      deleted rule instances

    <!-- -->

    - #### getNewRuleInstanceRelations

          public java.util.List<NFERuleInstanceRelation> getNewRuleInstanceRelations()

      Returns the new rule instance relations.
      Returns:
      new rule instance relations

    <!-- -->

    - #### getDeletedRuleInstanceRelations

          public java.util.List<NFERuleInstanceRelation> getDeletedRuleInstanceRelations()

      Returns the deleted rule instance relations.
      Returns:
      deleted rule instance relations

    <!-- -->

    - #### clearChanges

          public void clearChanges()

      Clear changes.

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

- [Prev Class](NFEBasicModelManipulator.md)
- [Next Class](NFEConnectableEdge.md)

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
