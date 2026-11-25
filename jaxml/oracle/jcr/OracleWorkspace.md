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

- **[Prev Class](OracleSession.md)**
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

**oracle.jcr**

## **Interface OracleWorkspace**

- **All Superinterfaces:**
  **[Workspace](../../javax/jcr/Workspace.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleWorkspace is a JCR session's view of a repository workspace.**
  **
  **

      public interface OracleWorkspace
      extends Workspace

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------|
    | `void`            | `commit``()`<br>Deprecated. <br>Explicitly commits the in-progress local transaction.      |
    | `void`            | `rollback``()`<br>Deprecated. <br>Explicitly rolls back the in-progress local transaction. |

    - ### Methods inherited from interface javax.jcr.[Workspace](../../javax/jcr/Workspace.md)

      [`clone`](../../javax/jcr/Workspace.md)`, `[`copy`](../../javax/jcr/Workspace.md)`, `[`copy`](../../javax/jcr/Workspace.md)`, `[`getAccessibleWorkspaceNames`](../../javax/jcr/Workspace.md)`, `[`getImportContentHandler`](../../javax/jcr/Workspace.md)`, `[`getName`](../../javax/jcr/Workspace.md)`, `[`getNamespaceRegistry`](../../javax/jcr/Workspace.md)`, `[`getNodeTypeManager`](../../javax/jcr/Workspace.md)`, `[`getObservationManager`](../../javax/jcr/Workspace.md)`, `[`getQueryManager`](../../javax/jcr/Workspace.md)`, `[`getSession`](../../javax/jcr/Workspace.md)`, `[`importXML`](../../javax/jcr/Workspace.md)`, `[`move`](../../javax/jcr/Workspace.md)`, `[`restore`](../../javax/jcr/Workspace.md)

<!-- -->

- - ### Method Detail

    - #### commit

          void commit()
               throws RepositoryException

      Deprecated. 
      Explicitly commits the in-progress local transaction.
      Throws:
      [`RepositoryException`](../../javax/jcr/RepositoryException.md) - if the operation fails

    <!-- -->

    - #### rollback

          void rollback()
                 throws RepositoryException

      Deprecated. 
      Explicitly rolls back the in-progress local transaction.
      Throws:
      [`RepositoryException`](../../javax/jcr/RepositoryException.md) - if the operation fails

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

- **[Prev Class](OracleSession.md)**
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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
