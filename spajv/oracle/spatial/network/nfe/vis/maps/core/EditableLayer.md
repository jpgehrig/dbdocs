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

- [Prev Class](Drawable.md)
- [Next Class](EditChangeListener.md)

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

oracle.spatial.network.nfe.vis.maps.core

## Interface EditableLayer

- All Superinterfaces:
  [GeoObjectLayer](GeoObjectLayer.md), [Layer](Layer.md)

  <!-- -->

  All Known Implementing Classes:
  [AbstractDataSetLayer](../layer/AbstractDataSetLayer.md)

  ------------------------------------------------------------------------



      public interface EditableLayer
      extends GeoObjectLayer

  A layer which support editing actions on its content

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `PROPERTY_EDITABLE`   |

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`PROPERTY_NAME`](Layer.md)`, `[`PROPERTY_PROVIDERID`](Layer.md)`, `[`PROPERTY_SRID`](Layer.md)`, `[`PROPERTY_VISIBLE`](Layer.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                                                                                          |
    |-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                      | `addEditChangeListener``(`[`EditChangeListener`](EditChangeListener.md)` l)`<br>Adds a change listener to listen for editing changes            |
    | `boolean`                   | `appendToObject``(java.lang.Object key, java.lang.Object spatialObject)`<br>Appends the provided spatialObject to an existing feature           |
    | `void`                      | `clearChanges``()`                                                                                                                              |
    | [`GeoObject`](GeoObject.md) | `deleteObject``(java.lang.Object key)`<br>Deletes an existing GeoObject instance.                                                               |
    | `boolean`                   | `insertObject``(java.lang.Object key, `[`GeoObject`](GeoObject.md)` obj)`<br>Inserts a new GeoObject instance                                   |
    | `boolean`                   | `isEditable``()`                                                                                                                                |
    | `boolean`                   | `isModified``()`                                                                                                                                |
    | [`GeoObject`](GeoObject.md) | `newObject``(java.lang.Object spatialObject, java.lang.Object[] params)`<br>Creates a new GeoObject with the provided parameters                |
    | `void`                      | `removeEditChangeListener``(`[`EditChangeListener`](EditChangeListener.md)` l)`                                                                 |
    | `boolean`                   | `save``()`                                                                                                                                      |
    | `void`                      | `setEditable``(boolean editable)`                                                                                                               |
    | [`GeoObject`](GeoObject.md) | `updateObject``(java.lang.Object key, `[`GeoObject`](GeoObject.md)` changedObject)`<br>Updates an existing GeoObject with the specified change. |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObjectLayer](GeoObjectLayer.md)

      [`getObject`](GeoObjectLayer.md)`, `[`getObjects`](GeoObjectLayer.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`added`](Layer.md)`, `[`clear`](Layer.md)`, `[`fromXMLElement`](Layer.md)`, `[`getCanvas`](Layer.md)`, `[`getDataMBR`](Layer.md)`, `[`getFullExtent`](Layer.md)`, `[`getIcon`](Layer.md)`, `[`getName`](Layer.md)`, `[`getProviderID`](Layer.md)`, `[`getSRID`](Layer.md)`, `[`handleEvent`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`isVisible`](Layer.md)`, `[`mapRegionChanged`](Layer.md)`, `[`removed`](Layer.md)`, `[`render`](Layer.md)`, `[`repaint`](Layer.md)`, `[`setCanvas`](Layer.md)`, `[`setName`](Layer.md)`, `[`setProviderID`](Layer.md)`, `[`setSRID`](Layer.md)`, `[`setVisible`](Layer.md)`, `[`toXMLElement`](Layer.md)`, `[`update`](Layer.md)

<!-- -->

- - ### Field Detail

    - #### PROPERTY_EDITABLE

          static final java.lang.String PROPERTY_EDITABLE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### updateObject

          GeoObject updateObject(java.lang.Object key,
                                 GeoObject changedObject)

      Updates an existing GeoObject with the specified change.
      Parameters:
      `changedObject` - the object containing changes

      Returns:
      the old object

    <!-- -->

    - #### deleteObject

          GeoObject deleteObject(java.lang.Object key)

      Deletes an existing GeoObject instance.
      Parameters:
      `key` - the object to be deleted

      Returns:
      the deleted object

    <!-- -->

    - #### insertObject

          boolean insertObject(java.lang.Object key,
                               GeoObject obj)
                        throws java.lang.Exception

      Inserts a new GeoObject instance
      Parameters:
      `obj` - the new object to be added to this layer.

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### newObject

          GeoObject newObject(java.lang.Object spatialObject,
                              java.lang.Object[] params)
                       throws java.lang.Exception

      Creates a new GeoObject with the provided parameters
      Parameters:
      `spatialObject` -

      `params` -

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### appendToObject

          boolean appendToObject(java.lang.Object key,
                                 java.lang.Object spatialObject)
                          throws java.lang.Exception

      Appends the provided spatialObject to an existing feature
      Parameters:
      `key` -

      `spatialObject` -

      Returns:
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### setEditable

          void setEditable(boolean editable)

    <!-- -->

    - #### isEditable

          boolean isEditable()

    <!-- -->

    - #### isModified

          boolean isModified()

    <!-- -->

    - #### save

          boolean save()

    <!-- -->

    - #### clearChanges

          void clearChanges()

    <!-- -->

    - #### addEditChangeListener

          void addEditChangeListener(EditChangeListener l)

      Adds a change listener to listen for editing changes
      Parameters:
      `l` -

    <!-- -->

    - #### removeEditChangeListener

          void removeEditChangeListener(EditChangeListener l)

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

- [Prev Class](Drawable.md)
- [Next Class](EditChangeListener.md)

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
