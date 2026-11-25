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

- **[Prev Class](RepositoryException.md)**
- **[Next Class](SimpleCredentials.md)**

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

## **Interface Session**

- **All Known Subinterfaces:**
  **[OracleSession](../../oracle/jcr/OracleSession.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Session

  **The `Session` object provides read and (in level 2) write access to the content of a particular workspace in the repository.**
  **The `Session` object is returned by [`Repository.login(javax.jcr.Credentials, java.lang.String)`](Repository.md). It encapsulates both the authorization settings of a particular user (as specified by the passed `Credentials`)and a binding to the workspace specified by the `workspaceName` passed on `login`.**

  **Each `Session` object is associated one-to-one with a `Workspace` object. The `Workspace` object represents a "view" of an actual repository workspace entity as seen through the authorization settings of its associated `Session`.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                                                                                                                                                                                                    |
    |---------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                  | `addLockToken``(java.lang.String lt)`<br>Adds the specified lock token to this session.                                                                                                                                                                                                                                                                   |
    | `void`                                                  | `checkPermission``(java.lang.String absPath, java.lang.String actions)`<br>Determines whether this `Session` has permission to perform the specified actions at the specified `absPath`.                                                                                                                                                                  |
    | `void`                                                  | `exportDocumentView``(java.lang.String absPath, `[`ContentHandler`](../../org/xml/sax/ContentHandler.md)` contentHandler, boolean skipBinary, boolean noRecurse)`<br>Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` into a series of SAX events by calling the methods of the supplied `org.xml.sax.ContentHandler`. |
    | `void`                                                  | `exportDocumentView``(java.lang.String absPath, java.io.OutputStream out, boolean skipBinary, boolean noRecurse)`<br>Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` as an XML stream and outputs it to the supplied `OutputStream`.                                                                                  |
    | `void`                                                  | `exportSystemView``(java.lang.String absPath, `[`ContentHandler`](../../org/xml/sax/ContentHandler.md)` contentHandler, boolean skipBinary, boolean noRecurse)`<br>Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` into a series of SAX events by calling the methods of the supplied `org.xml.sax.ContentHandler`.   |
    | `void`                                                  | `exportSystemView``(java.lang.String absPath, java.io.OutputStream out, boolean skipBinary, boolean noRecurse)`<br>Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` as an XML stream and outputs it to the supplied `OutputStream`.                                                                                    |
    | `java.lang.Object`                                      | `getAttribute``(java.lang.String name)`<br>Returns the value of the named attribute as an `Object`, or `null` if no attribute of the given name exists.                                                                                                                                                                                                   |
    | `java.lang.String[]`                                    | `getAttributeNames``()`<br>Returns the names of the attributes set in this session as a result of the `Credentials` that were used to acquire it.                                                                                                                                                                                                         |
    | [`ContentHandler`](../../org/xml/sax/ContentHandler.md) | `getImportContentHandler``(java.lang.String parentAbsPath, int uuidBehavior)`<br>Returns an `org.xml.sax.ContentHandler` which can be used to push SAX events into the repository.                                                                                                                                                                        |
    | [`Item`](Item.md)                                       | `getItem``(java.lang.String absPath)`<br>Returns the item at the specified absolute path in the workspace.                                                                                                                                                                                                                                                |
    | `java.lang.String[]`                                    | `getLockTokens``()`<br>Returns an array containing all lock tokens currently held by this session.                                                                                                                                                                                                                                                        |
    | `java.lang.String`                                      | `getNamespacePrefix``(java.lang.String uri)`<br>Returns the prefix to which the given URI is mapped                                                                                                                                                                                                                                                       |
    | `java.lang.String[]`                                    | `getNamespacePrefixes``()`<br>Returns all prefixes currently set for this session.                                                                                                                                                                                                                                                                        |
    | `java.lang.String`                                      | `getNamespaceURI``(java.lang.String prefix)`<br>For a given prefix, returns the URI to which it is mapped as currently set in this `Session`.                                                                                                                                                                                                             |
    | [`Node`](Node.md)                                       | `getNodeByUUID``(java.lang.String uuid)`<br>Returns the node specifed by the given UUID.                                                                                                                                                                                                                                                                  |
    | [`Repository`](Repository.md)                           | `getRepository``()`<br>Returns the `Repository` object through which this session was acquired.                                                                                                                                                                                                                                                           |
    | [`Node`](Node.md)                                       | `getRootNode``()`<br>Returns the root node of the workspace.                                                                                                                                                                                                                                                                                              |
    | `java.lang.String`                                      | `getUserID``()`<br>Gets the user ID that was used to acquire this session.                                                                                                                                                                                                                                                                                |
    | [`ValueFactory`](ValueFactory.md)                       | `getValueFactory``()`<br>This method returns a `ValueFactory` that is used to create `Value` objects for use when setting repository properties.                                                                                                                                                                                                          |
    | [`Workspace`](Workspace.md)                             | `getWorkspace``()`<br>Returns the `Workspace` attached to this `Session`.                                                                                                                                                                                                                                                                                 |
    | `boolean`                                               | `hasPendingChanges``()`<br>Returns `true` if this session holds pending (that is, unsaved) changes; otherwise returns `false`.                                                                                                                                                                                                                            |
    | `Session`                                               | `impersonate``(`[`Credentials`](Credentials.md)` credentials)`<br>Returns a new session in accordance with the specified (new) Credentials.                                                                                                                                                                                                               |
    | `void`                                                  | `importXML``(java.lang.String parentAbsPath, java.io.InputStream in, int uuidBehavior)`<br>Deserializes an XML document and adds the resulting item subtree as a child of the node at parentAbsPath.                                                                                                                                                      |
    | `boolean`                                               | `isLive``()`<br>Returns `true` if this `Session` object is usable by the client.                                                                                                                                                                                                                                                                          |
    | `boolean`                                               | `itemExists``(java.lang.String absPath)`<br>Returns `true` if an item exists at `absPath`; otherwise returns `false`.                                                                                                                                                                                                                                     |
    | `void`                                                  | `logout``()`<br>Releases all resources associated with this `Session`.                                                                                                                                                                                                                                                                                    |
    | `void`                                                  | `move``(java.lang.String srcAbsPath, java.lang.String destAbsPath)`<br>Moves the node at `srcAbsPath` (and its entire subtree) to the new location at `destAbsPath`.                                                                                                                                                                                      |
    | `void`                                                  | `refresh``(boolean keepChanges)`<br>If `keepChanges` is `false`, this method discards all pending changes currently recorded in this `Session` and returns all items to reflect the current saved state.                                                                                                                                                  |
    | `void`                                                  | `removeLockToken``(java.lang.String lt)`<br>Removes the specified lock token from this session.                                                                                                                                                                                                                                                           |
    | `void`                                                  | `save``()`<br>Validates all pending changes currently recorded in this `Session`.                                                                                                                                                                                                                                                                         |
    | `void`                                                  | `setNamespacePrefix``(java.lang.String prefix, java.lang.String uri)`<br>Within the scope of this session, rename a persistently registered namespace URI to the new prefix.                                                                                                                                                                              |

<!-- -->

- - ### Method Detail

    - #### getRepository

          Repository getRepository()

      Returns the `Repository` object through which this session was acquired.
      Returns:
      a [`Repository`](Repository.md) object.

    <!-- -->

    - #### getUserID

          java.lang.String getUserID()

      Gets the user ID that was used to acquire this session. This method is free to return an "anonymous user id" or `null` if the `Credentials` used to acquire this session happens not to have provided a real user ID (for example, if instead of `SimpleCredentials` some other implementation of `Credentials` was used).
      Returns:
      the user id from the credentials used to acquire this session.

    <!-- -->

    - #### getAttribute

          java.lang.Object getAttribute(java.lang.String name)

      Returns the value of the named attribute as an `Object`, or `null` if no attribute of the given name exists. See `getAttributeNames()`.
      Parameters:
      `name` - the name of an attribute passed in the credentials used to acquire this session.

      Returns:
      the value of the attribute.

    <!-- -->

    - #### getAttributeNames

          java.lang.String[] getAttributeNames()

      Returns the names of the attributes set in this session as a result of the `Credentials` that were used to acquire it. Not all `Credentials` implementations will contain attributes (though, for example, `SimpleCredentials` does allow for them). This method returns an empty array if the `Credentials` instance used to acquire this `Session` did not provide attributes.
      Returns:
      A string array containing the names of all attributes passed in the credentials used to acquire this session.

    <!-- -->

    - #### getWorkspace

          Workspace getWorkspace()

      Returns the `Workspace` attached to this `Session`.
      Returns:
      a [`Workspace`](Workspace.md) object.

    <!-- -->

    - #### impersonate

          Session impersonate(Credentials credentials)
                       throws LoginException,
                              RepositoryException

      Returns a new session in accordance with the specified (new) Credentials. Allows the current user to "impersonate" another using incomplete credentials (perhaps including a user name but no password, for example), assuming that their original session gives them that permission.
      The new `Session` is tied to a new `Workspace` instance. In other words, `Workspace` instances are not re-used. However, the `Workspace` instance returned represents the same actual persistent workspace entity in the repository as is represented by the `Workspace` object tied to this `Session`.

      Throws a `LoginException` if the current session does not have sufficient rights.

      Parameters:
      `credentials` - A `Credentials` object

      Returns:
      a `Session` object

      Throws:
      [`LoginException`](LoginException.md) - if the current session does not have sufficient rights.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getRootNode

          Node getRootNode()
                    throws RepositoryException

      Returns the root node of the workspace. The root node, "/", is the main access point to the content of the workspace.
      Returns:
      The root node of the workspace: a `Node` object.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getNodeByUUID

          Node getNodeByUUID(java.lang.String uuid)
                      throws ItemNotFoundException,
                             RepositoryException

      Returns the node specifed by the given UUID. Only applies to nodes that expose a UUID, in other words, those of mixin node type `mix:referenceable`
      Parameters:
      `uuid` - A universally unique identifier.

      Returns:
      A `Node`.

      Throws:
      [`ItemNotFoundException`](ItemNotFoundException.md) - if the specified UUID is not found.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getItem

          Item getItem(java.lang.String absPath)
                throws PathNotFoundException,
                       RepositoryException

      Returns the item at the specified absolute path in the workspace.
      Parameters:
      `absPath` - An absolute path.

      Returns:
      An `Item`.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if the specified path cannot be found.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### itemExists

          boolean itemExists(java.lang.String absPath)
                      throws RepositoryException

      Returns `true` if an item exists at `absPath`; otherwise returns `false`. Also returns `false` if the specified `absPath` is malformed.
      Parameters:
      `absPath` - an absolute path

      Returns:
      `true` if an item exists at `absPath`; otherwise returns `false`.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### move

          void move(java.lang.String srcAbsPath,
                    java.lang.String destAbsPath)
             throws ItemExistsException,
                    PathNotFoundException,
                    VersionException,
                    ConstraintViolationException,
                    LockException,
                    RepositoryException

      Moves the node at `srcAbsPath` (and its entire subtree) to the new location at `destAbsPath`.
      In order to persist the change, a `save` must be called on the parents of both the source and destination locations.

      A `ConstraintViolationException` is thrown either immediately or on `save` if performing this operation would violate a node type or implementation-specific constraint. Implementations may differ on when this validation is performed.

      As well, a `ConstraintViolationException` will be thrown on `save` if an attempt is made to seperately `save` either the source or destination node.

      Note that this behaviour differs from that of [`Workspace.move(java.lang.String, java.lang.String)`](Workspace.md), which operates directly in the persistent workspace and does not require a `save`.

      The `destAbsPath` provided must not have an index on its final element. If it does then a `RepositoryException` is thrown. Strictly speaking, the `destAbsPath` parameter is actually an *absolute path* to the parent node of the new location, appended with the new *name* desired for the moved node. It does not specify a position within the child node ordering (if such ordering is supported). If ordering is supported by the node type of the parent node of the new location, then the newly moved node is appended to the end of the child node list.

      This method cannot be used to move just an individual property by itself. It moves an entire node and its subtree (including, of course, any properties contained therein).

      If no node exists at `srcAbsPath` or no node exists one level above `destAbsPath` (in other words, there is no node that will serve as the parent of the moved item) then a `PathNotFoundException` is thrown either immediately or on `save`. Implementations may differ on when this validation is performed.

      An `ItemExistsException` is thrown either immediately or on `save` if a property already exists at `destAbsPath` or a node already exists there and same-name siblings are not allowed. Implementations may differ on when this validation is performed.

      A `VersionException` is thrown either immediately or on `save` if the parent node of `destAbsPath` or the parent node of `srcAbsPath] is versionable and checked-in, or is non-versionable and its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.`

      `A ``LockException`` is thrown either immediately or on ``save`` if a lock prevents the ``move``. Implementations may differ on when this validation is performed.`

      Parameters:
      `srcAbsPath` - the root of the subtree to be moved.

      `destAbsPath` - the location to which the subtree is to be moved.

      Throws:
      [`ItemExistsException`](ItemExistsException.md) - if a property already exists at `destAbsPath` or a node already exist there, and same name siblings are not allowed and this implementation performs this validation immediately instead of waiting until `save`.

      [`PathNotFoundException`](PathNotFoundException.md) - if either `srcAbsPath` or `destAbsPath` cannot be found and this implementation performs this validation immediately instead of waiting until `save`.

      [`VersionException`](version/VersionException.md) - if the parent node of `destAbsPath` or the parent node of `srcAbsPath` is versionable and checked-in, or or is non-verionable and its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if a node-type or other constraint violation is detected immediately and this implementation performs this validation immediately instead of waiting until `save`.

      [`LockException`](lock/LockException.md) - if the move operation would violate a lock and this implementation performs this validation immediately instead of waiting until `save`.

      [`RepositoryException`](RepositoryException.md) - if the last element of `destAbsPath` has an index or if another error occurs.

    <!-- -->

    - #### save

          void save()
             throws AccessDeniedException,
                    ItemExistsException,
                    ConstraintViolationException,
                    InvalidItemStateException,
                    VersionException,
                    LockException,
                    NoSuchNodeTypeException,
                    RepositoryException

      Validates all pending changes currently recorded in this `Session`. If validation of all pending changes succeeds, then this change information is cleared from the `Session`. If the `save` occurs outside a transaction, the changes are persisted and thus made visible to other `Sessions`. If the `save` occurs within a transaction, the changes are not persisted until the transaction is committed.
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

      A `LockException` is thrown if any of the changes to be persisted would violate a lock.

      An `InvalidItemStateException` is thrown if any of the changes to be persisted conflicts with a change already persisted through another session and the implementation is such that this conflict can only be detected at save-time and therefore was not detected earlier, at change-time.

      A `VersionException` is thrown if the `save` would make a result in a change to persistent storage that would violate the read-only status of a checked-in node.

      A `LockException` is thrown if the `save` would result in a change to persistent storage that would violate a lock.

      A `NoSuchNodeTypeException` is thrown if the `save` would result in the addition of a node with an unrecognized node type.

      A `RepositoryException` will be thrown if another error occurs.

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if any of the changes to be persisted would violate the access privileges of the this `Session`. Also thrown if any of the changes to be persisted would cause the removal of a node that is currently referenced by a `REFERENCE` property that this Session *does not* have read access to.

      [`ItemExistsException`](ItemExistsException.md) - if any of the changes to be persisted would be prevented by the presence of an already existing item in the workspace.

      [`LockException`](lock/LockException.md) - if any of the changes to be persisted would violate a lock.

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
                throws RepositoryException

      If `keepChanges` is `false`, this method discards all pending changes currently recorded in this `Session` and returns all items to reflect the current saved state. Outside a transaction this state is simply the current state of persistent storage. Within a transaction, this state will reflect persistent storage as modified by changes that have been saved but not yet committed.
      If `keepChanges` is true then pending change are not discarded but items that do not have changes pending have their state refreshed to reflect the current saved state, thus revealing changes made by other sessions.

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### hasPendingChanges

          boolean hasPendingChanges()
                             throws RepositoryException

      Returns `true` if this session holds pending (that is, unsaved) changes; otherwise returns `false`.
      Returns:
      a boolean

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs

    <!-- -->

    - #### getValueFactory

          ValueFactory getValueFactory()
                                throws UnsupportedRepositoryOperationException,
                                       RepositoryException

      This method returns a `ValueFactory` that is used to create `Value` objects for use when setting repository properties.
      If writing to the repository is not supported (because this is a level 1-only implementation, for example) an `UnsupportedRepositoryOperationException` will be thrown.

      Returns:
      a `ValueFactory`

      Throws:
      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - if writing to the repository is not supported.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### checkPermission

          void checkPermission(java.lang.String absPath,
                               java.lang.String actions)
                        throws java.security.AccessControlException,
                               RepositoryException

      Determines whether this `Session` has permission to perform the specified actions at the specified `absPath`. This method quietly returns if the access request is permitted, or throws a suitable `java.security.AccessControlException` otherwise.
      The `actions` parameter is a comma separated list of action strings. The following action strings are defined:

      - `add_node`: If `checkPermission(path, "add_node")` returns quietly, then this `Session` has permission to add a node at `path`, otherwise permission is denied.
      - `set_property`: If `checkPermission(path, "set_property")` returns quietly, then this `Session` has permission to set (add or change) a property at `path`, otherwise permission is denied.
      - `remove`: If `checkPermission(path, "remove")` returns quietly, then this `Session` has permission to remove an item at `path`, otherwise permission is denied.
      - `read`: If `checkPermission(path, "read")` returns quietly, then this `Session` has permission to retrieve (and read the value of, in the case of a property) an item at `path`, otherwise permission is denied.

      When more than one action is specified in the `actions` parameter, this method will only return quietly if this `Session` has permission to perform *all* of the listed actions at the specified path.
      The information returned through this method will only reflect access control policies and not other restrictions that may exist. For example, even though `checkPermission` may indicate that a particular `Session` may add a property at `/A/B/C`, the node type of the node at `/A/B` may prevent the addition of a property called `C`.

      Throws:
      `java.security.AccessControlException` - If permission is denied.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getImportContentHandler

          ContentHandler getImportContentHandler(java.lang.String parentAbsPath,
                                                 int uuidBehavior)
                                          throws PathNotFoundException,
                                                 ConstraintViolationException,
                                                 VersionException,
                                                 LockException,
                                                 RepositoryException

      Returns an `org.xml.sax.ContentHandler` which can be used to push SAX events into the repository. If the incoming XML stream (in the form of SAX events) does not appear to be a JCR *system view* XML document then it is interpreted as a JCR *document view* XML document.
      The incoming XML is deserialized into a subtree of items immediately below the node at `parentAbsPath`.

      This method simply returns the `ContentHandler` without altering the state of the session; the actual deserialization to the session transient space is done through the methods of the `ContentHandler`. Invalid XML data will cause the `ContentHandler` to throw a `SAXException`.

      As SAX events are fed into the `ContentHandler`, the tree of new items is built in the transient storage of the session. In order to persist the new content, `save` must be called. The advantage of this through-the-session method is that (depending on which constraint checks the implementation leaves until `save`) structures that violate node type constraints can be imported, fixed and then saved. The disadvantage is that a large import will result in a large cache of pending nodes in the session. See [`Workspace.getImportContentHandler(java.lang.String, int)`](Workspace.md) for a version of this method that does not go through the session.

      The flag `uuidBehavior` governs how the UUIDs of incoming (deserialized) nodes are handled. There are four options:

      - [`ImportUUIDBehavior.IMPORT_UUID_CREATE_NEW`](ImportUUIDBehavior.md): Incoming referenceable nodes are added in the same way that new node is added with `Node.addNode`. That is, they are either assigned newly created UUIDs upon addition or upon `save` (depending on the implementation). In either case, UUID collisions will not occur.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REMOVE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then the already existing node (and its subtree) is removed from wherever it may be in the workspace before the incoming node is added. Note that this can result in nodes "disappearing" from locations in the workspace that are remote from the location to which the incoming subtree is being written. Both the removal and the new addition will be persisted on `save`.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REPLACE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace, then the already-existing node is replaced by the incoming node in the same position as the existing node. Note that this may result in the incoming subtree being disaggregated and "spread around" to different locations in the workspace. In the most extreme case this behavior may result in no node at all being added as child of `parentAbsPath`. This will occur if the topmost element of the incoming XML has the same UUID as an existing node elsewhere in the workspace. The change will be persisted on `save`.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_THROW`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then a `SAXException` is thrown by the `ContentHandler` during deserialization.

      Unlike `Workspace.getImportContentHandler`, this method does not necessarily enforce all node type constraints during deserialization. Those that would be immediately enforced in a normal write method (`Node.addNode`, `Node.setProperty` etc.) of this implementation cause the returned `ContentHandler` to throw an immediate `SAXException` during deserialization. All other constraints are checked on save, just as they are in normal write operations. However, which node type constraints are enforced depends upon whether node type information in the imported data is respected, and this is an implementation-specific issue.
      A `SAXException` will also be thrown by the returned `ContentHandler` during deserialization if `uuidBehavior` is set to `IMPORT_UUID_COLLISION_REMOVE_EXISTING` and an incoming node has the same UUID as the node at `parentAbsPath` or one of its ancestors.

      A `PathNotFoundException` is thrown either immediately or on `save` if no node exists at `parentAbsPath`. Implementations may differ on when this validation is performed

      A `ConstraintViolationException` is thrown either immediately or on `save` if the new subtree cannot be added to the node at parentAbsPath due to node-type or other implementation-specific constraints, and this can be determined before the first SAX event is sent. Implementations may differ on when this validation is performed.

      A `VersionException` is thrown either immediately or on `save` if the node at `parentAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` is thrown either immediately or on `save` if a lock prevents the addition of the subtree. Implementations may differ on when this validation is performed.

      Parameters:
      `parentAbsPath` - the absolute path of a node under which (as child) the imported subtree will be built.

      `uuidBehavior` - a four-value flag that governs how incoming UUIDs are handled.

      Returns:
      an org.xml.sax.ContentHandler whose methods may be called to feed SAX events into the deserializer.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `parentAbsPath` and this implementation performs this validation immediately instead of waiting until `save`.

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if the new subtree cannot be added to the node at `parentAbsPath` due to node-type or other implementation-specific constraints, and this implementation performs this validation immediately instead of waiting until `save`.

      [`VersionException`](version/VersionException.md) - if the node at `parentAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`..

      [`LockException`](lock/LockException.md) - if a lock prevents the addition of the subtree and this implementation performs this validation immediately instead of waiting until `save`..

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
                         VersionException,
                         InvalidSerializedDataException,
                         LockException,
                         RepositoryException

      Deserializes an XML document and adds the resulting item subtree as a child of the node at parentAbsPath.
      If the incoming XML stream does not appear to be a JCR *system view* XML document then it is interpreted as a *document view* XML document.

      The tree of new items is built in the transient storage of the Session. In order to persist the new content, `save` must be called. The advantage of this through-the-session method is that (depending on what constraint checks the implementation leaves until `save`) structures that violate node type constraints can be imported, fixed and then saved. The disadvantage is that a large import will result in a large cache of pending nodes in the session. See [`Workspace.importXML(java.lang.String, java.io.InputStream, int)`](Workspace.md) for a version of this method that does not go through the `Session`.

      The flag `uuidBehavior` governs how the UUIDs of incoming (deserialized) nodes are handled. There are four options:

      - [`ImportUUIDBehavior.IMPORT_UUID_CREATE_NEW`](ImportUUIDBehavior.md): Incoming referenceable nodes are added in the same way that new node is added with `Node.addNode`. That is, they are either assigned newly created UUIDs upon addition or upon `save` (depending on the implementation). In either case, UUID collisions will not occur.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REMOVE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then the already existing node (and its subtree) is removed from wherever it may be in the workspace before the incoming node is added. Note that this can result in nodes "disappearing" from locations in the workspace that are remote from the location to which the incoming subtree is being written. Both the removal and the new addition will be persisted on `save`.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_REPLACE_EXISTING`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace, then the already-existing node is replaced by the incoming node in the same position as the existing node. Note that this may result in the incoming subtree being disaggregated and "spread around" to different locations in the workspace. In the most extreme case this behavior may result in no node at all being added as child of `parentAbsPath`. This will occur if the topmost element of the incoming XML has the same UUID as an existing node elsewhere in the workspace. The change will only be persisted on `save`.
      - [`ImportUUIDBehavior.IMPORT_UUID_COLLISION_THROW`](ImportUUIDBehavior.md): If an incoming referenceable node has the same UUID as a node already existing in the workspace then an `ItemExistsException` is thrown.

      Unlike [`Workspace.importXML(java.lang.String, java.io.InputStream, int)`](Workspace.md), this method does not necessarily enforce all node type constraints during deserialization. Those that would be immediately enforced in a normal write method (`Node.addNode`, `Node.setProperty` etc.) of this implementation cause an immediate `ConstraintViolationException` during deserialization. All other constraints are checked on `save`, just as they are in normal write operations. However, which node type constraints are enforced depends upon whether node type information in the imported data is respected, and this is an implementation-specific issue.
      A `ConstraintViolationException` will also be thrown immediately if `uuidBehavior` is set to `IMPORT_UUID_COLLISION_REMOVE_EXISTING` and an incoming node has the same UUID as the node at `parentAbsPath` or one of its ancestors.

      A `PathNotFoundException` is thrown either immediately or on `save` if no node exists at `parentAbsPath`. Implementations may differ on when this validation is performed

      A `ConstraintViolationException` is thrown either immediately or on `save` if the new subtree cannot be added to the node at parentAbsPath due to node-type or other implementation-specific constraints, and this can be determined before the first SAX event is sent. Implementations may differ on when this validation is performed.

      A `VersionException` is thrown either immediately or on `save` if the node at `parentAbsPath` is versionable and checked-in, or is non-versionable but its nearest versionable ancestor is checked-in. Implementations may differ on when this validation is performed.

      A `LockException` is thrown either immediately or on `save` if a lock prevents the addition of the subtree. Implementations may differ on when this validation is performed.

      Parameters:
      `parentAbsPath` - the absolute path of the node below which the deserialized subtree is added.

      `in` - The `Inputstream` from which the XML to be deserilaized is read.

      `uuidBehavior` - a four-value flag that governs how incoming UUIDs are handled.

      Throws:
      `java.io.IOException` - if an error during an I/O operation occurs.

      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `parentAbsPath` and this implementation performs this validation immediately instead of waiting until `save`..

      [`ItemExistsException`](ItemExistsException.md) - if deserialization would overwrite an existing item and this implementation performs this validation immediately instead of waiting until `save`..

      [`ConstraintViolationException`](nodetype/ConstraintViolationException.md) - if a node type or other implementation-specific constraint is violated that would be checked on a normal write method or if `uuidBehavior` is set to `IMPORT_UUID_COLLISION_REMOVE_EXISTING` and an incoming node has the same UUID as the node at `parentAbsPath` or one of its ancestors.

      [`VersionException`](version/VersionException.md) - if the node at `parentAbsPath` is versionable and checked-in, or its nearest versionable ancestor is checked-in and this implementation performs this validation immediately instead of waiting until `save`..

      [`InvalidSerializedDataException`](InvalidSerializedDataException.md) - if incoming stream is not a valid XML document.

      [`LockException`](lock/LockException.md) - if a lock prevents the addition of the subtree and this implementation performs this validation immediately instead of waiting until `save`..

      [`RepositoryException`](RepositoryException.md) - is another error occurs.

    <!-- -->

    - #### exportSystemView

          void exportSystemView(java.lang.String absPath,
                                ContentHandler contentHandler,
                                boolean skipBinary,
                                boolean noRecurse)
                         throws PathNotFoundException,
                                SAXException,
                                RepositoryException

      Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` into a series of SAX events by calling the methods of the supplied `org.xml.sax.ContentHandler`. The resulting XML is in the system view form. Note that `absPath` must be the path of a node, not a property.
      If `skipBinary` is true then any properties of `PropertyType.BINARY` will be serialized as if they are empty. That is, the existence of the property will be serialized, but its content will not appear in the serialized output (the `<sv:value>` element will have no content). Note that in the case of multi-value `BINARY` properties, the number of values in the property will be reflected in the serialized output, though they will all be empty. If `skipBinary` is false then the actual value(s) of each `BINARY` property is recorded using Base64 encoding.

      If `noRecurse` is true then only the node at `absPath` and its properties, but not its child nodes, are serialized. If `noRecurse` is `false` then the entire subtree rooted at `absPath` is serialized.

      If the user lacks read access to some subsection of the specified tree, that section simply does not get serialized, since, from the user's point of view, it is not there.

      The serialized output will reflect the state of the current workspace as modified by the state of this `Session`. This means that pending changes (regardless of whether they are valid according to node type constraints) and the current session-mapping of namespaces are reflected in the output.

      A `PathNotFoundException` is thrown if no node exists at `absPath`.

      A `SAXException` is thrown if an error occurs while feeding events to the `ContentHandler`.

      Parameters:
      `absPath` - The path of the root of the subtree to be serialized. This must be the path to a node, not a property

      `contentHandler` - The `org.xml.sax.ContentHandler` to which the SAX events representing the XML serialization of the subtree will be output.

      `skipBinary` - A `boolean` governing whether binary properties are to be serialized.

      `noRecurse` - A `boolean` governing whether the subtree at absPath is to be recursed.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `absPath`.

      [`SAXException`](../../org/xml/sax/SAXException.md) - if an error occurs while feeding events to the `org.xml.sax.ContentHandler`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### exportSystemView

          void exportSystemView(java.lang.String absPath,
                                java.io.OutputStream out,
                                boolean skipBinary,
                                boolean noRecurse)
                         throws java.io.IOException,
                                PathNotFoundException,
                                RepositoryException

      Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` as an XML stream and outputs it to the supplied `OutputStream`. The resulting XML is in the system view form. Note that `absPath` must be the path of a node, not a property.
      If `skipBinary` is true then any properties of `PropertyType.BINARY` will be serialized as if they are empty. That is, the existence of the property will be serialized, but its content will not appear in the serialized output (the `<sv:value>` element will have no content). Note that in the case of multi-value `BINARY` properties, the number of values in the property will be reflected in the serialized output, though they will all be empty. If `skipBinary` is false then the actual value(s) of each `BINARY` property is recorded using Base64 encoding.

      If `noRecurse` is true then only the node at `absPath` and its properties, but not its child nodes, are serialized. If `noRecurse` is `false` then the entire subtree rooted at `absPath` is serialized.

      If the user lacks read access to some subsection of the specified tree, that section simply does not get serialized, since, from the user's point of view, it is not there.

      The serialized output will reflect the state of the current workspace as modified by the state of this `Session`. This means that pending changes (regardless of whether they are valid according to node type constraints) and the current session-mapping of namespaces are reflected in the output.

      A `PathNotFoundException` is thrown if no node exists at `absPath`.

      A `SAXException` is thrown if an error occurs while feeding events to the `ContentHandler`.

      Parameters:
      `absPath` - The path of the root of the subtree to be serialized. This must be the path to a node, not a property

      `out` - The `OutputStream` to which the XML serialization of the subtree will be output.

      `skipBinary` - A `boolean` governing whether binary properties are to be serialized.

      `noRecurse` - A `boolean` governing whether the subtree at absPath is to be recursed.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `absPath`.

      `java.io.IOException` - if an error during an I/O operation occurs.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### exportDocumentView

          void exportDocumentView(java.lang.String absPath,
                                  ContentHandler contentHandler,
                                  boolean skipBinary,
                                  boolean noRecurse)
                           throws PathNotFoundException,
                                  SAXException,
                                  RepositoryException

      Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` into a series of SAX events by calling the methods of the supplied `org.xml.sax.ContentHandler`. The resulting XML is in the document view form. Note that `absPath` must be the path of a node, not a property.
      If `skipBinary` is true then any properties of `PropertyType.BINARY` will be serialized as if they are empty. That is, the existence of the property will be serialized, but its content will not appear in the serialized output (the value of the attribute will be empty). If `skipBinary` is false then the actual value(s) of each `BINARY` property is recorded using Base64 encoding.

      If `noRecurse` is true then only the node at `absPath` and its properties, but not its child nodes, are serialized. If `noRecurse` is `false` then the entire subtree rooted at `absPath` is serialized.

      If the user lacks read access to some subsection of the specified tree, that section simply does not get serialized, since, from the user's point of view, it is not there.

      The serialized output will reflect the state of the current workspace as modified by the state of this `Session`. This means that pending changes (regardless of whether they are valid according to node type constraints) and the current session-mapping of namespaces are reflected in the output.

      A `PathNotFoundException` is thrown if no node exists at `absPath`.

      A `SAXException` is thrown if an error occurs while feeding events to the `ContentHandler`.

      Parameters:
      `absPath` - The path of the root of the subtree to be serialized. This must be the path to a node, not a property

      `contentHandler` - The `org.xml.sax.ContentHandler` to which the SAX events representing the XML serialization of the subtree will be output.

      `skipBinary` - A `boolean` governing whether binary properties are to be serialized.

      `noRecurse` - A `boolean` governing whether the subtree at absPath is to be recursed.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `absPath`.

      [`SAXException`](../../org/xml/sax/SAXException.md) - if an error occurs while feeding events to the `org.xml.sax.ContentHandler`.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### exportDocumentView

          void exportDocumentView(java.lang.String absPath,
                                  java.io.OutputStream out,
                                  boolean skipBinary,
                                  boolean noRecurse)
                           throws java.io.IOException,
                                  PathNotFoundException,
                                  RepositoryException

      Serializes the node (and if `noRecurse` is `false`, the whole subtree) at `absPath` as an XML stream and outputs it to the supplied `OutputStream`. The resulting XML is in the document view form. Note that `absPath` must be the path of a node, not a property.
      If `skipBinary` is true then any properties of `PropertyType.BINARY` will be serialized as if they are empty. That is, the existence of the property will be serialized, but its content will not appear in the serialized output (the value of the attribute will be empty). If `skipBinary` is false then the actual value(s) of each `BINARY` property is recorded using Base64 encoding.

      If `noRecurse` is true then only the node at `absPath` and its properties, but not its child nodes, are serialized. If `noRecurse` is `false` then the entire subtree rooted at `absPath` is serialized.

      If the user lacks read access to some subsection of the specified tree, that section simply does not get serialized, since, from the user's point of view, it is not there.

      The serialized output will reflect the state of the current workspace as modified by the state of this `Session`. This means that pending changes (regardless of whether they are valid according to node type constraints) and the current session-mapping of namespaces are reflected in the output.

      A `PathNotFoundException` is thrown if no node exists at `absPath`.

      A `SAXException` is thrown if an error occurs while feeding events to the `ContentHandler`.

      Parameters:
      `absPath` - The path of the root of the subtree to be serialized. This must be the path to a node, not a property

      `out` - The `OutputStream` to which the XML serialization of the subtree will be output.

      `skipBinary` - A `boolean` governing whether binary properties are to be serialized.

      `noRecurse` - A `boolean` governing whether the subtree at absPath is to be recursed.

      Throws:
      [`PathNotFoundException`](PathNotFoundException.md) - if no node exists at `absPath`.

      `java.io.IOException` - if an error during an I/O operation occurs.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### setNamespacePrefix

          void setNamespacePrefix(java.lang.String prefix,
                                  java.lang.String uri)
                           throws NamespaceException,
                                  RepositoryException

      Within the scope of this session, rename a persistently registered namespace URI to the new prefix. The renaming only affects operations done through this session. To clear all renamings the client must acquire a new session.
      A prefix that is currently already mapped to some URI (either persistently in the repository `NamespaceRegistry` or transiently within this `Session`) cannot be remapped to a new URI using this method, since this would make any content stored using the old URI unreadable. An attempt to do this will throw a `NamespaceException`.

      As well, a `NamespaceException` will be thrown if an attempt is made to remap an existing namespace URI to a prefix beginning with the characters "`xml`" (in any combination of case).

      A `NamespaceException` will also be thrown if the specified uri is not among those registered in the NamespaceRegistry.

      Parameters:
      `prefix` - a string

      `uri` - a string

      Throws:
      [`NamespaceException`](NamespaceException.md) - if the specified uri is not registered or an attempt is made to remap to an illegal prefix.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getNamespacePrefixes

          java.lang.String[] getNamespacePrefixes()
                                           throws RepositoryException

      Returns all prefixes currently set for this session. This includes all those registered in the `NamespaceRegistry` but *not over-ridden* by a `Session.setNamespacePrefix`, plus those currently set locally by `Session.setNamespacePrefix`.
      Returns:
      a string array

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs

    <!-- -->

    - #### getNamespaceURI

          java.lang.String getNamespaceURI(java.lang.String prefix)
                                    throws NamespaceException,
                                           RepositoryException

      For a given prefix, returns the URI to which it is mapped as currently set in this `Session`. If the prefix is unknown, a `NamespaceException` is thrown.
      Parameters:
      `prefix` - a string

      Returns:
      a string

      Throws:
      [`NamespaceException`](NamespaceException.md) - if the prefix is unknown.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### getNamespacePrefix

          java.lang.String getNamespacePrefix(java.lang.String uri)
                                       throws NamespaceException,
                                              RepositoryException

      Returns the prefix to which the given URI is mapped
      Parameters:
      `uri` - a string

      Returns:
      a string

      Throws:
      [`NamespaceException`](NamespaceException.md) - if the URI is unknown.

      [`RepositoryException`](RepositoryException.md) - if another error occurs

    <!-- -->

    - #### logout

          void logout()

      Releases all resources associated with this `Session`. This method should be called when a `Session` is no longer needed.

    <!-- -->

    - #### isLive

          boolean isLive()

      Returns `true` if this `Session` object is usable by the client. Otherwise, returns `false`. A usable `Session` is one that is neither logged-out, timed-out nor in any other way disconnected from the repository.
      Returns:
      `true` if this `Session` is usable, `false` otherwise.

    <!-- -->

    - #### addLockToken

          void addLockToken(java.lang.String lt)

      Adds the specified lock token to this session. Holding a lock token allows the `Session` object of the lock owner to alter nodes that are locked by the lock specified by that particular lock token.
      Parameters:
      `lt` - a lock token (a string)

    <!-- -->

    - #### getLockTokens

          java.lang.String[] getLockTokens()

      Returns an array containing all lock tokens currently held by this session.
      Returns:
      an array of lock tokens (strings)

    <!-- -->

    - #### removeLockToken

          void removeLockToken(java.lang.String lt)

      Removes the specified lock token from this session.
      Parameters:
      `lt` - a lock token (a string)

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

- **[Prev Class](RepositoryException.md)**
- **[Next Class](SimpleCredentials.md)**

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
