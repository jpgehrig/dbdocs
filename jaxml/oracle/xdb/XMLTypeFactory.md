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

- **[Prev Class](XMLType.md)**
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

**oracle.xdb**

## **Class XMLTypeFactory**

- **java.lang.Object**

- - **oracle.xdb.XMLTypeFactory**

<!-- -->

- **All Implemented Interfaces:**
  **oracle.jdbc.internal.ObjectDataFactory, oracle.sql.ORADataFactory**

  ------------------------------------------------------------------------

  **
  **

      public class XMLTypeFactory
      extends java.lang.Object
      implements oracle.sql.ORADataFactory

  **The XMLTypeFactory which instantiates the XMLType classes.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                    |
    |---------------------------|----------------------------------------------------------|
    | `static int`              | `_SQL_TYPECODE`<br>A constant set to OPAQUE oracle type. |
    | `static java.lang.String` | `_SQL_TYPENAME`<br>A constant set to SYS.XMLTYPE.        |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XMLTypeFactory``()`        |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                  |
    |----------------------|-----------------------------------------------------------------------------------------|
    | `oracle.sql.ORAData` | `create``(oracle.sql.Datum d, int type)`<br>The create method of the Oradata interface. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### \_SQL_TYPECODE

          public static final int _SQL_TYPECODE

      A constant set to OPAQUE oracle type. Required for the ORADATA interface.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### \_SQL_TYPENAME

          public static final java.lang.String _SQL_TYPENAME

      A constant set to SYS.XMLTYPE. Required for the ORADATA interface.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XMLTypeFactory

          public XMLTypeFactory()

  <!-- -->

  - ### Method Detail

    - #### create

          public oracle.sql.ORAData create(oracle.sql.Datum d,
                                           int type)
                                    throws java.sql.SQLException

      The create method of the Oradata interface. This will construct a new XMLType with the specified datum and return the XMLType as an ORAData interface.
      Specified by:
      `create` in interface `oracle.sql.ORADataFactory`

      Parameters:
      `d` - the datum from which the XMLType will be constructed.

      `type` - the type of the datum (currently not used)

      Returns:
      the constructed XMLType (in form of the ORAData interface.

      Throws:
      `java.sql.SQLException`

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

- **[Prev Class](XMLType.md)**
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
