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

- **[Prev Class](Session.md)**
- **[Next Class](UnsupportedRepositoryOperationException.md)**

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

## **Class SimpleCredentials**

- **java.lang.Object**

- - **javax.jcr.SimpleCredentials**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, [Credentials](Credentials.md)**

  ------------------------------------------------------------------------

  **
  **

      public final class SimpleCredentials
      extends java.lang.Object
      implements Credentials

  **`SimpleCredentials` implements the `Credentials` interface and represents simple user ID/password credentials.**
  **See Also:**
  **[Serialized Form](../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                               |
    |-------------------------------------------------------------------------------------------------------------------------------------------|
    | `SimpleCredentials``(java.lang.String userID, char[] password)`<br>Create a new `SimpleCredentials` object, given a user ID and password. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                                                  |
    |----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`   | `getAttribute``(java.lang.String name)`<br>Returns the value of the named attribute as an `Object`, or `null` if no attribute of the given name exists. |
    | `java.lang.String[]` | `getAttributeNames``()`<br>Returns the names of the attributes available to this credentials instance.                                                  |
    | `char[]`             | `getPassword``()`<br>Returns the user password.                                                                                                         |
    | `java.lang.String`   | `getUserID``()`<br>Returns the user ID.                                                                                                                 |
    | `void`               | `removeAttribute``(java.lang.String name)`<br>Removes an attribute from this credentials instance.                                                      |
    | `void`               | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Stores an attribute in this credentials instance.                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SimpleCredentials

          public SimpleCredentials(java.lang.String userID,
                                   char[] password)

      Create a new `SimpleCredentials` object, given a user ID and password.
      Note that the given password is cloned before it is stored in the new `SimpleCredentials` object. This should avoid the risk of having unnecessary references to password data lying around in memory.

      Parameters:
      `userID` - the user ID

      `password` - the user's password

  <!-- -->

  - ### Method Detail

    - #### getPassword

          public char[] getPassword()

      Returns the user password.
      Note that this method returns a reference to the password. It is the caller's responsibility to zero out the password information after it is no longer needed.

      Returns:
      the password

    <!-- -->

    - #### getUserID

          public java.lang.String getUserID()

      Returns the user ID.
      Returns:
      the user ID.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)

      Stores an attribute in this credentials instance.
      Parameters:
      `name` - a `String` specifying the name of the attribute

      `value` - the `Object` to be stored

    <!-- -->

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.String name)

      Returns the value of the named attribute as an `Object`, or `null` if no attribute of the given name exists.
      Parameters:
      `name` - a `String` specifying the name of the attribute

      Returns:
      an `Object` containing the value of the attribute, or `null` if the attribute does not exist

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(java.lang.String name)

      Removes an attribute from this credentials instance.
      Parameters:
      `name` - a `String` specifying the name of the attribute to remove

    <!-- -->

    - #### getAttributeNames

          public java.lang.String[] getAttributeNames()

      Returns the names of the attributes available to this credentials instance. This method returns an empty array if the credentials instance has no attributes available to it.
      Returns:
      a string array containing the names of the stored attributes

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

- **[Prev Class](Session.md)**
- **[Next Class](UnsupportedRepositoryOperationException.md)**

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
