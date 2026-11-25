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
- **[Next Class](EventIterator.md)**

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

**javax.jcr.observation**

## **Interface Event**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Event

  **An event fired by the observation mechanism. Also includes constants representing the event types defined by the JCR standard. Each constant is a power of 2 so that sets of event types can be encoded as a bitmask in a `int` value.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                |
    |-------------------|--------------------------------------------------------------------------------------|
    | `static int`      | `NODE_ADDED`<br>An event of this type is generated when a node is added.             |
    | `static int`      | `NODE_REMOVED`<br>An event of this type is generated when a node is removed.         |
    | `static int`      | `PROPERTY_ADDED`<br>An event of this type is generated when a property is added.     |
    | `static int`      | `PROPERTY_CHANGED`<br>An event of this type is generated when a property is changed. |
    | `static int`      | `PROPERTY_REMOVED`<br>An event of this type is generated when a property is removed. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                   |
    |--------------------|------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getPath``()`<br>Returns the absolute path of the parent node connected with this event. |
    | `int`              | `getType``()`<br>Returns the type of this event: a constant defined by this interface.   |
    | `java.lang.String` | `getUserID``()`<br>Returns the user ID connected with this event.                        |

<!-- -->

- - ### Field Detail

    - #### NODE_ADDED

          static final int NODE_ADDED

      An event of this type is generated when a node is added.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NODE_REMOVED

          static final int NODE_REMOVED

      An event of this type is generated when a node is removed.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_ADDED

          static final int PROPERTY_ADDED

      An event of this type is generated when a property is added.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_REMOVED

          static final int PROPERTY_REMOVED

      An event of this type is generated when a property is removed.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_CHANGED

          static final int PROPERTY_CHANGED

      An event of this type is generated when a property is changed.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getType

          int getType()

      Returns the type of this event: a constant defined by this interface. One of:
      - `NODE_ADDED`
      - `NODE_REMOVED`
      - `PROPERTY_ADDED`
      - `PROPERTY_REMOVED`
      - `PROPERTY_CHANGED`

      Returns:
      the type of this event.

    <!-- -->

    - #### getPath

          java.lang.String getPath()
                            throws RepositoryException

      Returns the absolute path of the parent node connected with this event. The interpretation given to the returned path depends upon the type of the event:
      - If the event type is `NODE_ADDED` then this method returns the absolute path of the node that was added.
      - If the event type is `NODE_REMOVED` then this method returns the absolute path of the node that was removed.
      - If the event type is `PROPERTY_ADDED` then this method returns the absolute path of the property that was added.
      - If the event type is `PROPERTY_REMOVED` then this method returns the absolute path of the property that was removed.
      - If the event type is `PROPERTY_CHANGED` then this method returns the absolute path of of the changed property.

      Returns:
      the absolute path of the parent node connected with this event.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getUserID

          java.lang.String getUserID()

      Returns the user ID connected with this event. This is the string returned by getUserID of the session that caused the event.
      Returns:
      a `String`.

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
- **[Next Class](EventIterator.md)**

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
