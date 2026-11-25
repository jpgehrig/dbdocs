Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](Session.md)
- [Next Class](SessionNamespace.ATTR_EVENT_TYPE.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.security.xs

## Interface SessionNamespace

-

  ------------------------------------------------------------------------



      public interface SessionNamespace

  This interface represents a set of name/value (`SessionNamespaceAttibute`) pairs associated with `Session`, which are commonly used to record application state, user profile, and so on.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                                       |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`SessionNamespace.ATTR_EVENT_TYPE`](SessionNamespace.ATTR_EVENT_TYPE.md)<br>The list of possible events an attribute can have. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                     | Method and Description                                                                                                                                                                                                                                       |
    |---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`SessionNamespaceAttribute`](SessionNamespaceAttribute.md)                           | `createAttribute``(java.lang.String name, java.lang.String value)`<br>Creates a new attribute in the namespace with the specified name and value.                                                                                                            |
    | [`SessionNamespaceAttribute`](SessionNamespaceAttribute.md)                           | `createAttribute``(java.lang.String name, java.lang.String value, java.util.List<`[`SessionNamespace.ATTR_EVENT_TYPE`](SessionNamespace.ATTR_EVENT_TYPE.md)`> event)`<br>Creates a new attribute in the namespace with the specified name, value, and event. |
    | `void`                                                                                | `deleteAttribute``(java.lang.String name)`<br>Deletes the specified attribute                                                                                                                                                                                |
    | [`SessionNamespaceAttribute`](SessionNamespaceAttribute.md)                           | `getAttribute``(java.lang.String name)`<br>" Returns the specified attribute."                                                                                                                                                                               |
    | `java.util.Collection<`[`SessionNamespaceAttribute`](SessionNamespaceAttribute.md)`>` | `getAttributes``()`<br>Returns a collection of the attribute names in the namespace.                                                                                                                                                                         |
    | `java.lang.String`                                                                    | `getName``()`<br>Returns the name of the namespace                                                                                                                                                                                                           |
    | [`SessionNamespaceAttribute`](SessionNamespaceAttribute.md)                           | `resetAttribute``(java.lang.String name)`<br>Resets the specified attribute in the namespace to its default value.                                                                                                                                           |
    | [`SessionNamespaceAttribute`](SessionNamespaceAttribute.md)                           | `setAttribute``(java.lang.String name, java.lang.String value)`<br>Sets the attribute for a session namespace with the specified name and value                                                                                                              |
    | `java.lang.String`                                                                    | `toString``()`<br>Returns a string representation of the namespace                                                                                                                                                                                           |

<!-- -->

- - ### Method Detail

    - #### getAttributes

          java.util.Collection<SessionNamespaceAttribute> getAttributes()

      Returns a collection of the attribute names in the namespace.
      Returns:
      An enumeration of of attribute objects

    <!-- -->

    - #### createAttribute

          SessionNamespaceAttribute createAttribute(java.lang.String name,
                                                    java.lang.String value)
                                             throws java.sql.SQLException,
                                                    SessionNamespaceException,
                                                    AccessDeniedException,
                                                    XSException,
                                                    InvalidXSAttributeException,
                                                    NotAttachedException

      Creates a new attribute in the namespace with the specified name and value.
      Parameters:
      `name` - name of the attribute

      `value` - value of the attribute

      Returns:
      the newly created attribute

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the current user does not have the privilege to attach to the session

      [`XSException`](XSException.md) - when a generic error is detected

      [`SessionNamespaceException`](SessionNamespaceException.md) - when the attibute name is invalid

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute value is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### createAttribute

          SessionNamespaceAttribute createAttribute(java.lang.String name,
                                                    java.lang.String value,
                                                    java.util.List<SessionNamespace.ATTR_EVENT_TYPE> event)
                                             throws java.sql.SQLException,
                                                    SessionNamespaceException,
                                                    AccessDeniedException,
                                                    XSException,
                                                    InvalidXSAttributeException,
                                                    NotAttachedException

      Creates a new attribute in the namespace with the specified name, value, and event.
      Parameters:
      `name` - name of the attribute

      `value` - value of the attribute

      `event` - event registration of the attribute

      Returns:
      the newly created attribute

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the current user does not have the privilege to attach to the session

      [`XSException`](XSException.md) - when a generic error is detected

      [`SessionNamespaceException`](SessionNamespaceException.md) - when the attibute name is invalid

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute value is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### resetAttribute

          SessionNamespaceAttribute resetAttribute(java.lang.String name)
                                            throws java.sql.SQLException,
                                                   AccessDeniedException,
                                                   XSException,
                                                   InvalidXSAttributeException,
                                                   NotAttachedException

      Resets the specified attribute in the namespace to its default value.
      Parameters:
      `name` - name of the attribute

      Returns:
      the attribute that has been reset

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the current user does not have the privilege to reset the attribute

      [`XSException`](XSException.md) - when a generic error is detected

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### setAttribute

          SessionNamespaceAttribute setAttribute(java.lang.String name,
                                                 java.lang.String value)
                                          throws java.sql.SQLException,
                                                 SessionNamespaceException,
                                                 AccessDeniedException,
                                                 XSException,
                                                 InvalidXSAttributeException,
                                                 NotAttachedException

      Sets the attribute for a session namespace with the specified name and value
      Parameters:
      `name` - name of the attribute

      `value` - value of the attribute

      Returns:
      SessionNamespaceAttribute attribute object whose value is set

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the current user does not have the privilege to set the attribute

      [`XSException`](XSException.md) - when a generic error is detected

      [`SessionNamespaceException`](SessionNamespaceException.md) - when the namespace is invalid

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### getAttribute

          SessionNamespaceAttribute getAttribute(java.lang.String name)
                                          throws java.sql.SQLException,
                                                 AccessDeniedException,
                                                 XSException,
                                                 InvalidXSAttributeException,
                                                 NotAttachedException

      " Returns the specified attribute."
      Parameters:
      `name` - the name of the attribute in the namespace

      Returns:
      the specified session attribute (null if not found)

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the current user does not have the privilege to get the attribute

      [`XSException`](XSException.md) - when a generic error is detected

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### deleteAttribute

          void deleteAttribute(java.lang.String name)
                        throws java.sql.SQLException,
                               AccessDeniedException,
                               XSException,
                               InvalidXSAttributeException,
                               NotAttachedException

      Deletes the specified attribute
      Parameters:
      `name` - name of the attribute

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the current user does not have the privilege to delete the attribute

      [`XSException`](XSException.md) - when a generic error is detected

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### getName

          java.lang.String getName()

      Returns the name of the namespace
      Returns:
      The String corresponding to the name for the namespace

    <!-- -->

    - #### toString

          java.lang.String toString()

      Returns a string representation of the namespace
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      a string representation of the namespace

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](Session.md)
- [Next Class](SessionNamespace.ATTR_EVENT_TYPE.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
