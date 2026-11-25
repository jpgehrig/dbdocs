------------------------------------------------------------------------

#### new EditChangeManager()

This class represents an edit change manager typically associated with a layer being edited.

The argument options is a properties bag that supplies various attributes for the new edit
change manager, including the layer this manager should be associated with.

### Methods

------------------------------------------------------------------------

#### addFeature(key, feature)

Registers the addition of a new feature.

##### Parameters:

| Name      | Type | Description      |
|-----------|------|------------------|
| `key`     |      | feture key value |
| `feature` |      | feature object   |

##### Returns:

an edit change event object (EditChangeEvent)

Type
Object

------------------------------------------------------------------------

#### clearChanges()

Clear all changes.

------------------------------------------------------------------------

#### getChangedAttributesOfModifiedFeature(key)

Returns the attribute names of modified features that have the
values changed.
For new and removed features this method returns null.

##### Parameters:

| Name  | Type | Description |
|-------|------|-------------|
| `key` |      |             |

##### Returns:

attribute names

------------------------------------------------------------------------

#### getModifiedFeatures()

Returns the modified features.

##### Returns:

a list with modified features

Type
Object

------------------------------------------------------------------------

#### getNewFeatures()

Returns the new features.

##### Returns:

a list with new features

Type
Object

------------------------------------------------------------------------

#### getRemovedFeatures()

Returns the removed features keys

##### Returns:

a list with removed feature

Type
Object

------------------------------------------------------------------------

#### hasChanges()

Returns if there are any change.

##### Returns:

true or false

------------------------------------------------------------------------

#### hasSpatialAttributeChanged(key)

Returns if spatial attribute of modified feature has changed.
For new and removed features this method returns false.

##### Parameters:

| Name  | Type | Description |
|-------|------|-------------|
| `key` |      |             |

##### Returns:

true or false

------------------------------------------------------------------------

#### isModifiedFeature()

Returns if input id is a modified feature.

------------------------------------------------------------------------

#### isNewFeature()

Returns if input id is a new feature.

------------------------------------------------------------------------

#### isRemovedFeature()

Returns if input id is a removed feature.

------------------------------------------------------------------------

#### redo()

Redo the change event

------------------------------------------------------------------------

#### removeFeature(key)

Registers that feature is removed.

##### Parameters:

| Name  | Type | Description |
|-------|------|-------------|
| `key` |      | feature key |

##### Returns:

an edit change event object (EditChangeEvent)

Type
Object

------------------------------------------------------------------------

#### undo()

Undo the change event

------------------------------------------------------------------------

#### updateFeature(key, changeObject, updateType)

Registers an update in the feature. The update may be a change
on the spatial attribute, a change on a single non-spatial
attribute, or a change in multiple non-spatial attributes.

Spatial change: object type is of one spatial class (JGeometry, AnnotationText, ...).
Attribute change: object type is of Field class.
Multi attribute change: object type is of Field\[\] elements.

##### Parameters:

| Name           | Type | Description                                    |
|----------------|------|------------------------------------------------|
| `key`          |      | feature key value                              |
| `changeObject` |      | change object (geometry or list of attributes) |
| `updateType`   |      | defines the type of update change              |

##### Returns:

an edit change event object (EditChangeEvent)

Type
Object
