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

- **[Prev Class](Credentials.md)**
- **[Next Class](InvalidItemStateException.md)**

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

## **Interface ImportUUIDBehavior**

-

  ------------------------------------------------------------------------

  **
  **

      public interface ImportUUIDBehavior

  **The possible actions specified by the `uuidBehavior` parameter in [`Workspace.importXML(java.lang.String, java.io.InputStream, int)`](Workspace.md), [`Session.importXML(java.lang.String, java.io.InputStream, int)`](Session.md), [`Workspace.getImportContentHandler(java.lang.String, int)`](Workspace.md) and [`Session.getImportContentHandler(java.lang.String, int)`](Session.md).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                     |
    |-------------------|-------------------------------------------|
    | `static int`      | `IMPORT_UUID_COLLISION_REMOVE_EXISTING`   |
    | `static int`      | `IMPORT_UUID_COLLISION_REPLACE_EXISTING`  |
    | `static int`      | `IMPORT_UUID_COLLISION_THROW`             |
    | `static int`      | `IMPORT_UUID_CREATE_NEW`                  |

<!-- -->

-
  -

    ### **Field Detail**

    - #### **IMPORT_UUID_CREATE_NEW**

          static final int IMPORT_UUID_CREATE_NEW

      **See Also:**
      **[Constant Field Values](../../constant-values.md)**

    - #### **IMPORT_UUID_COLLISION_REMOVE_EXISTING**

          static final int IMPORT_UUID_COLLISION_REMOVE_EXISTING

      **See Also:**
      **[Constant Field Values](../../constant-values.md)**

    - #### **IMPORT_UUID_COLLISION_REPLACE_EXISTING**

          static final int IMPORT_UUID_COLLISION_REPLACE_EXISTING

      **See Also:**
      **[Constant Field Values](../../constant-values.md)**

    - #### **IMPORT_UUID_COLLISION_THROW**

          static final int IMPORT_UUID_COLLISION_THROW

      **See Also:**
      **[Constant Field Values](../../constant-values.md)**

**Skip navigation links**

- **[Overview](../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../deprecated-list.md)**
- **[Index](../../index-all.md)**
- **[Help](../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](Credentials.md)**
- **[Next Class](InvalidItemStateException.md)**

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
