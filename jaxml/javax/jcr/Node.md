Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NamespaceRegistry.md)**
- **[Next Class](NodeIterator.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.jcr**

## **Interface Node**

- **All Superinterfaces:**
  **[Item](Item.md)**

  <!-- -->

  **All Known Subinterfaces:**
  **[Version](version/Version.md), [VersionHistory](version/VersionHistory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Node
      extends Item

  **The `Node` interface represents a node in the hierarchy that makes up the repository.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                                                                       |
    |------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                         | `addMixin``(java.lang.String mixinName)`<br>Adds the specified mixin node type to this node.                                                                                                                                                                                 |
    | `Node`                                         | `addNode``(java.lang.String relPath)`<br>Creates a new node at `relPath`.                                                                                                                                                                                                    |
    | `Node`                                         | `addNode``(java.lang.String relPath, java.lang.String primaryNodeTypeName)`<br>Creates a new node at `relPath` of the specified node type.                                                                                                                                   |
    | `boolean`                                      | `canAddMixin``(java.lang.String mixinName)`<br>Returns `true` if the specified mixin node type, `mixinName`, can be added to this node.                                                                                                                                      |
    | `void`                                         | `cancelMerge``(`[`Version`](version/Version.md)` version)`<br>Cancels the merge process with respect to this node and specified `version`.                                                                                                                                   |
    | [`Version`](version/Version.md)                | `checkin``()`<br>Creates a new version with a system generated version name and returns that version (which will be the new base version of this node).                                                                                                                      |
    | `void`                                         | `checkout``()`<br>Sets this versionable node to checked-out status by setting its `jcr:isCheckedOut` property to true and adds to the `jcr:predecessors` (multi-value) property a reference to the current base version (the same value as held in `jcr:baseVersion`).       |
    | `void`                                         | `doneMerge``(`[`Version`](version/Version.md)` version)`<br>Completes the merge process with respect to this node and the specified `version`.                                                                                                                               |
    | [`Version`](version/Version.md)                | `getBaseVersion``()`<br>Returns the current base version of this versionable node.                                                                                                                                                                                           |
    | `java.lang.String`                             | `getCorrespondingNodePath``(java.lang.String workspaceName)`<br>Returns the absolute path of the node in the specified workspace that corresponds to `this` node.                                                                                                            |
    | [`NodeDefinition`](nodetype/NodeDefinition.md) | `getDefinition``()`<br>Returns the node definition that applies to this node.                                                                                                                                                                                                |
    | `int`                                          | `getIndex``()`<br>This method returns the index of this node within the ordered set of its same-name sibling nodes.                                                                                                                                                          |
    | [`Lock`](lock/Lock.md)                         | `getLock``()`<br>Returns the `Lock` object that applies to this node.                                                                                                                                                                                                        |
    | [`NodeType`](nodetype/NodeType.md)`[]`         | `getMixinNodeTypes``()`<br>Returns an array of NodeType objects representing the mixin node types assigned to this node.                                                                                                                                                     |
    | `Node`                                         | `getNode``(java.lang.String relPath)`<br>Returns the node at `relPath` relative to this node.                                                                                                                                                                                |
    | [`NodeIterator`](NodeIterator.md)              | `getNodes``()`<br>Returns a `NodeIterator` over all child `Node`s of this `Node`.                                                                                                                                                                                            |
    | [`NodeIterator`](NodeIterator.md)              | `getNodes``(java.lang.String namePattern)`<br>Gets all child nodes of this node that match `namePattern`.                                                                                                                                                                    |
    | [`Item`](Item.md)                              | `getPrimaryItem``()`<br>Returns the primary child item of this node.                                                                                                                                                                                                         |
    | [`NodeType`](nodetype/NodeType.md)             | `getPrimaryNodeType``()`<br>Returns the primary node type of this node.                                                                                                                                                                                                      |
    | [`PropertyIterator`](PropertyIterator.md)      | `getProperties``()`<br>Returns all properties of this node.                                                                                                                                                                                                                  |
    | [`PropertyIterator`](PropertyIterator.md)      | `getProperties``(java.lang.String namePattern)`<br>Gets all properties of this node that match `namePattern`.                                                                                                                                                                |
    | [`Property`](Property.md)                      | `getProperty``(java.lang.String relPath)`<br>Returns the property at `relPath` relative to `this` node.                                                                                                                                                                      |
    | [`PropertyIterator`](PropertyIterator.md)      | `getReferences``()`<br>Returns all `REFERENCE` properties that refer to this node.                                                                                                                                                                                           |
    | `java.lang.String`                             | `getUUID``()`<br>Returns the UUID of this node as recorded in this node's `jcr:uuid` property.                                                                                                                                                                               |
    | [`VersionHistory`](version/VersionHistory.md)  | `getVersionHistory``()`<br>Returns the `VersionHistory` object of this node.                                                                                                                                                                                                 |
    | `boolean`                                      | `hasNode``(java.lang.String relPath)`<br>Indicates whether a node exists at `relPath` Returns `true` if a node exists at `relPath` and `false` otherwise.                                                                                                                    |
    | `boolean`                                      | `hasNodes``()`<br>Indicates whether this node has child nodes.                                                                                                                                                                                                               |
    | `boolean`                                      | `hasProperties``()`<br>Indicates whether this node has properties.                                                                                                                                                                                                           |
    | `boolean`                                      | `hasProperty``(java.lang.String relPath)`<br>Indicates whether a property exists at `relPath` Returns `true` if a property exists at `relPath` and `false` otherwise.                                                                                                        |
    | `boolean`                                      | `holdsLock``()`<br>Returns `true` if this node holds a lock; otherwise returns `false`.                                                                                                                                                                                      |
    | `boolean`                                      | `isCheckedOut``()`<br>Returns true if this node is either \<li/\>versionable and currently checked-out, \<li/\>non-versionable and its nearest versionable ancestor is checked-out or \<li/\>non-versionable and it has no versionable ancestor.                             |
    | `boolean`                                      | `isLocked``()`<br>Returns `true` if this node is locked either as a result of a lock held by this node or by a deep lock on a node above this node; otherwise returns `false`.                                                                                               |
    | `boolean`                                      | `isNodeType``(java.lang.String nodeTypeName)`<br>Indicates whether this node is of the specified node type.                                                                                                                                                                  |
    | [`Lock`](lock/Lock.md)                         | `lock``(boolean isDeep, boolean isSessionScoped)`<br>Places a lock on this node.                                                                                                                                                                                             |
    | [`NodeIterator`](NodeIterator.md)              | `merge``(java.lang.String srcWorkspace, boolean bestEffort)`<br>This method can be thought of as a version-sensitive update (see 7.1.7 Updating and Cloning Nodes across Workspaces in the specification).                                                                   |
    | `void`                                         | `orderBefore``(java.lang.String srcChildRelPath, java.lang.String destChildRelPath)`<br>If this node supports child node ordering, this method inserts the child node at `srcChildRelPath` before its sibling, the child node at `destChildRelPath`, in the child node list. |
    | `void`                                         | `removeMixin``(java.lang.String mixinName)`<br>Removes the specified mixin node type from this node.                                                                                                                                                                         |
    | `void`                                         | `restore``(java.lang.String versionName, boolean removeExisting)`<br>Restores `this` node to the state defined by the version with the specified `versionName`.                                                                                                              |
    | `void`                                         | `restore``(`[`Version`](version/Version.md)` version, boolean removeExisting)`<br>Restores `this` node to the state defined by the specified `version`.                                                                                                                      |
    | `void`                                         | `restore``(`[`Version`](version/Version.md)` version, java.lang.String relPath, boolean removeExisting)`<br>Restores the specified version to `relPath`, relative to this node.                                                                                              |
    | `void`                                         | `restoreByLabel``(java.lang.String versionLabel, boolean removeExisting)`<br>Restores the version of this node with the specified version label.                                                                                                                             |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, boolean value)`<br>Sets the specified property to the specified value.                                                                                                                                                                 |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, java.util.Calendar value)`<br>Sets the specified property to the specified value.                                                                                                                                                      |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, double value)`<br>Sets the specified property to the specified value.                                                                                                                                                                  |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, java.io.InputStream value)`<br>Sets the specified property to the specified value.                                                                                                                                                     |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, long value)`<br>Sets the specified property to the specified value.                                                                                                                                                                    |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, Node value)`<br>Sets the specified (`REFERENCE`)property to refer to the specified `Node`.                                                                                                                                             |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, java.lang.String value)`<br>Sets the specified property to the specified value.                                                                                                                                                        |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, java.lang.String[] values)`<br>Sets the specified property to the specified array of values.                                                                                                                                           |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, java.lang.String[] values, int type)`<br>Sets the specified property to the specified array of values and to the specified type.                                                                                                       |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, java.lang.String value, int type)`<br>Sets the specified (single-value) property to the specified value.                                                                                                                               |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, `[`Value`](Value.md)` value)`<br>Sets the specified (single-value) property of this node to the specified `value`.                                                                                                                     |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, `[`Value`](Value.md)`[] values)`<br>Sets the specified (multi-value) property to the specified array of values.                                                                                                                        |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, `[`Value`](Value.md)`[] values, int type)`<br>Sets the specified (multi-value) property to the specified array of values.                                                                                                              |
    | [`Property`](Property.md)                      | `setProperty``(java.lang.String name, `[`Value`](Value.md)` value, int type)`<br>Sets the specified (single-value) property to the specified value.                                                                                                                          |
    | `void`                                         | `unlock``()`<br>Removes the lock on this node.                                                                                                                                                                                                                               |
    | `void`                                         | `update``(java.lang.String srcWorkspaceName)`<br>If this node does have a corresponding node in the workspace `srcWorkspaceName`, then this replaces this node and its subtree with a clone of the corresponding node and its subtree.                                       |

    - ### Methods inherited from interface javax.jcr.[Item](Item.md)

      [`accept`](Item.md)`, `[`getAncestor`](Item.md)`, `[`getDepth`](Item.md)`, `[`getName`](Item.md)`, `[`getParent`](Item.md)`, `[`getPath`](Item.md)`, `[`getSession`](Item.md)`, `[`isModified`](Item.md)`, `[`isNew`](Item.md)`, `[`isNode`](Item.md)`, `[`isSame`](Item.md)`, `[`refresh`](Item.md)`, `[`remove`](Item.md)`, `[`save`](Item.md)

<!-- -->

- - ### Method Detail

    - #### addNode

          Node addNode(java.lang.String relPath)
                throws ItemExistsException,
                       PathNotFoundException,
                       VersionException,
                       ConstraintViolationException,
                       LockException,
                       RepositoryException

      Creates a new node at `relPath`. The new node will only be persisted on `save()` if it meets the constraint criteria of the parent node's node type.
      In order to save a newly added node, `save` must be called either on the `Session`, or on the new node's parent or higher-order ancestor (grandparent, etc.). An attempt to call `save` *only* on the newly added node will throw a `RepositoryException`.

      In the context of this method the `relPath` provided must not have an index on its final element. If it does then a `RepositoryException` is thrown.

      Strictly speaking, the parameter is actually a relative path to the parent node of the node to be added, appended with the name desired for the new node (if the a node is being added directly below `this` node then only the name need be specified). It does not specify a position within the child node ordering. If ordering is supported by the node type of the parent node then the new node is appended to the end of the child node list.

      Since this signature does not allow explicit node type assignment, the new node's primary node type will be determined (either immediately or on `save`, depending on the implementation) by the child node definitions in the node types of its parent.

      An `ItemExistsException` will be thrown either immediately (by this method), or on `save`, if an item at the specified path already exists and same-name siblings are not allowed. Implementations may differ on when this validation is performed.

      A `PathNotFoundException` will be thrown either immediately, or on `save`, if the specified path implies intermediary nodes that do not exist. Implementations may differ on when this validation is performed.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if adding the node would violate a node type or implementation-specific constraint or if an attempt is made to add a node as the child of a property. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save`, if the node to which the new child is being added is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately (by this method), or on `save`, if a lock prevents the addition of the node. Implementations may differ on when this validation is performed.

      Parameters:
      `relPath` - The path of the new node to be created.

      Returns:
      The node that was added.

      Throws:
      [`ItemExistsException`](ItemExistsException.md) - if an item at the specified path already exists, same-name siblings are not allowed and this implementation performs this validation immediately instead of waiting until `save`.

      [`PathNotFoundException`](PathNotFoundException.md) - if the specified path implies intermediary `Node`s that do not exist or the last element of `relPath` has an index, and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if a node type or implementation-specific constraint is violated or if an attempt is made to add a node as the child of a property and this implementation performs this validation immediately instead of waiting until `save`.

      [`VersionException`](version/VersionException.md) - if the node to which the new child is being added is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the addition of the node and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If the last element of `relPath` has an index or if another error occurs.

    <!-- -->

    - #### addNode

          Node addNode(java.lang.String relPath,
                       java.lang.String primaryNodeTypeName)
                throws ItemExistsException,
                       PathNotFoundException,
                       NoSuchNodeTypeException,
                       LockException,
                       VersionException,
                       ConstraintViolationException,
                       RepositoryException

      Creates a new node at `relPath` of the specified node type. The same as `addNode(String relPath)` except that the primary node type of the new node is explictly specified.
      An `ItemExistsException` will be thrown either immediately (by this method), or on `save`, if an item at the specified path already exists and same-name siblings are not allowed. Implementations may differ on when this validation is performed.

      A `PathNotFoundException` will be thrown either immediately, or on `save`, if the specified path implies intermediary nodes that do not exist. Implementations may differ on when this validation is performed.

      A NoSuchNodeTypeException will be thrown either immediately or on `save`, if the specified node type is not recognized. Implementations may differ on when this validation is performed.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if adding the node would violate a node type or implementation-specific constraint or if an attempt is made to add a node as the child of a property. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save`, if the node to which the new child is being added is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately (by this method), or on `save`, if a lock prevents the addition of the node. Implementations may differ on when this validation is performed.

      Parameters:
      `relPath` - the path of the new node to be created.

      `primaryNodeTypeName` - The name of the primary node type of the new node.

      Returns:
      the node that was added.

      Throws:
      [`ItemExistsException`](ItemExistsException.md) - if an item at the specified path already exists, same-name siblings are not allowed and this implementation performs this validation immediately instead of waiting until `save`.

      [`PathNotFoundException`](PathNotFoundException.md) - if the specified path implies intermediary `Node`s that do not exist or the last element of `relPath` has an index, and this implementation performs this validation immediately instead of waiting until `save`.

      [`NoSuchNodeTypeException`](nodetype/NoSuchNodeTypeException.md) - if the specified node type is not recognized and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if a node type or implementation-specific constraint is violated or if an attempt is made to add a node as the child of a property and this implementation performs this validation immediately instead of waiting until `save`.

      [`VersionException`](version/VersionException.md) - if the node to which the new child is being added is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the addition of the node and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if the last element of `relPath` has an index or if another error occurs.

    <!-- -->

    - #### orderBefore

          void orderBefore(java.lang.String srcChildRelPath,
                           java.lang.String destChildRelPath)
                    throws UnsupportedRepositoryOperationException,
                           VersionException,
                           ConstraintViolationException,
                           ItemNotFoundException,
                           LockException,
                           RepositoryException

      If this node supports child node ordering, this method inserts the child node at `srcChildRelPath` before its sibling, the child node at `destChildRelPath`, in the child node list.
      To place the node `srcChildRelPath` at the end of the list, a `destChildRelPath` of `null` is used.

      Note that (apart from the case where `destChildRelPath` is `null`) both of these arguments must be relative paths of depth one, in other words they are the names of the child nodes, possibly suffixed with an index.

      If `srcChildRelPath` and `destChildRelPath` are the same, then no change is made.

      Changes to ordering of child nodes are persisted on `save` of the parent node. But, if this node does not support child node ordering, then a `UnsupportedRepositoryOperationException` thrown.

      If `srcChildRelPath` is not the relative path to a child node of this node then an `ItemNotFoundException` is thrown.

      If `destChildRelPath` is neither the relative path to a child node of this node nor `null`, then an `ItemNotFoundException` is also thrown.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if this operation would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save`, if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately (by this method), or on `save`, if a lock prevents the re-ordering. Implementations may differ on when this validation is performed.

      Parameters:
      `srcChildRelPath` - the relative path to the child node (that is, name plus possible index) to be moved in the ordering

      `destChildRelPath` - the the relative path to the child node (that is, name plus possible index) before which the node `srcChildRelPath` will be placed.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if ordering is not supported.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if an implementation-specific ordering restriction is violated and this implementation performs this validation immediately instead of waiting until `save`.

      [`ItemNotFoundException`](ItemNotFoundException.md) - if either parameter is not the relative path of a child node of this node.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`..

      [`LockException`](lock/LockException.md) - if a lock prevents the re-ordering and this implementation performs this validation immediately instead of waiting until `save`..

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               Value value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified (single-value) property of this node to the specified `value`. If the property does not yet exist, it is created. The property type of the property will be that specified by the node type of this node.
      If the property type of the supplied `Value` object is different from that required, then a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown. If another error occurs, a `RepositoryException` is thrown.

      If the node type of this node does not indicate a specific property type, then the property type of the supplied `Value` object is used and if the property already exists it assumes both the new value and new property type.

      If the property is multi-valued, a `ValueFormatException` is thrown.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (Value)null)` would remove property called `"P"` of the node in `N`.

      To persist the addition, removal or change of a property to the workspace, `save` must be called on the session, this node, or a higher-order ancestor of the property.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to be assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               Value value,
                               int type)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified (single-value) property to the specified value. If the property does not yet exist, it is created.
      The type of the new property is determined by the `type` parameter specified.

      If the property type of the supplied `Value` object is different from that required, then a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown.

      If the property is not single-valued then a `ValueFormatException` is also thrown.

      If the property already exists it assumes both the new value and the new property type.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (Value)null, type)` would remove property called `"P"` of the node in `N`.

      To persist the addition or removal of a property, `save` must be called on the `Session`, this `Node`, or an ancestor of this `Node`.

      To persist a change in the value of a property or in the type of a property (assuming the change is permitted by the applicable property definition) a save on the `Property` object itself is sufficent, though a `save` on the `Session`, this `Node` or an ancestor of this `Node` will also work.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - the name of the property to be set.

      `value` - a `Value` object.

      `type` - the type of the property.

      Returns:
      the `Property` object set, or `null` if this method was used to remove a property (by setting its value to `null`).

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the specified type or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               Value[] values)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified (multi-value) property to the specified array of values. If the property does not yet exist, it is created. Same as `setProperty(String name, Value value)` except that an array of `Value` objects is assigned instead of a single `Value`.
      The property type of the property will be that specified by the node type of this node. If the property type of the supplied `Value` objects is different from that required, then a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown.

      All `Value` objects in the array must be of the same type, otherwise a `ValueFormatException` is thrown. If the property is not multi-valued then a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.

      If the node type of this node does not indicate a specific property type, then the property type of the supplied `Value` objects is used and if the property already exists it assumes both the new values and the new property type.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (Value[])null)` would remove property called `"P"` of the node in `N`.

      Note that this is different from passing an array that contains `null` elements. In such a case, the array is compacted by removing the `null`s. The resulting set of values never contains nulls. However, the set may be empty: `N.setProperty("P", new Value[]{null})` would set the property to the empty set of values.

      To persist the addition, removal or change of a property to the workspace, save must be called on the session, this node, or a higher-order ancestor of the property.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - the name of the property to be set.

      `values` - an array of `Value` objects.

      Returns:
      the updated `Property` object.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is not multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               Value[] values,
                               int type)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified (multi-value) property to the specified array of values. If the property does not yet exist, it is created. The type of the property is determined by the `type` parameter specified.
      If the property type of the supplied `Value` objects is different from that specified, then a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown.

      If the property already exists it assumes both the new values and the new property type.

      All `Value` objects in the array must be of the same type, otherwise a `ValueFormatException` is thrown. If the property is not multi-valued then a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (Value[])null, type)` would remove property called `"P"` of the node in `N`.

      Note that this is different from passing an array that contains `null` elements. In such a case, the array is compacted by removing the `null`s. The resulting set of values never contains nulls. However, the set may be empty: `N.setProperty("P", new Value[]{null}, type)` would set the property to the empty set of values.

      To persist the addition, removal or change of a property to the workspace, save must be called on the session, this node, or a higher-order ancestor of the property.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - the name of the property to be set.

      `values` - an array of `Value` objects.

      `type` - the type of the property.

      Returns:
      the updated `Property` object.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the specified type or if the property already exists and is not multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               java.lang.String[] values)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified array of values. Same as `setProperty(String name, Value[] values)` except that the values are specified as `String` objects instead of `Value` objects.
      Parameters:
      `name` - the name of the property to be set.

      `values` - an array of `Value` objects.

      Returns:
      the updated `Property` object.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is not multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               java.lang.String[] values,
                               int type)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified array of values and to the specified type. Same as `setProperty(String name, Value[] values, int type)` except that the values are specified as `String` objects instead of `Value` objects.
      Parameters:
      `name` - the name of the property to be set.

      `values` - an array of `Value` objects.

      `type` - the type of the property.

      Returns:
      the updated `Property` object.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the specified type or if the property already exists and is not multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               java.lang.String value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified value. If the property does not yet exist, it is created. The property type of the property being set is determined by the node type of `this` node (the one on which this method is being called). If this is something other than `PropertyType.STRING`, a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown. If the property is multi-valued, a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.
      If the node type of `this` node does not specify a particular property type for the property being set then `PropertyType.STRING` is used and, if the property already exists, it assumes both the new value and type `PropertyType.STRING`.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (String)null)` would remove property called `"P"` of the node in `N`.

      To persist the addition, removal or change of a property `save` must be called.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               java.lang.String value,
                               int type)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified (single-value) property to the specified value. If the property does not yet exist, it is created.
      The type of the property is determined by the `type` parameter specified.

      If the property type specified is not `PropertyType.STRING`, then a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown.

      If the property is not single-valued then a `ValueFormatException` is also thrown.

      If the property already exists it assumes both the new value and the new property type.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (Value)null, type)` would remove property called `"P"` of the node in `N`.

      To persist the addition or removal of a property, `save` must be called on the `Session`, this `Node`, or an ancestor of this `Node`.

      To persist a change in the value of a property or in the type of a property (assuming the change is permitted by the applicable property definition) a save on the `Property` object itself is sufficent, though a `save` on the `Session`, this `Node` or an ancestor of this `Node` will also work.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - the name of the property to be set.

      `value` - a `String` object.

      `type` - the type of the property.

      Returns:
      the `Property` object set, or `null` if this method was used to remove a property (by setting its value to `null`).

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the specified type or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               java.io.InputStream value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified value. If the property does not yet exist, it is created. The property type of the property being set is determined by the node type of `this` node (the one on which this method is being called). If this is something other than `PropertyType.BINARY`, a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown. If the property is multi-valued, a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.
      If the node type of `this` node does not specify a particular property type for the property being set then `PropertyType.BINARY` is used and, if the property already exists, it assumes both the new value and type `PropertyType.BINARY`.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (InputStream)null)` would remove property called `"P"` of the node in `N`.

      To persist the addition, removal or change of a property `save` must be called.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               boolean value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified value. If the property does not yet exist, it is created. The property type of the property being set is determined by the node type of `this` node (the one on which this method is being called). If this is something other than `PropertyType.BOOLEAN`, a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown. If the property is multi-valued, a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.
      If the node type of `this` node does not specify a particular property type for the property being set then `PropertyType.BOOLEAN` is used and, if the property already exists, it assumes both the new value and type `PropertyType.BOOLEAN`.

      To persist the addition, removal or change of a property `save` must be called.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               double value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified value. If the property does not yet exist, it is created. The property type of the property being set is determined by the node type of `this` node (the one on which this method is being called). If this is something other than `PropertyType.DOUBLE`, a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown. If the property is multi-valued, a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.
      If the node type of `this` node does not specify a particular property type for the property being set then `PropertyType.DOUBLE` is used and, if the property already exists, it assumes both the new value and type `PropertyType.DOUBLE`.

      To persist the addition, removal or change of a property `save` must be called.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               long value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified value. If the property does not yet exist, it is created. The property type of the property being set is determined by the node type of `this` node (the one on which this method is being called). If this is something other than `PropertyType.LONG`, a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown. If the property is multi-valued, a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.
      If the node type of `this` node does not specify a particular property type for the property being set then `PropertyType.LONG` is used and, if the property already exists, it assumes both the new value and type `PropertyType.LONG`.

      To persist the addition, removal or change of a property `save` must be called.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               java.util.Calendar value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified property to the specified value. If the property does not yet exist, it is created. The property type of the property being set is determined by the node type of `this` node (the one on which this method is being called). If this is something other than `PropertyType.DATE`, a best-effort conversion is attempted. If the conversion fails, a `ValueFormatException` is thrown. If the property is multi-valued, a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.
      If the node type of `this` node does not specify a particular property type for the property being set then `PropertyType.DATE` is used and, if the property already exists, it assumes both the new value and type `PropertyType.DATE`.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (Calendar)null)` would remove property called `"P"` of the node in `N`.

      To persist the addition, removal or change of a property `save` must be called.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### setProperty

          Property setProperty(java.lang.String name,
                               Node value)
                        throws ValueFormatException,
                               VersionException,
                               LockException,
                               ConstraintViolationException,
                               RepositoryException

      Sets the specified (`REFERENCE`)property to refer to the specified `Node`. If the property does not yet exist, it is created. The property type of the property being set is determined by the node type of `this` node (the one on which this method is being called). If the property type of this property is something other than either `PropertyType.REFERENCE` or undefined then a `ValueFormatException` is thrown. If the property is multi-valued, a `ValueFormatException` is also thrown. If another error occurs, a `RepositoryException` is thrown.
      If the node type of `this` node does not specify a particular property type for the property being set then `PropertyType.REFERENCE` is used and, if the property already exists, it assumes both the new value and type `PropertyType.REFERENCE`.

      Passing a `null` as the second parameter removes the property. It is equivalent to calling `remove` on the `Property` object itself. For example, `N.setProperty("P", (Node)null)` would remove property called `"P"` of the node in `N`.

      To persist the addition, removal or change of a property `save` must be called.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the change would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the setting of the property. Implementations may differ on when this validation is performed.

      Parameters:
      `name` - The name of a property of this node

      `value` - The value to assigned

      Returns:
      The updated `Property` object

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if `value` cannot be converted to the type of the specified property or if the property already exists and is multi-valued.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the setting of the property and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the change would violate a node-type or other constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### getNode

          Node getNode(java.lang.String relPath)
                throws PathNotFoundException,
                       RepositoryException

      Returns the node at `relPath` relative to this node.
      If `relPath` contains a path element that refers to a node with same-name sibling nodes without explicitly including an index using the array-style notation (`[x]`), then the index \[1\] is assumed (indexing of same name siblings begins at 1, not 0, in order to preserve compatibility with XPath).

      Within the scope of a single `Session` object, if a `Node` object has been acquired, any subsequent call of getNode reacquiring the same node must return a `Node` object reflecting the same state as the earlier `Node` object. Whether this object is actually the same `Node` instance, or simply one wrapping the same state, is up to the implementation.

      Parameters:
      `relPath` - The relative path of the node to retrieve.

      Returns:
      The node at `relPath`.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - If no node exists at the specified path.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### getNodes

          NodeIterator getNodes()
                         throws RepositoryException

      Returns a `NodeIterator` over all child `Node`s of this `Node`. Does *not* include properties of this `Node`. The same reacquisition semantics apply as with `getNode(String)`. If this node has no child nodes, then an empty iterator is returned.
      Returns:
      A `NodeIterator` over all child `Node`s of this `Node`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an error occurs.

    <!-- -->

    - #### getNodes

          NodeIterator getNodes(java.lang.String namePattern)
                         throws RepositoryException

      Gets all child nodes of this node that match `namePattern`. The pattern may be a full name or a partial name with one or more wildcard characters ("`*`"), or a disjunction (using the "`|`" character to represent logical `OR`) of these. For example,
      `N.getNodes("jcr:* | myapp:report | my doc")`

      would return a `NodeIterator` holding all child nodes of `N` that are either called '`myapp:report`', begin with the prefix '`jcr:`' or are called '`my doc`'.

      Note that leading and trailing whitespace around a disjunct is ignored, but whitespace within a disjunct forms part of the pattern to be matched.

      The EBNF for `namePattern` is:

      `namePattern ::= disjunct {'|' disjunct}`
      `disjunct ::= name [':' name]`
      `name ::= '*' | ['*'] fragment {'*' fragment} ['*']`
      `fragment ::= char {char}`
      `char ::= nonspace | ' '`
      `nonspace ::= (* Any Unicode character except: '/', ':', '[', ']', '*', ''', '"', '|' or any whitespace character *)`

      The pattern is matched against the names (not the paths) of the immediate child nodes of this node.

      If this node has no matching child nodes, then an empty iterator is returned.

      The same reacquisition semantics apply as with `getNode(String)`.

      Parameters:
      `namePattern` - a name pattern

      Returns:
      a `NodeIterator`

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an unexpected error occurs.

    <!-- -->

    - #### getProperty

          Property getProperty(java.lang.String relPath)
                        throws PathNotFoundException,
                               RepositoryException

      Returns the property at `relPath` relative to `this` node. The same reacquisition semantics apply as with `getNode(String)`.
      Parameters:
      `relPath` - The relative path of the property to retrieve.

      Returns:
      The property at `relPath`.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - If no property exists at the specified path.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### getProperties

          PropertyIterator getProperties()
                                  throws RepositoryException

      Returns all properties of this node. Returns a `PropertyIterator` over all properties of this node. Does *not* include child *nodes* of this node. The same reacquisition semantics apply as with `getNode(String)`. If this node has no properties, then an empty iterator is returned.
      Returns:
      A `PropertyIterator`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an error occurs.

    <!-- -->

    - #### getProperties

          PropertyIterator getProperties(java.lang.String namePattern)
                                  throws RepositoryException

      Gets all properties of this node that match `namePattern`. The pattern may be a full name or a partial name with one or more wildcard characters ("`*`"), or a disjunction (using the "`|`" character to represent logical `OR`) of these. For example,
      `N.getProperties("jcr:* | myapp:name | my doc")`

      would return a `PropertyIterator` holding all properties of `N` that are either called '`myapp:name`', begin with the prefix '`jcr:`' or are called '`my doc`'.

      Note that leading and trailing whitespace around a disjunct is ignored, but whitespace within a disjunct forms part of the pattern to be matched.

      The EBNF for `namePattern` is:

      `namePattern ::= disjunct {'|' disjunct}`
      `disjunct ::= name [':' name]`
      `name ::= '*' | ['*'] fragment {'*' fragment} ['*']`
      `fragment ::= char {char}`
      `char ::= nonspace | ' '`
      `nonspace ::= (* Any Unicode character except: '/', ':', '[', ']', '*', ''', '"', '|' or any whitespace character *)`

      The pattern is matched against the names (not the paths) of the immediate child properties of this node.

      If this node has no matching properties, then an empty iterator is returned.

      The same reacquisition semantics apply as with `getNode(String)`.

      Parameters:
      `namePattern` - a name pattern

      Returns:
      a `PropertyIterator`

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an unexpected error occurs.

    <!-- -->

    - #### getPrimaryItem

          Item getPrimaryItem()
                       throws ItemNotFoundException,
                              RepositoryException

      Returns the primary child item of this node. The primary node type of this node may specify one child item (child node or property) of this node as the *primary child item*. This method returns that item. If this node does not have a primary item, either because none is declared in the node type or because a declared primary item is not present on this node instance, then this method throws an `ItemNotFoundException`. The same reacquisition semantics apply as with `getNode(String)`.
      Returns:
      the primary child item.

      Throws:
      [`ItemNotFoundException`](ItemNotFoundException.md) - if this node does not have a primary child item, either because none is declared in the node type or because a declared primary item is not present on this node instance.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getUUID

          java.lang.String getUUID()
                            throws UnsupportedRepositoryOperationException,
                                   RepositoryException

      Returns the UUID of this node as recorded in this node's `jcr:uuid` property. This method only works on nodes of mixin node type `mix:referenceable`. On nonreferenceable nodes, this method throws an `UnsupportedRepositoryOperationException`. To avoid throwing an exception to determine whether a node has a UUID, a call to `isNodeType("mix:referenceable")` can be made.
      Returns:
      the UUID of this node

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - If this node nonreferenceable.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### getIndex

          int getIndex()
                throws RepositoryException

      This method returns the index of this node within the ordered set of its same-name sibling nodes. This index is the one used to address same-name siblings using the square-bracket notation, e.g., `/a[3]/b[4]`. Note that the index always starts at 1 (not 0), for compatibility with XPath. As a result, for nodes that do not have same-name-siblings, this method will always return 1.
      Returns:
      The index of this node within the ordered set of its same-name sibling nodes.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getReferences

          PropertyIterator getReferences()
                                  throws RepositoryException

      Returns all `REFERENCE` properties that refer to this node.
      Some level 2 implementations may only return properties that have been saved (in a transactional setting this includes both those properties that have been saved but not yet committed, as well as properties that have been committed). Other level 2 implementations may additionally return properties that have been added within the current `Session` but are not yet saved.

      In implementations that support versioing, this method does not return `REFERENCE` propertiesthat are part of the frozen state of a version in version storage.

      If this node has no references, an empty iterator is returned.

      Returns:
      A `PropertyIterator`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs

    <!-- -->

    - #### hasNode

          boolean hasNode(java.lang.String relPath)
                   throws RepositoryException

      Indicates whether a node exists at `relPath` Returns `true` if a node exists at `relPath` and `false` otherwise.
      Parameters:
      `relPath` - The path of a (possible) node.

      Returns:
      `true` if a node exists at `relPath`; `false` otherwise.

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an unspecified error occurs.

    <!-- -->

    - #### hasProperty

          boolean hasProperty(java.lang.String relPath)
                       throws RepositoryException

      Indicates whether a property exists at `relPath` Returns `true` if a property exists at `relPath` and `false` otherwise.
      Parameters:
      `relPath` - The path of a (possible) property.

      Returns:
      `true` if a property exists at `relPath`; `false` otherwise.

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an unspecified error occurs.

    <!-- -->

    - #### hasNodes

          boolean hasNodes()
                    throws RepositoryException

      Indicates whether this node has child nodes. Returns `true` if this node has one or more child nodes; `false` otherwise.
      Returns:
      `true` if this node has one or more child nodes; `false` otherwise.

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an unspecified error occurs.

    <!-- -->

    - #### hasProperties

          boolean hasProperties()
                         throws RepositoryException

      Indicates whether this node has properties. Returns `true` if this node has one or more properties; `false` otherwise.
      Returns:
      `true` if this node has one or more properties; `false` otherwise.

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an unspecified error occurs.

    <!-- -->

    - #### getPrimaryNodeType

          NodeType getPrimaryNodeType()
                               throws RepositoryException

      Returns the primary node type of this node. Which node type is returned when this method is called on the root node of a workspace is up to the implementation, though the returned type must, of course, be consistent with ther child nodes and properties of the root node.
      Returns:
      a `NodeType` object.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs

    <!-- -->

    - #### getMixinNodeTypes

          NodeType[] getMixinNodeTypes()
                                throws RepositoryException

      Returns an array of NodeType objects representing the mixin node types assigned to this node. This includes only those mixin types explicitly assigned to this node, and therefore listed in the property `jcr:mixinTypes`. It does not include mixin types inherited through the additon of supertypes to the primary type hierarchy.
      Returns:
      an array of `NodeType` objects.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs

    <!-- -->

    - #### isNodeType

          boolean isNodeType(java.lang.String nodeTypeName)
                      throws RepositoryException

      Indicates whether this node is of the specified node type. Returns `true` if this node is of the specified node type or a subtype of the specified node type. Returns `false` otherwise.
      Parameters:
      `nodeTypeName` - the name of a node type.

      Returns:
      true if this node is of the specified node type or a subtype of the specified node type; returns false otherwise.

      Throws:
      [`RepositoryException`](RepositoryException.md) - If an error occurs.

    <!-- -->

    - #### addMixin

          void addMixin(java.lang.String mixinName)
                 throws NoSuchNodeTypeException,
                        VersionException,
                        ConstraintViolationException,
                        LockException,
                        RepositoryException

      Adds the specified mixin node type to this node. Also adds `mixinName` to this node's `jcr:mixinTypes` property immediately. Semantically, the mixin node type assignment may take effect immediately and at the very least, it must take effect on `save`.
      A `ConstraintViolationException` is thrown either immediately or on `save` if a conflict with another assigned mixin or the primary node type or for an implementation-specific reason. Implementations may differ on when this validation is done.

      In some implementations it may only be possible to add mixin types before a a node is first saved, and not after. I such cases any later calls to `addMixin` will throw a `ConstraintViolationException` either immediately or on `save`.

      A `NoSuchNodeTypeException` is thrown either immediately or on `save` if the specified `mixinName` is not recognized. Implementations may differ on when this validation is done.

      A `VersionException` is thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is done.

      A `LockException` is thrown either immediately or on `save` if a lock prevents the addition of the mixin. Implementations may differ on when this validation is done.

      Parameters:
      `mixinName` - the name of the mixin node type to be added

      Throws:
      [`NoSuchNodeTypeException`](nodetype/NoSuchNodeTypeException.md) - If the specified `mixinName` is not recognized and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - If the specified mixin node type is prevented from being assigned.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`..

      [`LockException`](lock/LockException.md) - if a lock prevents the addition of the mixin and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### removeMixin

          void removeMixin(java.lang.String mixinName)
                    throws NoSuchNodeTypeException,
                           VersionException,
                           ConstraintViolationException,
                           LockException,
                           RepositoryException

      Removes the specified mixin node type from this node. Also removes `mixinName` from this node's `jcr:mixinTypes` property immediately. Semantically, the mixin node type removal may take effect immediately and at the very least, it must take effect on `save`.
      If this node does not have the specified mixin, a `NoSuchNodeTypeException` is thrown either immediately or on `save`. Implementations may differ on when this validation is done.

      A `ConstraintViolationException` will be thrown either immediately or on `save` if the removal of a mixin is not allowed. Implementations are free to enforce any policy they like with regard to mixin removal and may differ on when this validation is done.

      A `VersionException` is thrown either immediately or on `save` if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is done.

      A `LockException` is thrown either immediately or on `save` if a lock prevents the removal of the mixin. Implementations may differ on when this validation is done.

      Parameters:
      `mixinName` - the name of the mixin node type to be removed.

      Throws:
      [`NoSuchNodeTypeException`](nodetype/NoSuchNodeTypeException.md) - if the specified `mixinName` is not currently assigned to this node and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the specified mixin node type is prevented from being removed and this implementation performs this validation immediately instead of waiting until `save`.

      [`VersionException`](version/VersionException.md) - if this node is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the removal of the mixin and this implementation performs this validation immediately instead of waiting until `save`..

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### canAddMixin

          boolean canAddMixin(java.lang.String mixinName)
                       throws NoSuchNodeTypeException,
                              RepositoryException

      Returns `true` if the specified mixin node type, `mixinName`, can be added to this node. Returns `false` otherwise. A result of `false` must be returned in each of the following cases:
      - The mixin's definition conflicts with an existing primary or mixin node type of this node.
      - This node is versionable and checked-in or is non-versionable and its nearest versionable ancestor is checked-in.
      - This node is protected (as defined in this node's `NodeDefinition`, found in the node type of this node's parent).
      - An access control restriction would prevent the addition of the mixin.
      - A lock would prevent the addition of the mixin.
      - An implementation-specific restriction would prevent the addition of the mixin.

      A `NoSuchNodeTypeException` is thrown if the specified mixin node type name is not recognized.
      Parameters:
      `mixinName` - The name of the mixin to be tested.

      Returns:
      `true` if the specified mixin node type, `mixinName`, can be added to this node; `false` otherwise.

      Throws:
      [`NoSuchNodeTypeException`](nodetype/NoSuchNodeTypeException.md) - if the specified mixin node type name is not recognized.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getDefinition

          NodeDefinition getDefinition()
                                throws RepositoryException

      Returns the node definition that applies to this node. In some cases there may appear to be more than one definition that could apply to this node. However, it is assumed that upon creation of this node, a single particular definition was used and it is *that* definition that this method returns. How this governing definition is selected upon node creation from among others which may have been applicable is an implementation issue and is not covered by this specification. The `NodeDefinition` returned when this method is called on the root node of a workspace is also up to the implementation.
      Returns:
      a `NodeDefinition` object.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

      See Also:
      [`NodeType.getChildNodeDefinitions()`](nodetype/NodeType.md)

    <!-- -->

    - #### checkin

          Version checkin()
                   throws VersionException,
                          UnsupportedRepositoryOperationException,
                          InvalidItemStateException,
                          LockException,
                          RepositoryException

      Creates a new version with a system generated version name and returns that version (which will be the new base version of this node). Sets the `jcr:checkedOut` property to false thus putting the node into the *checked-in* state. This means that this node and its *connected non-versionable subtree* become read-only. A node's connected non-versionable subtree is the set of non-versionable descendant nodes reachable from that node through child links without encountering any versionable nodes. In other words, the read-only status flows down from the checked-in node along every child link until either a versionable node is encountered or an item with no children is encountered.
      Read-only status means that an item cannot be altered by the client using standard API methods (addNode, setProperty, etc.). The only exceptions to this rule are the `restore(java.lang.String, boolean)` (all signatures), [`Workspace.restore(javax.jcr.version.Version[], boolean)`](Workspace.md), `merge(java.lang.String, boolean)` and `update(java.lang.String)` operations; these do not respect read-only status due to check-in. Note that `remove` of a read-only node is possible, as long as its parent is not read-only (since removal is an alteration of the parent node).

      If this node is already checked-in, this method has no effect but returns the current base version of this node.

      If this node is not versionable, an `UnsupportedRepositoryOperationException` is thrown.

      A `VersionException` is thrown or if a child item of this node has an `OnParentVersion` status of `ABORT`. This includes the case where an unresolved merge failure exists on this node, as indicated by the presence of the `jcr:mergeFailed` property.

      If there are unsaved changes pending on this node, an `InvalidItemStateException` is thrown.

      Throws a `LockException` if a lock prevents the checkin.

      If `checkin` succeeds, the change to the `jcr:checkedOut` property is automatically saved (there is no need to do an additional `save`).

      Returns:
      a `Version` object

      Throws:
      [`VersionException`](version/VersionException.md) - if jcr:predecessors does not contain at least one value or if a child item of this node has an `OnParentVersion` status of `ABORT`. This includes the case where an unresolved merge failure exists on this node, as indicated by the presence of a `jcr:mergeFailed` property.

      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - If this node is not versionable.

      [`InvalidItemStateException`](InvalidItemStateException.md) - If unsaved changes exist on this node.

      [`LockException`](lock/LockException.md) - if a lock prevents the checkin.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### checkout

          void checkout()
                 throws UnsupportedRepositoryOperationException,
                        LockException,
                        RepositoryException

      Sets this versionable node to checked-out status by setting its `jcr:isCheckedOut` property to true and adds to the `jcr:predecessors` (multi-value) property a reference to the current base version (the same value as held in `jcr:baseVersion`). This method puts the node into the *checked-out* state, making it and its connected non-versionable subtree no longer read-only (see `checkin()` for an explanation of the term "connected non-versionable subtree").
      If successful, these changes are persisted immediately, there is no need to call `save`.

      If this node is already checked-out, this method has no effect.

      If this node is not versionable, an `UnsupportedRepositoryOperationException` is thrown.
      Throws a `LockException` if a lock prevents the checkout.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - If this node is not versionable.

      [`LockException`](lock/LockException.md) - if a lock prevents the checkout.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### doneMerge

          void doneMerge(Version version)
                  throws VersionException,
                         InvalidItemStateException,
                         UnsupportedRepositoryOperationException,
                         RepositoryException

      Completes the merge process with respect to this node and the specified `version`.
      When the `merge(java.lang.String, boolean)` method is called on a node, every versionable node in that subtree is compared with its corresponding node in the indicated other workspace and a "merge test result" is determined indicating one of the following:

      1.  This node will be updated to the state of its correspondee (if the base version of the correspondee is more recent in terms of version history)
      2.  This node will be left alone (if this node's base version is more recent in terms of version history).
      3.  This node will be marked as having failed the merge test (if this node's base version is on a different branch of the version history from the base version of its corresponding node in the other workspace, thus preventing an automatic determination of which is more recent).

      (See `merge(java.lang.String, boolean)` for more details)
      In the last case the merge of the non-versionable subtree (the "content") of this node must be done by the application (for example, by providing a merge tool for the user).

      Additionally, once the content of the nodes has been merged, their version graph branches must also be merged. The JCR versioning system provides for this by keeping a record, for each versionable node that fails the merge test, of the base verison of the corresponding node that caused the merge failure. This record is kept in the `jcr:mergeFailed` property of this node. After a `merge`, this property will contain one or more (if multiple merges have been performed) `REFERENCE`s that point to the "offending versions".

      To complete the merge process, the client calls `doneMerge(Version v)` passing the version object referred to be the `jcr:mergeFailed` property that the client wishes to connect to `this` node in the version graph. This has the effect of moving the reference to the indicated version from the `jcr:mergeFailed` property of `this` node to the `jcr:predecessors`.

      If the client chooses not to connect this node to a particular version referenced in the `jcr:mergeFailed` property, he calls `cancelMerge(Version version)`. This has the effect of removing the reference to the specified `version` from `jcr:mergeFailed` *without* adding it to `jcr:predecessors`.

      Once the last reference in `jcr:mergeFailed` has been either moved to `jcr:predecessors` (with `doneMerge`) or just removed from `jcr:mergeFailed` (with `cancelMerge`) the `jcr:mergeFailed` property is automatically removed, thus enabling `this` node to be checked-in, creating a new version (note that before the `jcr:mergeFailed` is removed, its `OnParentVersion` setting of `ABORT` prevents checkin). This new version will have a predecessor connection to each version for which `doneMerge` was called, thus joining those branches of the version graph.

      If successful, these changes are persisted immediately, there is no need to call `save`.

      A `VersionException` is thrown if the `version` specified is not among those referecned in this node's `jcr:mergeFailed` property.

      If there are unsaved changes pending on this node, an `InvalidItemStateException` is thrown.

      An `UnsupportedRepositoryOperationException` is thrown if this node is not versionable.

      A `RepositoryException` is thrown if another error occurs.

      Parameters:
      `version` - a version referred to by this node's `jcr:mergeFailed` property.

      Throws:
      [`VersionException`](version/VersionException.md) - if the version specifed is not among those referenced in this node's `jcr:mergeFailed` or if this node is currently checked-in.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if there are unsaved changes pending on this node.

      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if this node is not versionable.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### cancelMerge

          void cancelMerge(Version version)
                    throws VersionException,
                           InvalidItemStateException,
                           UnsupportedRepositoryOperationException,
                           RepositoryException

      Cancels the merge process with respect to this node and specified `version`.
      See `doneMerge(javax.jcr.version.Version)` for a full explanation. Also see `merge(java.lang.String, boolean)` for more details.

      If successful, these changes are persisted immediately, there is no need to call `save`.

      A `VersionException` is thrown if the `version` specified is not among those referecned in this node's `jcr:mergeFailed`.

      An `UnsupportedRepositoryOperationException` is thrown if this nod is not versionable.

      If there are unsaved changes pending on this node, an `InvalidItemStateException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Parameters:
      `version` - a version referred to by this node's `jcr:mergeFailed` property.

      Throws:
      [`VersionException`](version/VersionException.md) - if the version specified is not among those referenced in this node's `jcr:mergeFailed` or if this node is currently checked-in.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if there are unsaved changes pending on this node.

      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if this node is not versionable.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### update

          void update(java.lang.String srcWorkspaceName)
               throws NoSuchWorkspaceException,
                      AccessDeniedException,
                      LockException,
                      InvalidItemStateException,
                      RepositoryException

      If this node does have a corresponding node in the workspace `srcWorkspaceName`, then this replaces this node and its subtree with a clone of the corresponding node and its subtree.
      If this node does not have a corresponding node in the workspace `srcWorkspaceName`, then the `update` method has no effect.

      The *corresponding node* is defined as the node in `srcWorkspace` with the same UUID as this node or, if this node has no UUID, the same path relative to the nearest ancestor that *does* have a UUID, or the root node, whichever comes first. This is qualified by the requirment that referencable nodes only correspond with other referencables and non-referenceables with other non-referenceables.

      If the update succeeds the changes made are persisted immediately, there is no need to call `save`.

      Note that `update` does not respect the checked-in status of nodes. An `update` may change a node even if it is currently checked-in (This fact is only relevant in an implementation that supports versioning).

      If the specified `srcWorkspace` does not exist, a `NoSuchWorkspaceException` is thrown.

      If the current session does not have sufficient rights to perform the operation, then an `AccessDeniedException` is thrown.

      An InvalidItemStateException is thrown if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      Throws a `LockException` if a lock prevents the update.

      A `RepositoryException` is thrown if another error occurs.

      Parameters:
      `srcWorkspaceName` - the name of the source workspace.

      Throws:
      [`NoSuchWorkspaceException`](NoSuchWorkspaceException.md) - If `srcWorkspace` does not exist.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      [`AccessDeniedException`](AccessDeniedException.md) - If the current session does not have sufficient rights to perform the operation.

      [`LockException`](lock/LockException.md) - if a lock prevents the update.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### merge

          NodeIterator merge(java.lang.String srcWorkspace,
                             boolean bestEffort)
                      throws NoSuchWorkspaceException,
                             AccessDeniedException,
                             VersionException,
                             LockException,
                             InvalidItemStateException,
                             RepositoryException

      This method can be thought of as a version-sensitive update (see 7.1.7 Updating and Cloning Nodes across Workspaces in the specification).
      It recursively tests each versionable node in the subtree of this node against its corresponding node in `srcWorkspace` with respect to the relation between their respective base versions and either updates the node in question or not, depending on the outcome of the test. For details see 8.2.10 Merge in the specification. A `MergeException` is thrown if `bestEffort` is false and a versionable node is encountered whose corresponding node's base version is on a divergent branch from this node's base version.

      If successful, the changes are persisted immediately, there is no need to call `save`.

      This method returns a `NodeIterator` over all versionable nodes in the subtree that received a merge result of fail.

      If `bestEffort` is false, this iterator will be empty (since if it merge returns successfully, instead of throwing an exception, it will be because no failures were encountered).

      If `bestEffort` is `true`, this iterator will contain all nodes that received a fail during the course of this merge operation.

      If the specified `srcWorkspace` does not exist, a `NoSuchWorkspaceException` is thrown.

      If the current session does not have sufficient permissions to perform the operation, then an `AccessDeniedException` is thrown.

      An `InvalidItemStateException` is thrown if this session (not necessarily this node) has pending unsaved changes.

      A `LockException` is thrown if a lock prevents the merge.

      Parameters:
      `srcWorkspace` - the name of the source workspace.

      `bestEffort` - a boolean

      Returns:
      iterator over all nodes that received a merge result of "fail" in the course of this operation.

      Throws:
      [`MergeException`](MergeException.md) - if `bestEffort` is `false` and a failed merge result is encountered.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this session (not necessarily this node) has pending unsaved changes.

      [`NoSuchWorkspaceException`](NoSuchWorkspaceException.md) - if `srcWorkspace` does not exist.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session does not have sufficient rights to perform the operation.

      [`LockException`](lock/LockException.md) - if a lock prevents the merge.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

      [`VersionException`](version/VersionException.md)

    <!-- -->

    - #### getCorrespondingNodePath

          java.lang.String getCorrespondingNodePath(java.lang.String workspaceName)
                                             throws ItemNotFoundException,
                                                    NoSuchWorkspaceException,
                                                    AccessDeniedException,
                                                    RepositoryException

      Returns the absolute path of the node in the specified workspace that corresponds to `this` node.
      The *corresponding node* is defined as the node in `srcWorkspace` with the same UUID as this node or, if this node has no UUID, the same path relative to the nearest ancestor that *does* have a UUID, or the root node, whichever comes first. This is qualified by the requirment that referencable nodes only correspond with other referencables and non-referenceables with other non-referenceables.

      If no corresponding node exists then an `ItemNotFoundException` is thrown.

      If the specified workspace does not exist then a `NoSuchWorkspaceException` is thrown.

      If the current `Session` does not have sufficent rights to perform this operation, an `AccessDeniedException` is thrown.

      Parameters:
      `workspaceName` -

      Returns:
      the absolute path to the corresponding node.

      Throws:
      [`ItemNotFoundException`](ItemNotFoundException.md) - if no corresponding node is found.

      [`NoSuchWorkspaceException`](NoSuchWorkspaceException.md) - if the workspace is unknown.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current `session` has insufficent rights to perform this operation.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### isCheckedOut

          boolean isCheckedOut()
                        throws RepositoryException

      Returns true if this node is either

      Returns false if this node is either

      Returns:
      a boolean

      Throws:
      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### restore

          void restore(java.lang.String versionName,
                       boolean removeExisting)
                throws VersionException,
                       ItemExistsException,
                       UnsupportedRepositoryOperationException,
                       LockException,
                       InvalidItemStateException,
                       RepositoryException

      Restores `this` node to the state defined by the version with the specified `versionName`.
      If this node is not versionable, an `UnsupportedRepositoryOperationException` is thrown.

      If successful, the change is persisted immediately and there is no need to call `save`.

      A `VersionException` is thrown if no version with the specified `versionName` exists in this node's version history or if an attempt is made to restore the root version (`jcr:rootVersion`).

      An InvalidItemStateException is thrown if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      A LockException is thrown if a lock prevents the addition of the mixin.

      This method will work regardless of whether this node is checked-in or not.

      A UUID collision occurs when a node exists *outside the subtree rooted at this node* with the same UUID as a node that would be introduced by the `restore` operation *into the subtree at this node*. The result in such a case is governed by the `removeExisting` flag. If `removeExisting` is `true`, then the incoming node takes precedence, and the existing node (and its subtree) is removed. If `removeExisting` is `false`, then a `ItemExistsException` is thrown and no changes are made. Note that this applies not only to cases where the restored node itself conflicts with an existing node but also to cases where a conflict occurs with any node that would be introduced into the workspace by the restore operation. In particular, conflicts involving subnodes of the restored node that have `OnParentVersion` settings of `COPY` or `VERSION` are also governed by the `removeExisting` flag.

      Parameters:
      `versionName` - a `Version` object

      `removeExisting` - a boolean flag that governs what happens in case of a UUID collision.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if versioning is not supported.

      [`VersionException`](version/VersionException.md) - if the specified `version` is not part of this node's version history or if an attempt is made to restore the root version (`jcr:rootVersion`).

      [`ItemExistsException`](ItemExistsException.md) - if `removeExisting` is `false` and a UUID collision occurs.

      [`LockException`](lock/LockException.md) - if a lock prevents the restore.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### restore

          void restore(Version version,
                       boolean removeExisting)
                throws VersionException,
                       ItemExistsException,
                       UnsupportedRepositoryOperationException,
                       LockException,
                       RepositoryException

      Restores `this` node to the state defined by the specified `version`.
      If this node is not versionable, an `UnsupportedRepositoryOperationException` is thrown.

      If successful, the change is persisted immediately and there is no need to call `save`.

      A `VersionException` is thrown if the specified `version` is not part of this node's version history or if an attempt is made to restore the root version (`jcr:rootVersion`).

      An InvalidItemStateException is thrown if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      A `LockException` is thrown if a lock prevents the restore.

      This method will work regardless of whether this node is checked-in or not.

      A UUID collision occurs when a node exists *outside the subtree rooted at this node* with the same UUID as a node that would be introduced by the `restore` operation *into the subtree at this node*. The result in such a case is governed by the `removeExisting` flag. If `removeExisting` is `true`, then the incoming node takes precedence, and the existing node (and its subtree) is removed. If `removeExisting` is `false`, then a `ItemExistsException` is thrown and no changes are made. Note that this applies not only to cases where the restored node itself conflicts with an existing node but also to cases where a conflict occurs with any node that would be introduced into the workspace by the restore operation. In particular, conflicts involving subnodes of the restored node that have `OnParentVersion` settings of `COPY` or `VERSION` are also governed by the `removeExisting` flag.

      Parameters:
      `version` - a `Version` object

      `removeExisting` - a boolean flag that governs what happens in case of a UUID collision.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if versioning is not supported.

      [`VersionException`](version/VersionException.md) - if the specified `version` is not part of this node's version history or if an attempt is made to restore the root version (`jcr:rootVersion`).

      [`ItemExistsException`](ItemExistsException.md) - if `removeExisting` is `false` and a UUID collision occurs.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      [`LockException`](lock/LockException.md) - if a lock prevents the restore.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### restore

          void restore(Version version,
                       java.lang.String relPath,
                       boolean removeExisting)
                throws PathNotFoundException,
                       ItemExistsException,
                       VersionException,
                       ConstraintViolationException,
                       UnsupportedRepositoryOperationException,
                       LockException,
                       InvalidItemStateException,
                       RepositoryException

      Restores the specified version to `relPath`, relative to this node.
      A node need not exist at relPath, though the parent of `relPath` must exist, otherwise a `PathNotFoundException` is thrown.

      If a node *does* exist at relPath then it must correspond to the version being restored (the version must be a version *of that node*) and must not be a root version (`jcr:rootVersion`), otherwise a `VersionException` is thrown.

      If no node exists at `relPath` then a `VersionException` is thrown if the parent node of `relPath` is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in.

      If there *is* a node at `relPath` then the checked-in status of that node itself and the checked-in status of its parent are irrelevant. The restore will work even if one or both are checked-in.

      A UUID collision occurs when a node exists *outside the subtree rooted at `relPath`* with the same UUID as a node that would be introduced by the `restore` operation *into the subtree at `relPath`* (Note that in cases where there is no node at `relPath`, this amounts to saying that a UUID collsion occurs if there exists a node *anywhere* in this workspace with the same UUID as a node that would be introduced by the `restore`). The result in such a case is governed by the `removeExisting` flag. If `removeExisting` is `true`, then the incoming node takes precedence, and the existing node (and its subtree) is removed. If `removeExisting` is `false`, then a `ItemExistsException` is thrown and no changes are made. Note that this applies not only to cases where the restored node itself conflicts with an existing node but also to cases where a conflict occurs with any node that would be introduced into the workspace by the restore operation. In particular, conflicts involving subnodes of the restored node that have `OnParentVersion` settings of `COPY` or `VERSION` are also governed by the `removeExisting` flag.

      If the would-be parent of the location `relPath` is actually a property, or if a node type restriction would be violated, then a `ConstraintViolationException` is thrown.

      If the `restore` succeeds, the changes made to this node are persisted immediately, there is no need to call `save`.

      An InvalidItemStateException is thrown if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      An `UnsupportedRepositoryOperationException` is thrown if versioning is not supported.

      A `LockException` is thrown if a lock prevents the restore.

      Parameters:
      `version` - a version object

      `relPath` - the path to which the version is to be restored

      `removeExisting` - overns what happens on UUID collision.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if the parent of `relPath` does not exist.

      [`ItemExistsException`](ItemExistsException.md) - if removeExisting is false and a UUID collision occurs

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - If the would-be parent of the location `relPath` is actually a property, or if a node type restriction would be violated

      [`VersionException`](version/VersionException.md) - if the parent node of `relPath` is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in or if a node exists at relPath that is not the node corresponding to the specified `version` or if an attempt is made to restore the root version (`jcr:rootVersion`).

      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if versioning is not supported.

      [`LockException`](lock/LockException.md) - if a lock prevents the restore.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### restoreByLabel

          void restoreByLabel(java.lang.String versionLabel,
                              boolean removeExisting)
                       throws VersionException,
                              ItemExistsException,
                              UnsupportedRepositoryOperationException,
                              LockException,
                              InvalidItemStateException,
                              RepositoryException

      Restores the version of this node with the specified version label. If this node is not versionable, an `UnsupportedRepositoryOperationException` is thrown. If successful, the change is persisted immediately and there is no need to call `save`.
      A `VersionException` is thrown if the specified `versionLabel` does not exist in this node's version history.

      An InvalidItemStateException is thrown if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      A `LockException` is thrown if a lock prevents the restore.

      This method will work regardless of whether this node is checked-in or not.

      A UUID collision occurs when a node exists *outside the subtree rooted at this node* with the same UUID as a node that would be introduced by the `restoreByLabel` operation *into the subtree at this node*. The result in such a case is governed by the `removeExisting` flag. If `removeExisting` is `true`, then the incoming node takes precedence, and the existing node (and its subtree) is removed. If `removeExisting` is `false`, then a `ItemExistsException` is thrown and no changes are made. Note that this applies not only to cases where the restored node itself conflicts with an existing node but also to cases where a conflict occurs with any node that would be introduced into the workspace by the restore operation. In particular, conflicts involving subnodes of the restored node that have `OnParentVersion` settings of `COPY` or `VERSION` are also governed by the `removeExisting` flag.

      Parameters:
      `versionLabel` - a String

      `removeExisting` - a boolean flag that governs what happens in case of a UUID collision.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if versioning is not supported.

      [`VersionException`](version/VersionException.md) - if the specified `versionLabel` does not exist in this node's version history.

      [`ItemExistsException`](ItemExistsException.md) - if `removeExisting` is `false` and a UUID collision occurs.

      [`LockException`](lock/LockException.md) - if a lock prevents the restore.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### getVersionHistory

          VersionHistory getVersionHistory()
                                    throws UnsupportedRepositoryOperationException,
                                           RepositoryException

      Returns the `VersionHistory` object of this node. This object provides access to the `nt:versionHistory` node holding this node's versions.
      If this node is not versionable, an `UnsupportedRepositoryOperationException` is thrown.

      Returns:
      a `VersionHistory` object

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if this node is not versionable.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### getBaseVersion

          Version getBaseVersion()
                          throws UnsupportedRepositoryOperationException,
                                 RepositoryException

      Returns the current base version of this versionable node.
      If this node is not versionable, an `UnsupportedRepositoryOperationException` is thrown.

      Returns:
      a `Version` object.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if this node is not versionable.

      [`RepositoryException`](RepositoryException.md) - If another error occurs.

    <!-- -->

    - #### lock

          Lock lock(boolean isDeep,
                    boolean isSessionScoped)
             throws UnsupportedRepositoryOperationException,
                    LockException,
                    AccessDeniedException,
                    InvalidItemStateException,
                    RepositoryException

      Places a lock on this node. If successful, this node is said to *hold* the lock.
      If `isDeep` is `true` then the lock applies to this node and all its descendant nodes; if `false`, the lock applies only to this, the holding node.

      If `isSessionScoped` is `true` then this lock will expire upon the expiration of the current session (either through an automatic or explicit `Session.logout`); if `false`, this lock does not expire until explicitly unlocked or automatically unlocked due to a implementation-specific limitation, such as a timeout.

      Returns a `Lock` object reflecting the state of the new lock and including a lock token. See, in contrast, `getLock()`, which returns the `Lock` *without* the lock token.

      The lock token is also automatically added to the set of lock tokens held by the current `Session`.

      If successful, then the property `jcr:lockOwner` is created and set to the value of `Session.getUserID` for the current session and the property `jcr:lockIsDeep` is set to the value passed in as `isDeep`. These changes are persisted automatically; there is no need to call `save`.

      Note that it is possible to lock a node even if it is checked-in (the lock-related properties will be changed despite the checked-in status).

      If this node is not of mixin node type `mix:lockable` then an `LockException` is thrown.

      If this node is already locked (either because it holds a lock or a lock above it applies to it), a `LockException` is thrown.

      If `isDeep` is `true` and a descendant node of this node already holds a lock, then a `LockException` is thrown.

      If the current session does not have sufficient privileges to place the lock, an `AccessDeniedException` is thrown.

      An `UnsupportedRepositoryOperationException` is thrown if this implementation does not support locking.

      An InvalidItemStateException is thrown if this node has pending unsaved changes.

      A `RepositoryException` is thrown if another error occurs.

      Parameters:
      `isDeep` - if `true` this lock will apply to this node and all its descendants; if `false`, it applies only to this node.

      `isSessionScoped` - if `true`, this lock expires with the current session; if `false` it expires when explicitly or automatically unlocked for some other reason.

      Returns:
      A `Lock` object containing a lock token.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if this implementation does not support locking.

      [`LockException`](lock/LockException.md) - if this node is not `mix:lockable` or this node is already locked or `isDeep` is `true` and a descendant node of this node already holds a lock.

      [`AccessDeniedException`](AccessDeniedException.md) - if this session does not have permission to lock this node.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this node has pending unsaved changes.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getLock

          Lock getLock()
                throws UnsupportedRepositoryOperationException,
                       LockException,
                       AccessDeniedException,
                       RepositoryException

      Returns the `Lock` object that applies to this node. This may be either a lock on this node itself or a deep lock on a node above this node.
      If this `Session` (the one through which this `Node` was acquired) holds the lock token for this lock, then the returned `Lock` object contains that lock token (accessible through `Lock.getLockToken`). If this `Session` does not hold the applicable lock token, then the returned `Lock` object will not contain the lock token (its `Lock.getLockToken` method will return `null`).

      If this node is not locked (no lock applies to this node), a `LockException` is thrown.

      If the current session does not have sufficient privileges to get the lock, an `AccessDeniedException` is thrown.

      An `UnsupportedRepositoryOperationException` is thrown if this implementation does not support locking.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      The applicable `Lock` object, without a contained lock token.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if this implementation does not support locking.

      [`LockException`](lock/LockException.md) - if no lock applies to this node.

      [`AccessDeniedException`](AccessDeniedException.md) - if the curent session does not have pernmission to get the lock.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### unlock

          void unlock()
               throws UnsupportedRepositoryOperationException,
                      LockException,
                      AccessDeniedException,
                      InvalidItemStateException,
                      RepositoryException

      Removes the lock on this node. Also removes the properties `jcr:lockOwner` and `jcr:lockIsDeep` from this node. These changes are persisted automatically; there is no need to call `save`.
      If this node does not currently hold a lock or holds a lock for which this Session does not have the correct lock token, then a `LockException` is thrown. Note however that the system may give permission to some users to unlock locks for which they do not have the lock token. Typically such "lock-superuser" capability is intended to facilitate administrational clean-up of orphaned open-scoped locks.

      Note that it is possible to unlock a node even if it is checked-in (the lock-related properties will be changed despite the checked-in status).

      If the current session does not have sufficient privileges to remove the lock, an `AccessDeniedException` is thrown.

      An `InvalidItemStateException` is thrown if this node has pending unsaved changes.

      An `UnsupportedRepositoryOperationException` is thrown if this implementation does not support locking.

      A `RepositoryException` is thrown if another error occurs.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if this implementation does not support locking.

      [`LockException`](lock/LockException.md) - if this node does not currently hold a lock or holds a lock for which this Session does not have the correct lock token

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session does not have permission to unlock this node.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this node has pending unsaved changes.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### holdsLock

          boolean holdsLock()
                     throws RepositoryException

      Returns `true` if this node holds a lock; otherwise returns `false`. To *hold* a lock means that this node has actually had a lock placed on it specifically, as opposed to just having a lock *apply* to it due to a deep lock held by a node above.
      Returns:
      a `boolean`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### isLocked

          boolean isLocked()
                    throws RepositoryException

      Returns `true` if this node is locked either as a result of a lock held by this node or by a deep lock on a node above this node; otherwise returns `false`.
      Returns:
      a `boolean`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NamespaceRegistry.md)**
- **[Next Class](NodeIterator.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
