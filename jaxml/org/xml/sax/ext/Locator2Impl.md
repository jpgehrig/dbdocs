Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](Locator2.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.xml.sax.ext**

## **Class Locator2Impl**

- **java.lang.Object**

- - **[org.xml.sax.helpers.LocatorImpl](../helpers/LocatorImpl.md)**

  - - **org.xml.sax.ext.Locator2Impl**

<!-- -->

- **All Implemented Interfaces:**
  **[Locator2](Locator2.md), [Locator](../Locator.md)**

  ------------------------------------------------------------------------

  **
  **

      public class Locator2Impl
      extends LocatorImpl
      implements Locator2

  **SAX2 extension helper for holding additional Entity information, implementing the [`Locator2`](Locator2.md) interface.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This is not part of core-only SAX2 distributions.**

  **Since:**
  **SAX 2.0.2**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                            |
    |--------------------------------------------------------------------------------------------------------|
    | `Locator2Impl``()`<br>Construct a new, empty Locator2Impl object.                                      |
    | `Locator2Impl``(`[`Locator`](../Locator.md)` locator)`<br>Copy an existing Locator or Locator2 object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                            |
    |--------------------|---------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getEncoding``()`<br>Returns the current value of the encoding property.                          |
    | `java.lang.String` | `getXMLVersion``()`<br>Returns the current value of the version property.                         |
    | `void`             | `setEncoding``(java.lang.String encoding)`<br>Assigns the current value of the encoding property. |
    | `void`             | `setXMLVersion``(java.lang.String version)`<br>Assigns the current value of the version property. |

    - ### Methods inherited from class org.xml.sax.helpers.[LocatorImpl](../helpers/LocatorImpl.md)

      [`getColumnNumber`](../helpers/LocatorImpl.md)`, `[`getLineNumber`](../helpers/LocatorImpl.md)`, `[`getPublicId`](../helpers/LocatorImpl.md)`, `[`getSystemId`](../helpers/LocatorImpl.md)`, `[`setColumnNumber`](../helpers/LocatorImpl.md)`, `[`setLineNumber`](../helpers/LocatorImpl.md)`, `[`setPublicId`](../helpers/LocatorImpl.md)`, `[`setSystemId`](../helpers/LocatorImpl.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[Locator](../Locator.md)

      [`getColumnNumber`](../Locator.md)`, `[`getLineNumber`](../Locator.md)`, `[`getPublicId`](../Locator.md)`, `[`getSystemId`](../Locator.md)

<!-- -->

- - ### Constructor Detail

    - #### Locator2Impl

          public Locator2Impl()

      Construct a new, empty Locator2Impl object. This will not normally be useful, since the main purpose of this class is to make a snapshot of an existing Locator.

    <!-- -->

    - #### Locator2Impl

          public Locator2Impl(Locator locator)

      Copy an existing Locator or Locator2 object. If the object implements Locator2, values of the *encoding* and *version*strings are copied, otherwise they set to *null*.
      Parameters:
      `locator` - The existing Locator object.

  <!-- -->

  - ### Method Detail

    - #### getXMLVersion

          public java.lang.String getXMLVersion()

      Returns the current value of the version property.
      Specified by:
      [`getXMLVersion`](Locator2.md) in interface [`Locator2`](Locator2.md)

      Returns:
      Identifier for the XML version being used to interpret the entity's text, or null if that information is not yet available in the current parsing state.

      See Also:
      `setXMLVersion(java.lang.String)`

    <!-- -->

    - #### getEncoding

          public java.lang.String getEncoding()

      Returns the current value of the encoding property.
      Specified by:
      [`getEncoding`](Locator2.md) in interface [`Locator2`](Locator2.md)

      Returns:
      Name of the character encoding being used to interpret \* the entity's text, or null if this was not provided for a \* character stream passed through an InputSource or is otherwise not yet available in the current parsing state.

      See Also:
      `setEncoding(java.lang.String)`

    <!-- -->

    - #### setXMLVersion

          public void setXMLVersion(java.lang.String version)

      Assigns the current value of the version property.
      Parameters:
      `version` - the new "version" value

      See Also:
      `getXMLVersion()`

    <!-- -->

    - #### setEncoding

          public void setEncoding(java.lang.String encoding)

      Assigns the current value of the encoding property.
      Parameters:
      `encoding` - the new "encoding" value

      See Also:
      `getEncoding()`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](Locator2.md)**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
