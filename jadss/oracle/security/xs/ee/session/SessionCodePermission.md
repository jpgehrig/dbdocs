Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- [Prev Class](NamespaceNotFoundException.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.security.xs.ee.session

## Class SessionCodePermission

- java.lang.Object

- - java.security.Permission

  - - oracle.security.xs.ee.session.SessionCodePermission

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.security.Guard

  ------------------------------------------------------------------------



      public final class SessionCodePermission
      extends java.security.Permission
      implements java.io.Serializable

  Permission to protect session operation to be allowed only for certain trusted code. Here is an example to grant xsee.jar to attach with any dynamic roles in opss xml based policy file:

           <grant>
                <grantee>
                     <codesource>
                         <url>file:${domain.home}/lib/xsee.jar</url>
                     </codesource>
                </grantee>
                <permissions>
                    <permission>
                        <class>oracle.security.xs.ee.session.SessionCodePermission</class>
                        <name>*</name>
                        <actions>attach</actions>
                    </permission>
                </permissions>
       </grant>



  See Also:
  [Serialized Form](../../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `ATTACH_ACTION`       |
    | `static java.lang.String` | `WILDCARD`            |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------|
    | `SessionCodePermission``(java.lang.String name, java.lang.String action)`<br>Constructor with specified name and action. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                           |
    |--------------------|------------------------------------------------------------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object obj)`<br>Checks two Permission objects for equality.                                  |
    | `java.lang.String` | `getActions``()`<br>Returns the actions of this Permission object.                                               |
    | `int`              | `hashCode``()`<br>Returns the hash code value of this Permission object.                                         |
    | `boolean`          | `implies``(java.security.Permission p)`<br>Checks to see if the current permission implies the given permission. |
    | `java.lang.String` | `toString``()`<br>Returns a string description of this Permission object.                                        |

    - ### Methods inherited from class java.security.Permission

      `checkGuard, getName, newPermissionCollection`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, finalize, getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ATTACH_ACTION

          public static java.lang.String ATTACH_ACTION

    <!-- -->

    - #### WILDCARD

          public static java.lang.String WILDCARD

  <!-- -->

  - ### Constructor Detail

    - #### SessionCodePermission

          public SessionCodePermission(java.lang.String name,
                                       java.lang.String action)

      Constructor with specified name and action.
      Parameters:
      `name` - name of the Permission object being created.

      `action` - action of the Permission object being created.

  <!-- -->

  - ### Method Detail

    - #### implies

          public boolean implies(java.security.Permission p)

      Checks to see if the current permission implies the given permission. The two parameters of the SessionCodePermission must both imply, then return true.
      Specified by:
      `implies` in class `java.security.Permission`

      Parameters:
      `p` - the given SessionCodePermission

      Returns:
      true if the current permission implies the given permission

    <!-- -->

    - #### getActions

          public java.lang.String getActions()

      Returns the actions of this Permission object.
      Specified by:
      `getActions` in class `java.security.Permission`

      Returns:
      the actions of this object.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Returns a string description of this Permission object.
      Overrides:
      `toString` in class `java.security.Permission`

      Returns:
      the description of this object.

    <!-- -->

    - #### hashCode

          public int hashCode()

      Returns the hash code value of this Permission object.
      Specified by:
      `hashCode` in class `java.security.Permission`

      Returns:
      a hash code value for this object.

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Checks two Permission objects for equality. Checks that *obj*'s class is the same as this object's class and has the same name and action as this object.
      Specified by:
      `equals` in class `java.security.Permission`

      Parameters:
      `obj` - the object we are testing for equality with this object.

      Returns:
      true if *obj* is a SessioncodePermission, and has the same name and action as this SessioncodePermission object, false otherwise.

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- [Prev Class](NamespaceNotFoundException.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
