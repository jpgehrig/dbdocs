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

- [Prev Class](AccessDeniedException.md)
- [Next Class](AttributeValue.md)

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

## Class AclId

- java.lang.Object

- - oracle.security.xs.AclId

<!-- -->

-

  ------------------------------------------------------------------------



      public class AclId
      extends java.lang.Object

  This class represents multiple ACL IDs in either long or raw form.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                |
    |------------------------------------------------------------------------------------------------------------|
    | `AclId``(byte[] raw)`<br>Constructs an AclId using the raw binary returned by the ora_get_aclids operator. |
    | `AclId``(java.util.List<java.lang.Long> ids)`<br>Constructs an AclId with internal ACL IDs of type long.   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                 |
    |-------------------|--------------------------------------------------------|
    | `long[]`          | `getIds``()`<br>Returns internal ACL IDs of type long. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AclId

          public AclId(byte[] raw)

      Constructs an AclId using the raw binary returned by the ora_get_aclids operator.
      Parameters:
      `raw` - list of ACL IDs in raw format

    <!-- -->

    - #### AclId

          public AclId(java.util.List<java.lang.Long> ids)

      Constructs an AclId with internal ACL IDs of type long. This is for advanced users only.
      Parameters:
      `ids` - list of ACL IDs

  <!-- -->

  - ### Method Detail

    - #### getIds

          public long[] getIds()

      Returns internal ACL IDs of type long.
      Returns:
      ACL ID

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

- [Prev Class](AccessDeniedException.md)
- [Next Class](AttributeValue.md)

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
