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

- **[Prev Class](InvalidSerializedDataException.md)**
- **[Next Class](ItemExistsException.md)**

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

## **Interface Item**

- **All Known Subinterfaces:**
  **[Node](Node.md), [Property](Property.md), [Version](version/Version.md), [VersionHistory](version/VersionHistory.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Item

  **The `Item` is the base interface of [`Node`](Node.md) and [`Property`](Property.md).**

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                                                                                                                                                                                                               |
    |-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                  | `accept``(`[`ItemVisitor`](ItemVisitor.md)` visitor)`<br>Accepts an `ItemVistor`.                                                                                                                                                                                                                    |
    | `Item`                  | `getAncestor``(int depth)`<br>Returns the ancestor of the specified depth.                                                                                                                                                                                                                           |
    | `int`                   | `getDepth``()`<br>Returns the depth of this `Item` in the workspace tree.                                                                                                                                                                                                                            |
    | `java.lang.String`      | `getName``()`<br>Returns the name of this `Item`.                                                                                                                                                                                                                                                    |
    | [`Node`](Node.md)       | `getParent``()`<br>Returns the parent of this `Item`.                                                                                                                                                                                                                                                |
    | `java.lang.String`      | `getPath``()`<br>Returns the absolute path to this item.                                                                                                                                                                                                                                             |
    | [`Session`](Session.md) | `getSession``()`<br>Returns the `Session` through which this `Item` was acquired.                                                                                                                                                                                                                    |
    | `boolean`               | `isModified``()`<br>Returns `true` if this `Item` has been saved but has subsequently been modified through the current session and therefore the state of this item as recorded in the session differs from the state of this item as saved.                                                        |
    | `boolean`               | `isNew``()`<br>Returns `true` if this is a new item, meaning that it exists only in transient storage on the `Session` and has not yet been saved.                                                                                                                                                   |
    | `boolean`               | `isNode``()`<br>Indicates whether this `Item` is a `Node` or a `Property`.                                                                                                                                                                                                                           |
    | `boolean`               | `isSame``(Item otherItem)`<br>Returns `true` if this `Item` object (the Java object instance) represents the same actual repository item as the object `otherItem`.                                                                                                                                  |
    | `void`                  | `refresh``(boolean keepChanges)`<br>If `keepChanges` is `false`, this method discards all pending changes currently recorded in this `Session` that apply to this Item or any of its descendants (that is, the subtree rooted at this Item)and returns all items to reflect the current saved state. |
    | `void`                  | `remove``()`<br>Removes `this` item (and its subtree).                                                                                                                                                                                                                                               |
    | `void`                  | `save``()`<br>Validates all pending changes currently recorded in this `Session` that apply to this `Item` or any of its descendants (that is, the subtree rooted at this Item).                                                                                                                     |

<!-- -->

- - ### Method Detail

    - #### getPath

          java.lang.String getPath()
                            throws RepositoryException

      Returns the absolute path to this item. If the path includes items that are same-name sibling nodes properties then those elements in the path will include the appropriate "square bracket" index notation (for example, `/a/b[3]/c`).
      Returns:
      the path of this `Item`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getName

          java.lang.String getName()
                            throws RepositoryException

      Returns the name of this `Item`. The name of an item is the last element in its path, minus any square-bracket index that may exist. If this `Item` is the root node of the workspace (i.e., if `this.getDepth() == 0`), an empty string will be returned.
      Returns:
      the (or a) name of this `Item` or an empty string if this `Item` is the root node.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getAncestor

          Item getAncestor(int depth)
                    throws ItemNotFoundException,
                           AccessDeniedException,
                           RepositoryException

      Returns the ancestor of the specified depth. An ancestor of depth *x* is the `Item` that is *x* levels down along the path from the root node to *this* `Item`.
      - *depth* = 0 returns the root node.
      - *depth* = 1 returns the child of the root node along the path to *this* `Item`.
      - *depth* = 2 returns the grandchild of the root node along the path to *this* `Item`.
      - And so on to *depth* = *n*, where *n* is the depth of *this* `Item`, which returns *this* `Item` itself.

      If *depth* \> *n* is specified then a `ItemNotFoundException` is thrown.
      Parameters:
      `depth` - An integer, 0 \<= *depth* \<= *n* where *n* is the depth of *this* `Item`.

      Returns:
      The ancestor of this `Item` at the specified `depth`.

      Throws:
      [`ItemNotFoundException`](ItemNotFoundException.md) - if *depth* \< 0 or *depth* \> *n* where *n* is the is the depth of this item.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session does not have sufficient access rights to retrieve the specified node.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getParent

          Node getParent()
                  throws ItemNotFoundException,
                         AccessDeniedException,
                         RepositoryException

      Returns the parent of this `Item`.
      Returns:
      The parent of this `Item`.

      Throws:
      [`ItemNotFoundException`](ItemNotFoundException.md) - if there is no parent. This only happens if this item is the root node of a workspace.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session does not have sufficient access rights to retrieve the parent of this item.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getDepth

          int getDepth()
                throws RepositoryException

      Returns the depth of this `Item` in the workspace tree. Returns the depth below the root node of *this* `Item` (counting *this* `Item` itself).
      - The root node returns 0.
      - A property or child node of the root node returns 1.
      - A property or child node of a child node of the root returns 2.
      - And so on to *this* `Item`.

      Returns:
      The depth of this `Item` in the workspace hierarchy.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getSession

          Session getSession()
                      throws RepositoryException

      Returns the `Session` through which this `Item` was acquired. Every `Item` can ultimately be traced back through a series of method calls to the call [`Session.getRootNode()`](Session.md), [`Session.getItem(java.lang.String)`](Session.md) or [`Session.getNodeByUUID(java.lang.String)`](Session.md). This method returns that `Session` object.
      Returns:
      the `Session` through which this `Item` was acquired.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### isNode

          boolean isNode()

      Indicates whether this `Item` is a `Node` or a `Property`. Returns `true` if this `Item` is a `Node`; Returns `false` if this `Item` is a `Property`.
      Returns:
      `true` if this `Item` is a `Node`, `false` if it is a `Property`.

    <!-- -->

    - #### isNew

          boolean isNew()

      Returns `true` if this is a new item, meaning that it exists only in transient storage on the `Session` and has not yet been saved. Within a transaction, `isNew` on an `Item` may return `false` (because the item has been saved) even if that `Item` is not in persistent storage (because the transaction has not yet been committed).
      Note that if an item returns `true` on `isNew`, then by definition is parent will return `true` on `isModified`.

      Note that in level 1 (that is, read-only) implementations, this method will always return `false`.

      Returns:
      `true` if this item is new; `false` otherwise.

    <!-- -->

    - #### isModified

          boolean isModified()

      Returns `true` if this `Item` has been saved but has subsequently been modified through the current session and therefore the state of this item as recorded in the session differs from the state of this item as saved. Within a transaction, `isModified` on an `Item` may return `false` (because the `Item` has been saved since the modification) even if the modification in question is not in persistent storage (because the transaction has not yet been committed).
      Note that in level 1 (that is, read-only) implementations, this method will always return `false`.

      Returns:
      `true` if this item is modified; `false` otherwise.

    <!-- -->

    - #### isSame

          boolean isSame(Item otherItem)
                  throws RepositoryException

      Returns `true` if this `Item` object (the Java object instance) represents the same actual repository item as the object `otherItem`.
      This method does not compare the *states* of the two items. For example, if two `Item` objects representing the same actual repository item have been retrieved through two different sessions and one has been modified, then this method will still return `true` for these two objects. Note that if two `Item` objects representing the same repository item are retrieved through the *same* session they will always reflect the same state (see section 6.3.1 *Reflecting Item State* in the specification document) so comparing state is not an issue.

      Parameters:
      `otherItem` - the `Item` object to be tested for identity with this `Item`.

      Returns:
      `true` if this `Item` object and `otherItem` represent the same actual repository item; `false` otherwise.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### accept

          void accept(ItemVisitor visitor)
               throws RepositoryException

      Accepts an `ItemVistor`. Calls the appropriate `ItemVistor` `visit` method of the according to whether *this* `Item` is a `Node` or a `Property`.
      Parameters:
      `visitor` - The ItemVisitor to be accepted.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### save

          void save()
             throws AccessDeniedException,
                    ItemExistsException,
                    ConstraintViolationException,
                    InvalidItemStateException,
                    ReferentialIntegrityException,
                    VersionException,
                    LockException,
                    NoSuchNodeTypeException,
                    RepositoryException

      Validates all pending changes currently recorded in this `Session` that apply to this `Item` or any of its descendants (that is, the subtree rooted at this Item). If validation of *all* pending changes succeeds, then this change information is cleared from the `Session`. If the `save` occurs outside a transaction, the changes are persisted and thus made visible to other `Sessions`. If the `save` occurs within a transaction, the changes are not persisted until the transaction is committed.
      If validation fails, then no pending changes are saved and they remain recorded on the `Session`. There is no best-effort or partial save.

      When an item is saved the item in persistent storage to which pending changes are written is determined as follows:

      - If the transient item has a UUID, then the changes are written to the persistent item with the same UUID.
      - If the transient item does not have a UUID then its nearest ancestor with a UUID, or the root node (whichever occurs first) is found, and the relative path from the node in persistent node with that UUID is used to determine the item in persistent storage to which the changes are to be written.

      As a result of these rules, a `save` of an item that has a UUID will succeed even if that item has, in the meantime, been moved in persistent storage to a new location (that is, its path has changed). However, a `save` of a non-UUID item will fail (throwing an `InvalidItemStateException`) if it has, in the meantime, been moved in persistent storage to a new location. A `save` of a non-UUID item will also fail if it has, in addition to being moved, been replaced in its original position by a UUID-bearing item.
      Note that `save` uses the same rules to match items between transient storage and persistent storage as [`Node.update(java.lang.String)`](Node.md) does to match nodes between two workspaces.

      An `AccessDeniedException` will be thrown if any of the changes to be persisted would violate the access privileges of this `Session`.

      If any of the changes to be persisted would cause the removal of a node that is currently the target of a `REFERENCE` property then a `ReferentialIntegrityException` is thrown, provided that this `Session` has read access to that `REFERENCE` property. If, on the other hand, this `Session` does not have read access to the `REFERENCE` property in question, then an `AccessDeniedException` is thrown instead.

      An `ItemExistsException` will be thrown if any of the changes to be persisted would be prevented by the presence of an already existing item in the workspace.

      A `ConstraintViolationException` will be thrown if any of the changes to be persisted would violate a node type restriction. Additionally, a repository may use this exception to enforce implementation- or configuration-dependant restrictions.

      An `InvalidItemStateException` is thrown if any of the changes to be persisted conflicts with a change already persisted through another session and the implementation is such that this conflict can only be detected at save-time and therefore was not detected earlier, at change-time.

      A `VersionException` is thrown if the `save` would make a result in a change to persistent storage that would violate the read-only status of a checked-in node.

      A `LockException` is thrown if the `save` would result in a change to persistent storage that would violate a lock.

      A `NoSuchNodeTypeException` is thrown if the `save` would result in the addition of a node with an unrecognized node type.

      A `RepositoryException` will be thrown if another error occurs.

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if any of the changes to be persisted would violate the access privileges of the this `Session`. Also thrown if any of the changes to be persisted would cause the removal of a node that is currently referenced by a `REFERENCE` property that this Session *does not* have read access to.

      [`ItemExistsException`](ItemExistsException.md) - if any of the changes to be persisted would be prevented by the presence of an already existing item in the workspace.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if any of the changes to be persisted would violate a node type or restriction. Additionally, a repository may use this exception to enforce implementation- or configuration-dependent restrictions.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if any of the changes to be persisted conflicts with a change already persisted through another session and the implementation is such that this conflict can only be detected at save-time and therefore was not detected earlier, at change-time.

      [`ReferentialIntegrityException`](ReferentialIntegrityException.md) - if any of the changes to be persisted would cause the removal of a node that is currently referenced by a `REFERENCE` property that this `Session` has read access to.

      [`VersionException`](version/VersionException.md) - if the `save` would make a result in a change to persistent storage that would violate the read-only status of a checked-in node.

      [`LockException`](lock/LockException.md) - if the `save` would result in a change to persistent storage that would violate a lock.

      [`NoSuchNodeTypeException`](nodetype/NoSuchNodeTypeException.md) - if the `save` would result in the addition of a node with an unrecognized node type.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### refresh

          void refresh(boolean keepChanges)
                throws InvalidItemStateException,
                       RepositoryException

      If `keepChanges` is `false`, this method discards all pending changes currently recorded in this `Session` that apply to this Item or any of its descendants (that is, the subtree rooted at this Item)and returns all items to reflect the current saved state. Outside a transaction this state is simple the current state of persistent storage. Within a transaction, this state will reflect persistent storage as modified by changes that have been saved but not yet committed.
      If `keepChanges` is true then pending change are not discarded but items that do not have changes pending have their state refreshed to reflect the current saved state, thus revealing changes made by other sessions.

      An `InvalidItemStateException` is thrown if this `Item` object represents a workspace item that has been removed (either by this session or another).

      Throws:
      [`InvalidItemStateException`](InvalidItemStateException.md) - if this `Item` object represents a workspace item that has been removed (either by this session or another).

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### remove

          void remove()
               throws VersionException,
                      LockException,
                      ConstraintViolationException,
                      RepositoryException

      Removes `this` item (and its subtree).
      To persist a removal, a `save` must be performed that includes the (former) parent of the removed item within its scope.

      A `ReferentialIntegrityException` will be thrown on `save` if this item or an item in its subtree is currently the target of a `REFERENCE` property located in this workspace but outside this item's subtree and the current `Session` has read access to that `REFERENCE` property.

      An `AccessDeniedException` will be thrown on `save` if this item or an item in its subtree is currently the target of a `REFERENCE` property located in this workspace but outside this item's subtree and the current `Session` *does not* have read access to that `REFERENCE` property.

      A `ConstraintViolationException` will be thrown either immediately or on `save`, if removing this item would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      A `VersionException` will be thrown either immediately or on `save`, if the parent node of this item is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` will be thrown either immediately or on `save` if a lock prevents the removal of this item. Implementations may differ on when this validation is performed.

      Throws:
      [`VersionException`](version/VersionException.md) - if the parent node of this item is versionable and checked-in or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if a lock prevents the removal of this item and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if removing the specified item would violate a node type or implementation-specific constraint and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

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

- **[Prev Class](InvalidSerializedDataException.md)**
- **[Next Class](ItemExistsException.md)**

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
