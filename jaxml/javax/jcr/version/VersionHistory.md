Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](VersionException.md)**
- **[Next Class](VersionIterator.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**javax.jcr.version**

## **Interface VersionHistory**

- **All Superinterfaces:**
  **[Item](../Item.md), [Node](../Node.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface VersionHistory
      extends Node

  **A `VersionHistory` object wraps an `nt:versionHistory` node. It provides convenient access to version history information.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                       |
    |-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `addVersionLabel``(java.lang.String versionName, java.lang.String label, boolean moveLabel)`<br>Adds the specified label to the specified version.                                                                           |
    | [`VersionIterator`](VersionIterator.md) | `getAllVersions``()`<br>Returns an iterator over all the versions within this version history The order of the returned objects will not necessarily correspond to the order of versions in terms of the successor relation. |
    | [`Version`](Version.md)                 | `getRootVersion``()`<br>Returns the root version of this version history.                                                                                                                                                    |
    | [`Version`](Version.md)                 | `getVersion``(java.lang.String versionName)`<br>Retrieves a particular version from this version history by version name.                                                                                                    |
    | `java.lang.String`                      | `getVersionableUUID``()`<br>Returns the UUID of the versionable node for which this is the version history.                                                                                                                  |
    | [`Version`](Version.md)                 | `getVersionByLabel``(java.lang.String label)`<br>Retrieves a particular version from this version history by version label.                                                                                                  |
    | `java.lang.String[]`                    | `getVersionLabels``()`<br>Returns all version labels of the history or an empty array if there are none.                                                                                                                     |
    | `java.lang.String[]`                    | `getVersionLabels``(`[`Version`](Version.md)` version)`<br>Returns all version labels of the given `version` - empty array if none.                                                                                          |
    | `boolean`                               | `hasVersionLabel``(java.lang.String label)`<br>Returns `true` if any version in the history has the given `label`.                                                                                                           |
    | `boolean`                               | `hasVersionLabel``(`[`Version`](Version.md)` version, java.lang.String label)`<br>Returns true if the given version has the given `label`.                                                                                   |
    | `void`                                  | `removeVersion``(java.lang.String versionName)`<br>Removes the named version from this version history and automatically repairs the version graph.                                                                          |
    | `void`                                  | `removeVersionLabel``(java.lang.String label)`<br>Removes the specified label from among the labels of this version history.                                                                                                 |

    - ### Methods inherited from interface javax.jcr.[Node](../Node.md)

      [`addMixin`](../Node.md)`, `[`addNode`](../Node.md)`, `[`addNode`](../Node.md)`, `[`canAddMixin`](../Node.md)`, `[`cancelMerge`](../Node.md)`, `[`checkin`](../Node.md)`, `[`checkout`](../Node.md)`, `[`doneMerge`](../Node.md)`, `[`getBaseVersion`](../Node.md)`, `[`getCorrespondingNodePath`](../Node.md)`, `[`getDefinition`](../Node.md)`, `[`getIndex`](../Node.md)`, `[`getLock`](../Node.md)`, `[`getMixinNodeTypes`](../Node.md)`, `[`getNode`](../Node.md)`, `[`getNodes`](../Node.md)`, `[`getNodes`](../Node.md)`, `[`getPrimaryItem`](../Node.md)`, `[`getPrimaryNodeType`](../Node.md)`, `[`getProperties`](../Node.md)`, `[`getProperties`](../Node.md)`, `[`getProperty`](../Node.md)`, `[`getReferences`](../Node.md)`, `[`getUUID`](../Node.md)`, `[`getVersionHistory`](../Node.md)`, `[`hasNode`](../Node.md)`, `[`hasNodes`](../Node.md)`, `[`hasProperties`](../Node.md)`, `[`hasProperty`](../Node.md)`, `[`holdsLock`](../Node.md)`, `[`isCheckedOut`](../Node.md)`, `[`isLocked`](../Node.md)`, `[`isNodeType`](../Node.md)`, `[`lock`](../Node.md)`, `[`merge`](../Node.md)`, `[`orderBefore`](../Node.md)`, `[`removeMixin`](../Node.md)`, `[`restore`](../Node.md)`, `[`restore`](../Node.md)`, `[`restore`](../Node.md)`, `[`restoreByLabel`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`setProperty`](../Node.md)`, `[`unlock`](../Node.md)`, `[`update`](../Node.md)

    <!-- -->

    - ### Methods inherited from interface javax.jcr.[Item](../Item.md)

      [`accept`](../Item.md)`, `[`getAncestor`](../Item.md)`, `[`getDepth`](../Item.md)`, `[`getName`](../Item.md)`, `[`getParent`](../Item.md)`, `[`getPath`](../Item.md)`, `[`getSession`](../Item.md)`, `[`isModified`](../Item.md)`, `[`isNew`](../Item.md)`, `[`isNode`](../Item.md)`, `[`isSame`](../Item.md)`, `[`refresh`](../Item.md)`, `[`remove`](../Item.md)`, `[`save`](../Item.md)

<!-- -->

- - ### Method Detail

    - #### getVersionableUUID

          java.lang.String getVersionableUUID()
                                       throws RepositoryException

      Returns the UUID of the versionable node for which this is the version history.
      Returns:
      the UUID of the versionable node for which this is the version history.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getRootVersion

          Version getRootVersion()
                          throws RepositoryException

      Returns the root version of this version history.
      Returns:
      a `Version` object.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getAllVersions

          VersionIterator getAllVersions()
                                  throws RepositoryException

      Returns an iterator over all the versions within this version history The order of the returned objects will not necessarily correspond to the order of versions in terms of the successor relation. To traverse the version graph one must traverse the `jcr:successor REFERENCE` properties starting with the root version. A version history will always have at least one version, the root version. Therefore, this method will always return an iterator of at least size 1.
      Returns:
      a `VersionIterator` object.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getVersion

          Version getVersion(java.lang.String versionName)
                      throws VersionException,
                             RepositoryException

      Retrieves a particular version from this version history by version name.
      Throws a `VersionException` if the specified version is not in this version history.

      Parameters:
      `versionName` - a version name

      Returns:
      a `Version` object.

      Throws:
      [`VersionException`](VersionException.md) - if the specified version is not in this version history.

      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getVersionByLabel

          Version getVersionByLabel(java.lang.String label)
                             throws RepositoryException

      Retrieves a particular version from this version history by version label.
      Throws a `VersionException` if the specified `label` is not in this version history.

      Parameters:
      `label` - a version label

      Returns:
      a `Version` object.

      Throws:
      [`VersionException`](VersionException.md) - if the specified `label` is not in this version history.

      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### addVersionLabel

          void addVersionLabel(java.lang.String versionName,
                               java.lang.String label,
                               boolean moveLabel)
                        throws VersionException,
                               RepositoryException

      Adds the specified label to the specified version. This corresponds to adding a value to the `jcr:versionLabels` multi-value property of the `nt:version` node that represents the specified version.
      Note that this change is made immediately; there is no need to call `save`. In fact, since the the version storage is read-only with respect to normal repository methods, `save` does not even function in this context.

      Within a particular version history, a given label may appear a maximum of once. If the specified label is already assigned to a version in this history and `moveLabel` is `true` then the label is removed from its current location and added to the version with the specified `versionName`. If `moveLabel` is `false`, then an attempt to add a label that already exists in this version history will throw a `VersionException`.

      A `VersionException` is also thrown if the named version is not in this `VersionHistory` or if it is the root version (`jcr:rootVersion`) or if the `label` specified is not a valid JCR `NAME`.

      Parameters:
      `versionName` - the name of the version to which the label is to be added.

      `label` - the label to be added.

      `moveLabel` - if `true`, then if `label` is already assigned to a version in this version history, it is moved to the new version specified; if `false`, then attempting to assign an already used label will throw a `VersionException`.

      Throws:
      [`VersionException`](VersionException.md) - if an attempt is made to add an existing label to a version history and `moveLabel` is `false` or if the specifed version does not exist in this version history or if the specified version is the root version (`jcr:rootVersion`).

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### removeVersionLabel

          void removeVersionLabel(java.lang.String label)
                           throws VersionException,
                                  RepositoryException

      Removes the specified label from among the labels of this version history. This corresponds to removing a property from the `jcr:versionLabels` child node of the `nt:versionHistory` node that represents this version history.
      Note that this change is made immediately; there is no need to call `save`. In fact, since the the version storage is read-only with respect to normal repository methods, `save` does not even function in this context.

      If a label is specified that does not exist in this version history, a `VersionException` is thrown.

      Parameters:
      `label` - a version label

      Throws:
      [`VersionException`](VersionException.md) - if the name labvel does not exist in this version history.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### hasVersionLabel

          boolean hasVersionLabel(java.lang.String label)
                           throws RepositoryException

      Returns `true` if any version in the history has the given `label`.
      Parameters:
      `label` - a version label

      Returns:
      a `boolean`.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### hasVersionLabel

          boolean hasVersionLabel(Version version,
                                  java.lang.String label)
                           throws VersionException,
                                  RepositoryException

      Returns true if the given version has the given `label`.
      Parameters:
      `version` - a Version object

      `label` - a version label

      Returns:
      a `boolean`.

      Throws:
      [`VersionException`](VersionException.md) - if the specified `version` is not of this version history.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getVersionLabels

          java.lang.String[] getVersionLabels()
                                       throws RepositoryException

      Returns all version labels of the history or an empty array if there are none.
      Returns:
      a `String` array containing all the labels of the version history.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getVersionLabels

          java.lang.String[] getVersionLabels(Version version)
                                       throws VersionException,
                                              RepositoryException

      Returns all version labels of the given `version` - empty array if none. Throws a `VersionException` if the specified `version` is not in this version history.
      Parameters:
      `version` -

      Returns:
      a `String` array containing all the labels of the given version

      Throws:
      [`VersionException`](VersionException.md) - if the specified `version` is not in this version history.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### removeVersion

          void removeVersion(java.lang.String versionName)
                      throws ReferentialIntegrityException,
                             AccessDeniedException,
                             UnsupportedRepositoryOperationException,
                             VersionException,
                             RepositoryException

      Removes the named version from this version history and automatically repairs the version graph. If the version to be removed is `V`, `V`'s predecessor set is `P` and `V`'s successor set is `S`, then the version graph is repaired s follows:
      - For each member of `P`, remove the reference to `V` from its successor list and add references to each member of `S`.
      - For each member of `S`, remove the reference to `V` from its predecessor list and add references to each member of `P`.

      Note that this change is made immediately; there is no need to call `save`. In fact, since the the version storage is read-only with respect to normal repository methods, `save` does not even function in this context.
      A `ReferentialIntegrityException` will be thrown if the specified version is currently the target of a `REFERENCE` property elsewhere in the repository (not just in this workspace) and the current `Session` has read access to that `REFERENCE` property.

      An `AccessDeniedException` will be thrown if the current `Session` does not have permission to remove the specified version or if the specified version is currently the target of a `REFERENCE` property elsewhere in the repository (not just in this workspace) and the current `Session` does not have read access to that `REFERENCE` property.

      Throws an `UnsupportedRepositoryOperationException` if this operation is not supported by the implementation.

      Throws a `VersionException` if the named version is not in this `VersionHistory`.

      Parameters:
      `versionName` - the name of a version in this version history.

      Throws:
      [`ReferentialIntegrityException`](../ReferentialIntegrityException.md) - if the specified version is currently the target of a `REFERENCE` property elsewhere in the repository (not necessarily in this workspace) and the current `Session` has read access to that `REFERENCE` property.

      [`AccessDeniedException`](../AccessDeniedException.md) - if the current Session does not have permission to remove the specified version or if the specified version is currently the target of a `REFERENCE` property elsewhere in the repository (not just in this workspace) and the current `Session` does not have read access to that `REFERENCE` property.

      [`UnsupportedRepositoryOperationException`](../UnsupportedRepositoryOperationException.md) - if this operation is not supported by the implementation.

      [`VersionException`](VersionException.md) - if the named version is not in this version history.

      [`RepositoryException`](../RepositoryException.md) - if another error occurs.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](VersionException.md)**
- **[Next Class](VersionIterator.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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
