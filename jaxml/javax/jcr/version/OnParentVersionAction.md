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

- **Prev Class**
- **[Next Class](Version.md)**

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

## **Class OnParentVersionAction**

- **java.lang.Object**

- - **javax.jcr.version.OnParentVersionAction**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class OnParentVersionAction
      extends java.lang.Object

  **The possible actions specified by the `onParentVersion` attribute in a property definition within a node type definition.**
  **This interface defines the following actions:**

  - **`COPY`**
  - **`VERSION`**
  - **`INITIALIZE`**
  - **`COMPUTE`**
  - **`IGNORE`**
  - **`ABORT`**

  **Every item (node or property) in the repository has a status indicator that governs what happens to that item when its parent node is versioned. This status is defined by the `onParentVersion` attribute in the `PropertyDefinition` or `NodeDefinition` that applies to the item in question.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                       |
    |---------------------------|---------------------------------------------------------------------------------------------|
    | `static int`              | `ABORT`                                                                                     |
    | `static java.lang.String` | `ACTIONNAME_ABORT`                                                                          |
    | `static java.lang.String` | `ACTIONNAME_COMPUTE`                                                                        |
    | `static java.lang.String` | `ACTIONNAME_COPY`<br>The names of the defined on-version actions, as used in serialization. |
    | `static java.lang.String` | `ACTIONNAME_IGNORE`                                                                         |
    | `static java.lang.String` | `ACTIONNAME_INITIALIZE`                                                                     |
    | `static java.lang.String` | `ACTIONNAME_VERSION`                                                                        |
    | `static int`              | `COMPUTE`                                                                                   |
    | `static int`              | `COPY`<br>The action constants.                                                             |
    | `static int`              | `IGNORE`                                                                                    |
    | `static int`              | `INITIALIZE`                                                                                |
    | `static int`              | `VERSION`                                                                                   |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                           |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `nameFromValue``(int action)`<br>Returns the name of the specified `action`, as used in serialization.                           |
    | `static int`              | `valueFromName``(java.lang.String name)`<br>Returns the numeric constant value of the on-version action with the specified name. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### COPY

          public static final int COPY

      The action constants.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### VERSION

          public static final int VERSION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### INITIALIZE

          public static final int INITIALIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPUTE

          public static final int COMPUTE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### IGNORE

          public static final int IGNORE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ABORT

          public static final int ABORT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ACTIONNAME_COPY

          public static final java.lang.String ACTIONNAME_COPY

      The names of the defined on-version actions, as used in serialization.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ACTIONNAME_VERSION

          public static final java.lang.String ACTIONNAME_VERSION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ACTIONNAME_INITIALIZE

          public static final java.lang.String ACTIONNAME_INITIALIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ACTIONNAME_COMPUTE

          public static final java.lang.String ACTIONNAME_COMPUTE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ACTIONNAME_IGNORE

          public static final java.lang.String ACTIONNAME_IGNORE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ACTIONNAME_ABORT

          public static final java.lang.String ACTIONNAME_ABORT

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### nameFromValue

          public static java.lang.String nameFromValue(int action)

      Returns the name of the specified `action`, as used in serialization.
      Parameters:
      `action` - the on-version action

      Returns:
      the name of the specified `action`

      Throws:
      `java.lang.IllegalArgumentException` - if `action` is not a valid on-version action.

    <!-- -->

    - #### valueFromName

          public static int valueFromName(java.lang.String name)

      Returns the numeric constant value of the on-version action with the specified name.
      Parameters:
      `name` - the name of the on-version action

      Returns:
      the numeric constant value

      Throws:
      `java.lang.IllegalArgumentException` - if `name` is not a valid on-version action name.

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

- **Prev Class**
- **[Next Class](Version.md)**

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
