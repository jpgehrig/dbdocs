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

- **[Prev Class](ValueFormatException.md)**
- **Next Class**

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

## **Interface Workspace**

- **All Known Subinterfaces:**
  **[OracleWorkspace](../../oracle/jcr/OracleWorkspace.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Workspace

  **The `Workspace` object represents a "view" of an actual repository workspace entity as seen through the authorization settings of its associated `Session`. Each `Workspace` object is associated one-to-one with a `Session` object. The `Workspace` object can be acquired by calling [`Session.getWorkspace()`](Session.md) on the associated `Session` object.**

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                         | Method and Description                                                                                                                                                                                                                                 |
    |-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                    | `clone``(java.lang.String srcWorkspace, java.lang.String srcAbsPath, java.lang.String destAbsPath, boolean removeExisting)`<br>Clones the subtree at the node `srcAbsPath` in `srcWorkspace` to the new location at `destAbsPath` in `this` workspace. |
    | `void`                                                    | `copy``(java.lang.String srcAbsPath, java.lang.String destAbsPath)`<br>This method copies the node at `srcAbsPath` to the new location at `destAbsPath`.                                                                                               |
    | `void`                                                    | `copy``(java.lang.String srcWorkspace, java.lang.String srcAbsPath, java.lang.String destAbsPath)`<br>This method copies the subtree at `srcAbsPath` in `srcWorkspace` to `destAbsPath` in `this` workspace.                                           |
    | `java.lang.String[]`                                      | `getAccessibleWorkspaceNames``()`<br>Returns an string array containing the names of all workspaces in this repository that are accessible to this user, given the `Credentials` that were used to get the `Session` tied to this `Workspace`.         |
    | [`ContentHandler`](../../org/xml/sax/ContentHandler.md)   | `getImportContentHandler``(java.lang.String parentAbsPath, int uuidBehavior)`<br>Returns an `org.xml.sax.ContentHandler` which can be used to push SAX events into the repository.                                                                     |
    | `java.lang.String`                                        | `getName``()`<br>Returns the name of the actual persistent workspace represented by this `Workspace` object.                                                                                                                                           |
    | [`NamespaceRegistry`](NamespaceRegistry.md)               | `getNamespaceRegistry``()`<br>Returns the `NamespaceRegistry` object, which is used to access information and (in level 2) set the mapping between namespace prefixes and URIs.                                                                        |
    | [`NodeTypeManager`](nodetype/NodeTypeManager.md)          | `getNodeTypeManager``()`<br>Returns the `NodeTypeManager` through which node type information can be queried.                                                                                                                                          |
    | [`ObservationManager`](observation/ObservationManager.md) | `getObservationManager``()`<br>If the the implementation supports observation this method returns the `ObservationManager` object; otherwise it throws an `UnsupportedRepositoryOperationException`.                                                   |
    | [`QueryManager`](query/QueryManager.md)                   | `getQueryManager``()`<br>Gets the `QueryManager`.                                                                                                                                                                                                      |
    | [`Session`](Session.md)                                   | `getSession``()`<br>Returns the `Session` object through which this `Workspace` object was acquired.                                                                                                                                                   |
    | `void`                                                    | `importXML``(java.lang.String parentAbsPath, java.io.InputStream in, int uuidBehavior)`<br>Deserializes an XML document and adds the resulting item subtree as a child of the node at `parentAbsPath`.                                                 |
    | `void`                                                    | `move``(java.lang.String srcAbsPath, java.lang.String destAbsPath)`<br>Moves the node at `srcAbsPath` (and its entire subtree) to the new location at `destAbsPath`.                                                                                   |
    | `void`                                                    | `restore``(`[`Version`](version/Version.md)`[] versions, boolean removeExisting)`<br>Restores a set of versions at once.                                                                                                                               |

<!-- -->

- - ### Method Detail

    - #### getSession

          Session getSession()

      Returns the `Session` object through which this `Workspace` object was acquired.
      Returns:
      a [`Session`](Session.md) object.

    <!-- -->

    - #### getName

          java.lang.String getName()

      Returns the name of the actual persistent workspace represented by this `Workspace` object.
      Returns:
      the name of this workspace.

    <!-- -->

    - #### copy

          void copy(java.lang.String srcAbsPath,
                    java.lang.String destAbsPath)
             throws ConstraintViolationException,
                    VersionException,
                    AccessDeniedException,
                    PathNotFoundException,
                    ItemExistsException,
                    LockException,
                    RepositoryException

      This method copies the node at `srcAbsPath` to the new location at `destAbsPath`. If successful, the change is persisted immediately, there is no need to call `save`.
      Copies of referenceable nodes (nodes with UUIDs) are automatically given new UUIDs.

      The `destAbsPath` provided must not have an index on its final element. If it does then a `RepositoryException` is thrown. Strictly speaking, the `destAbsPath` parameter is actually an *absolute path* to the parent node of the new location, appended with the new *name* desired for the copied node. It does not specify a position within the child node ordering. If ordering is supported by the node type of the parent node of the new location, then the new copy of the node is appended to the end of the child node list.

      This method cannot be used to copy just an individual property by itself. It copies an entire node and its subtree (including, of course, any properties contained therein).

      A `ConstraintViolationException` is thrown if the operation would violate a node-type or other implementation-specific constraint.

      A `VersionException` is thrown if the parent node of `destAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      An `AccessDeniedException` is thrown if the current session (i.e. the session that was used to acquire this `Workspace` object) does not have sufficient access rights to complete the operation.

      A `PathNotFoundException` is thrown if the node at `srcAbsPath` or the parent of `destAbsPath` does not exist.

      An `ItemExistException` is thrown if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed.

      A `LockException` is thrown if a lock prevents the copy.

      Parameters:
      `srcAbsPath` - the path of the node to be copied.

      `destAbsPath` - the location to which the node at `srcAbsPath` is to be copied.

      Throws:
      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the operation would violate a node-type or other implementation-specific constraint.

      [`VersionException`](version/VersionException.md) - if the parent node of `destAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session does not have sufficient access rights to complete the operation.

      [`PathNotFoundException`](PathNotFoundException.md) - if the node at `srcAbsPath` or the parent of `destAbsPath` does not exist.

      [`ItemExistsException`](ItemExistsException.md) - if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed.

      [`LockException`](lock/LockException.md) - if a lock prevents the copy.

      [`RepositoryException`](RepositoryException.md) - if the last element of `destAbsPath` has an index or if another error occurs.

    <!-- -->

    - #### copy

          void copy(java.lang.String srcWorkspace,
                    java.lang.String srcAbsPath,
                    java.lang.String destAbsPath)
             throws NoSuchWorkspaceException,
                    ConstraintViolationException,
                    VersionException,
                    AccessDeniedException,
                    PathNotFoundException,
                    ItemExistsException,
                    LockException,
                    RepositoryException

      This method copies the subtree at `srcAbsPath` in `srcWorkspace` to `destAbsPath` in `this` workspace. Unlike `clone`, this method *does* assign new UUIDs to the new copies of referenceable nodes. This operation is performed entirely within the persistent workspace, it does not involve transient storage and therefore does not require a `save`.
      The `destAbsPath` provided must not have an index on its final element. If it does then a `RepositoryException` is thrown. Strictly speaking, the `destAbsPath` parameter is actually an *absolute path* to the parent node of the new location, appended with the new *name* desired for the copied node. It does not specify a position within the child node ordering. If ordering is supported by the node type of the parent node of the new location, then the new copy of the node is appended to the end of the child node list.

      This method cannot be used to copy just an individual property by itself. It copies an entire node and its subtree (including, of course, any properties contained therein).

      A `NoSuchWorkspaceException` is thrown if `srcWorkspace` does not exist or if the current Session does not have permission to access it.

      A `ConstraintViolationException` is thrown if the operation would violate a node-type or other implementation-specific constraint.

      A `VersionException` is thrown if the parent node of `destAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      An `AccessDeniedException` is thrown if the current session (i.e. the session that was used to acquire this `Workspace` object) does not have sufficient access rights to complete the operation.

      A `PathNotFoundException` is thrown if the node at `srcAbsPath` in `srcWorkspace` or the parent of `destAbsPath` in this workspace does not exist.

      An `ItemExistException` is thrown if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed.

      A `LockException` is thrown if a lock prevents the copy.

      Parameters:
      `srcWorkspace` - the name of the workspace from which the copy is to be made.

      `srcAbsPath` - the path of the node to be copied.

      `destAbsPath` - the location to which the node at `srcAbsPath` is to be copied in `this` workspace.

      Throws:
      [`NoSuchWorkspaceException`](NoSuchWorkspaceException.md) - if `srcWorkspace` does not exist or if the current `Session` does not have permission to access it.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the operation would violate a node-type or other implementation-specific constraint

      [`VersionException`](version/VersionException.md) - if the parent node of `destAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session does have permission to access `srcWorkspace` but otherwise does not have sufficient access rights to complete the operation.

      [`PathNotFoundException`](PathNotFoundException.md) - if the node at `srcAbsPath` in `srcWorkspace` or the parent of `destAbsPath` in this workspace does not exist.

      [`ItemExistsException`](ItemExistsException.md) - if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed.

      [`LockException`](lock/LockException.md) - if a lock prevents the copy.

      [`RepositoryException`](RepositoryException.md) - if the last element of `destAbsPath` has an index or if another error occurs.

    <!-- -->

    - #### clone

          void clone(java.lang.String srcWorkspace,
                     java.lang.String srcAbsPath,
                     java.lang.String destAbsPath,
                     boolean removeExisting)
              throws NoSuchWorkspaceException,
                     ConstraintViolationException,
                     VersionException,
                     AccessDeniedException,
                     PathNotFoundException,
                     ItemExistsException,
                     LockException,
                     RepositoryException

      Clones the subtree at the node `srcAbsPath` in `srcWorkspace` to the new location at `destAbsPath` in `this` workspace. This method does not assign new UUIDs to the new nodes but preserves the UUIDs (if any) of their respective source nodes.
      If `removeExisting` is true and an existing node in this workspace (the destination workspace) has the same UUID as a node being cloned from `srcWorkspace`, then the incoming node takes precedence, and the existing node (and its subtree) is removed. If `removeExisting` is false then a UUID collision causes this method to throw a `ItemExistsException` and no changes are made.

      If successful, the change is persisted immediately, there is no need to call `save`.

      The `destAbsPath` provided must not have an index on its final element. If it does then a `RepositoryException` is thrown. Strictly speaking, the `destAbsPath` parameter is actually an *absolute path* to the parent node of the new location, appended with the new *name* desired for the cloned node. It does not specify a position within the child node ordering. If ordering is supported by the node type of the parent node of the new location, then the new clone of the node is appended to the end of the child node list.

      This method cannot be used to clone just an individual property by itself. It clones an entire node and its subtree (including, of course, any properties contained therein).

      A `NoSuchWorkspaceException` is thrown if `srcWorkspace` does not exist or if the current `Session` does not have permission to access it.

      A `ConstraintViolationException` is thrown if the operation would violate a node-type or other implementation-specific constraint.

      A `VersionException` is thrown if the parent node of `destAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in. This exception will also be thrown if `removeExisting` is `true`, and a UUID conflict occurs that would require the moving and/or altering of a node that is checked-in.

      An `AccessDeniedException` is thrown if the current session (i.e. the session that was used to acquire this `Workspace` object) does not have sufficient access rights to complete the operation.

      A `PathNotFoundException` is thrown if the node at `srcAbsPath` in `srcWorkspace` or the parent of `destAbsPath` in this workspace does not exist.

      An `ItemExistsException` is thrown if a node or property already exists at `destAbsPath`

      An `ItemExistException` is thrown if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed or if `removeExisting` is false and a UUID conflict occurs.

      A `LockException` is thrown if a lock prevents the clone.

      Parameters:
      `srcWorkspace` - The name of the workspace from which the node is to be copied.

      `srcAbsPath` - the path of the node to be copied in `srcWorkspace`.

      `destAbsPath` - the location to which the node at `srcAbsPath` is to be copied in `this` workspace.

      `removeExisting` - if `false` then this method throws an `ItemExistsException` on UUID conflict with an incoming node. If `true` then a UUID conflict is resolved by removing the existing node from its location in this workspace and cloning (copying in) the one from `srcWorkspace`.

      Throws:
      [`NoSuchWorkspaceException`](NoSuchWorkspaceException.md) - if `destWorkspace` does not exist.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the operation would violate a node-type or other implementation-specific constraint.

      [`VersionException`](version/VersionException.md) - if the parent node of `destAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in. This exception will also be thrown if `removeExisting` is `true`, and a UUID conflict occurs that would require the moving and/or altering of a node that is checked-in.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session does not have sufficient access rights to complete the operation.

      [`PathNotFoundException`](PathNotFoundException.md) - if the node at `srcAbsPath` in `srcWorkspace` or the parent of `destAbsPath` in this workspace does not exist.

      [`ItemExistsException`](ItemExistsException.md) - if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed or if `removeExisting` is false and a UUID conflict occurs.

      [`LockException`](lock/LockException.md) - if a lock prevents the clone.

      [`RepositoryException`](RepositoryException.md) - if the last element of `destAbsPath` has an index or if another error occurs.

    <!-- -->

    - #### move

          void move(java.lang.String srcAbsPath,
                    java.lang.String destAbsPath)
             throws ConstraintViolationException,
                    VersionException,
                    AccessDeniedException,
                    PathNotFoundException,
                    ItemExistsException,
                    LockException,
                    RepositoryException

      Moves the node at `srcAbsPath` (and its entire subtree) to the new location at `destAbsPath`. If successful, the change is persisted immediately, there is no need to call `save`. Note that this is in contrast to [`Session.move(java.lang.String, java.lang.String)`](Session.md) which operates within the transient space and hence requires a `save`.
      The `destAbsPath` provided must not have an index on its final element. If it does then a `RepositoryException` is thrown. Strictly speaking, the `destAbsPath` parameter is actually an *absolute path* to the parent node of the new location, appended with the new *name* desired for the moved node. It does not specify a position within the child node ordering. If ordering is supported by the node type of the parent node of the new location, then the newly moved node is appended to the end of the child node list.

      This method cannot be used to move just an individual property by itself. It moves an entire node and its subtree (including, of course, any properties contained therein).

      A `ConstraintViolationException` is thrown if the operation would violate a node-type or other implementation-specific constraint.

      A `VersionException` is thrown if the parent node of `destAbsPath` or the parent node of `srcAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      An `AccessDeniedException` is thrown if the current session (i.e. the session that was used to acquire this `Workspace` object) does not have sufficient access rights to complete the operation.

      A `PathNotFoundException` is thrown if the node at `srcAbsPath` or the parent of `destAbsPath` does not exist.

      An `ItemExistException` is thrown if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed.

      A `LockException` if a lock prevents the move.

      Parameters:
      `srcAbsPath` - the path of the node to be moved.

      `destAbsPath` - the location to which the node at `srcAbsPath` is to be moved.

      Throws:
      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the operation would violate a node-type or other implementation-specific constraint

      [`VersionException`](version/VersionException.md) - if the parent node of `destAbsPath` or the parent node of `srcAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      [`AccessDeniedException`](AccessDeniedException.md) - if the current session (i.e. the session that was used to aqcuire this `Workspace` object) does not have sufficient access rights to complete the operation.

      [`PathNotFoundException`](PathNotFoundException.md) - if the node at `srcAbsPath` or the parent of `destAbsPath` does not exist.

      [`ItemExistsException`](ItemExistsException.md) - if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed.

      [`LockException`](lock/LockException.md) - if a lock prevents the move.

      [`RepositoryException`](RepositoryException.md) - if the last element of `destAbsPath` has an index or if another error occurs.

    <!-- -->

    - #### restore

          void restore(Version[] versions,
                       boolean removeExisting)
                throws ItemExistsException,
                       UnsupportedRepositoryOperationException,
                       VersionException,
                       LockException,
                       InvalidItemStateException,
                       RepositoryException

      Restores a set of versions at once. Used in cases where a "chicken and egg" problem of mutually referring `REFERENCE` properties would prevent the restore in any serial order.
      If the restore succeeds the changes made to `this` node are persisted immediately, there is no need to call `save`.

      The following restrictions apply to the set of versions specified:

      If `S` is the set of versions being restored simultaneously,

      - For every version `V` in `S` that corresponds to a *missing* node, there must also be a parent of V in S.
      - `S` must contain at least one version that corresponds to an existing node in the workspace.
      - No `V` in `S` can be a root version (`jcr:rootVersion`).

      If any of these restrictions does not hold, the restore will fail because the system will be unable to determine the path locations to which one or more versions are to be restored. In this case a `VersionException` is thrown.
      The versionable nodes in this workspace that correspond to the versions being restored define a set of (one or more) subtrees. A UUID collision occurs when this workspace contains a node *outside these subtrees* that has the same UUID as one of the nodes that would be introduced by the `restore` operation *into one of these subtrees*. The result in such a case is governed by the `removeExisting` flag. If `removeExisting` is `true` then the incoming node takes precedence, and the existing node (and its subtree) is removed. If `removeExisting` is `false` then a `ItemExistsException` is thrown and no changes are made. Note that this applies not only to cases where the restored node itself conflicts with an existing node but also to cases where a conflict occurs with any node that would be introduced into the workspace by the restore operation. In particular, conflicts involving subnodes of the restored node that have `OnParentVersion` settings of `COPY` or `VERSION` are also governed by the `removeExisting` flag.

      An `UnsupportedRepositoryOperationException` is thrown if versioning is not supported.

      An `InvalidItemStateException` is thrown if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      A `LockException` is thrown if a lock prevents the restore.

      Parameters:
      `versions` - The set of versions to be restored

      `removeExisting` - governs what happens on UUID collision.

      Throws:
      [`ItemExistsException`](ItemExistsException.md) - if `removeExisting` is `false` and a UUID collision occurs with a node being restored.

      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if versioning is not supported.

      [`VersionException`](version/VersionException.md) - if the set of versions to be restored is such that the original path location of one or more of the versions cannot be determined or if the `restore` would change the state of a existing verisonable node that is currently checked-in or if a root version (`jcr:rootVersion`) is among those being restored.

      [`LockException`](lock/LockException.md) - if a lock prevents the restore.

      [`InvalidItemStateException`](InvalidItemStateException.md) - if this `Session` (not necessarily this `Node`) has pending unsaved changes.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getQueryManager

          QueryManager getQueryManager()
                                throws RepositoryException

      Gets the `QueryManager`. Returns the `QueryManager` object, through search methods are accessed.
      Returns:
      the `QueryManager` object.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getNamespaceRegistry

          NamespaceRegistry getNamespaceRegistry()
                                          throws RepositoryException

      Returns the `NamespaceRegistry` object, which is used to access information and (in level 2) set the mapping between namespace prefixes and URIs.
      Returns:
      the `NamespaceRegistry`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getNodeTypeManager

          NodeTypeManager getNodeTypeManager()
                                      throws RepositoryException

      Returns the `NodeTypeManager` through which node type information can be queried. There is one node type registry per repository, therefore the `NodeTypeManager` is not workspace-specific; it provides introspection methods for the global, repository-wide set of available node types.
      Returns:
      a `NodeTypeManager` object.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getObservationManager

          ObservationManager getObservationManager()
                                            throws UnsupportedRepositoryOperationException,
                                                   RepositoryException

      If the the implementation supports observation this method returns the `ObservationManager` object; otherwise it throws an `UnsupportedRepositoryOperationException`.
      Returns:
      an `ObservationManager` object.

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if the implementation does not support observation.

      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getAccessibleWorkspaceNames

          java.lang.String[] getAccessibleWorkspaceNames()
                                                  throws RepositoryException

      Returns an string array containing the names of all workspaces in this repository that are accessible to this user, given the `Credentials` that were used to get the `Session` tied to this `Workspace`.
      In order to access one of the listed workspaces, the user performs another `Repository.login`, specifying the name of the desired workspace, and receives a new `Session` object.

      Returns:
      string array of names of accessible workspaces.

      Throws:
      [`RepositoryException`](RepositoryException.md)

    <!-- -->

    - #### getImportContentHandler

          ContentHandler getImportContentHandler(java.lang.String parentAbsPath,
                                                 int uuidBehavior)
                                          throws PathNotFoundException,
                                                 ConstraintViolationException,
                                                 VersionException,
                                                 LockException,
                                                 AccessDeniedException,
                                                 RepositoryException

      Returns an `org.xml.sax.ContentHandler` which can be used to push SAX events into the repository. If the incoming XML stream (in the form of SAX events) does not appear to be a JCR system view XML document then it is interpreted as a document view XML document.
      The incoming XML is deserialized into a subtree of items immediately below the node at `parentAbsPath`.

      This method simply returns the `ContentHandler` without altering the state of the repository; the actual deserialization is done through the methods of the `ContentHandler`. Invalid XML data will cause the `ContentHandler` to throw a `SAXException`.

      As SAX events are fed into the `ContentHandler`, changes are made directly at the workspace level, without going through the `Session`. As a result, there is not need to call `save`. The advantage of this direct-to-workspace method is that a large import will not result in a large cache of pending nodes in the `Session`. The disadvantage is that structures that violate node type constraints cannot be imported, fixed and then saved. Instead, a constraint violation will cause the `ContentHandler` to throw a `SAXException`. See `Session.getImportContentHandler` for a version of this method that *does* go through the `Session`.

      The flag `uuidBehavior` governs how the UUIDs of incoming (deserialized) nodes are handled. There are four options:

      - [`ImportUUIDBehavior.IMPORT_UUID_CREATE_NEW`](ImportUUIDBehavior.md): Incoming referenceable nodes are assigned newly created UUIDs upon additon to the workspace. As a result UUID collisions never occur.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REMOVE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace, then the already exisitng node (and its subtree) is removed from wherever it may be in the workspace before the incoming node is added. Note that this can result in nodes "disappearing" from locations in the workspace that are remote from the location to which the incoming subtree is being written.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REPLACE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then the already existing node is replaced by the incoming node in the same position as the existing node. Note that this may result in the incoming subtree being disaggregated and "spread around" to different locations in the workspace. In the most extreme case this behavior may result in no node at all being added as child of `parentAbsPath`. This will occur if the topmost element of the incoming XML has the same UUID as an existing node elsewhere in the workspace.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_THROW`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then a SAXException is thrown by the returned `ContentHandler` during deserialization.

      A `SAXException` will be thrown by the returned `ContentHandler` during deserialization if the top-most element of the incoming XML would deserialize to a node with the same name as an existing child of `parentAbsPath` and that child does not allow same-name siblings.
      A `SAXException` will also be thrown by the returned `ContentHandler` during deserialzation if `uuidBehavior` is set to `IMPORT_UUID_COLLISION_REMOVE_EXISTING` and an incoming node has the same UUID as the node at `parentAbsPath` or one of its ancestors.

      A `PathNotFoundException` is thrown if no node exists at `parentAbsPath`.

      A `ConstraintViolationException` is thrown if the new subtree cannot be added to the node at `parentAbsPath` due to node-type or other implementation-specific constraints, and this can be determined before the first SAX event is sent. Unlike [`Session.getImportContentHandler(java.lang.String, int)`](Session.md), this method also enforces node type constraints by throwing `SAXException`s during deserialization. However, which node type constraints are enforced depends upon whether node type information in the imported data is respected, and this is an implementation-specific issue.

      A `VersionException` is thrown if the node at `parentAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      A `LockException` is thrown if a lock prevents the addition ofthe subtree.

      An `AccessDeniedException` is thrown if the session associated with this `Workspace` object does not have sufficient permissions to perform the import.

      Parameters:
      `parentAbsPath` - the absolute path of a node under which (as child) the imported subtree will be built.

      `uuidBehavior` - a four-value flag that governs how incoming UUIDs are handled.

      Returns:
      an org.xml.sax.ContentHandler whose methods may be called to feed SAX events into the deserializer.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `parentAbsPath`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the new subtree cannot be added to the node at `parentAbsPath` due to node-type or other implementation-specific constraints, and this can be determined before the first SAX event is sent.

      [`VersionException`](version/VersionException.md) - if the node at `parentAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      [`LockException`](lock/LockException.md) - if a lock prevents the addition of the subtree.

      [`AccessDeniedException`](AccessDeniedException.md) - if the session associated with this `Workspace` object does not have sufficient permissions to perform the import.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### importXML

          void importXML(java.lang.String parentAbsPath,
                         java.io.InputStream in,
                         int uuidBehavior)
                  throws java.io.IOException,
                         PathNotFoundException,
                         ItemExistsException,
                         ConstraintViolationException,
                         InvalidSerializedDataException,
                         LockException,
                         AccessDeniedException,
                         RepositoryException

      Deserializes an XML document and adds the resulting item subtree as a child of the node at `parentAbsPath`.
      If the incoming XML stream does not appear to be a JCR system view XML document then it is interpreted as a **document view** XML document.

      Changes are made directly at the workspace level, without going through the `Session`. As a result, there is not need to call `save`. The advantage of this direct-to-workspace method is that a large import will not result in a large cache of pending nodes in the `Session`. The disadvantage is that invalid data cannot be imported, fixed and then saved. Instead, invalid data will cause this method to throw an `InvalidSerializedDataException`. See `Session.importXML` for a version of this method that *does* go through the `Session`.

      The flag `uuidBehavior` governs how the UUIDs of incoming (deserialized) nodes are handled. There are four options:

      - [`ImportUUIDBehavior.IMPORT_UUID_CREATE_NEW`](ImportUUIDBehavior.md): Incoming referenceable nodes are assigned newly created UUIDs upon additon to the workspace. As a result UUID collisions never occur.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REMOVE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then the already exisitng node (and its subtree) is removed from wherever it may be in the workspace before the incoming node is added. Note that this can result in nodes "disappearing" from locations in the workspace that are remote from the location to which the incoming subtree is being written. If an incoming node has the same UUID as the existing root node of this workspace then
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REPLACE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then the already existing node is replaced by the incoming node in the same position as the existing node. Note that this may result in the incoming subtree being disaggregated and "spread around" to different locations in the workspace. In the most extreme edge case this behavior may result in no node at all being added as child of `parentAbsPath`. This will occur if the topmost element of the incoming XML has the same UUID as an existing node elsewhere in the workspace.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_THROW`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then an `ItemExistsException` is thrown.

      An `ItemExistsException` will be thrown if `uuidBehavior` is set to `IMPORT_UUID_CREATE_NEW` or `IMPORT_UUID_COLLISION_THROW` and the import would would overwrite an existing child of `parentAbsPath`.
      An IOException is thrown if an I/O error occurs.

      If no node exists at `parentAbsPath`, a `PathNotFoundException` is thrown.

      An ItemExisitsException is thrown if the top-most element of the incoming XML would deserialize to a node with the same name as an existing child of `parentAbsPath` and that child does not allow same-name siblings, or if a `uuidBehavior` is set to `IMPORT_UUID_COLLISION_THROW` and a UUID collision occurs.

      If node-type or other implementation-specific constraints prevent the addition of the subtree, a `ConstraintViolationException` is thrown.

      A `ConstraintViolationException` will also be thrown if `uuidBehavior` is set to `IMPORT_UUID_COLLISION_REMOVE_EXISTING` and an incoming node has the same UUID as the node at `parentAbsPath` or one of its ancestors.

      A `VersionException` is thrown if the node at `parentAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      A `LockException` is thrown if a lock prevents the addition of the subtree.

      An `AccessDeniedException` is thrown if the session associated with this `Workspace` object does not have sufficient permissions to perform the import.

      Parameters:
      `parentAbsPath` - the absolute path of the node below which the deserialized subtree is added.

      `in` - The `Inputstream` from which the XML to be deserilaized is read.

      `uuidBehavior` - a four-value flag that governs how incoming UUIDs are handled.

      Throws:
      `java.io.IOException` - if an error during an I/O operation occurs.

      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `parentAbsPath`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if node-type or other implementation-specific constraints prevent the addition of the subtree or if `uuidBehavior` is set to `IMPORT_UUID_COLLISION_REMOVE_EXISTING` and an incoming node has the same UUID as the node at `parentAbsPath` or one of its ancestors.

      [`VersionException`](version/VersionException.md) - if the node at `parentAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in.

      [`InvalidSerializedDataException`](InvalidSerializedDataException.md) - if incoming stream is not a valid XML document.

      [`ItemExistsException`](ItemExistsException.md) - if the top-most element of the incoming XML would deserialize to a node with the same name as an existing child of `parentAbsPath` and that child does not allow same-name siblings, or if a `uuidBehavior` is set to `IMPORT_UUID_COLLISION_THROW` and a UUID collision occurs.

      [`LockException`](lock/LockException.md) - if a lock prevents the addition of the subtree.

      [`AccessDeniedException`](AccessDeniedException.md) - if the session associated with this `Workspace` object does not have sufficient permissions to perform the import.

      [`RepositoryException`](RepositoryException.md) - is another error occurs.

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

- **[Prev Class](ValueFormatException.md)**
- **Next Class**

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
