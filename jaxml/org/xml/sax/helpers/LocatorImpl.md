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

- **[Prev Class](DefaultHandler.md)**
- **[Next Class](NamespaceSupport.md)**

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

**org.xml.sax.helpers**

## **Class LocatorImpl**

- **java.lang.Object**

- - **org.xml.sax.helpers.LocatorImpl**

<!-- -->

- **All Implemented Interfaces:**
  **[Locator](../Locator.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[Locator2Impl](../ext/Locator2Impl.md)**

  ------------------------------------------------------------------------

  **
  **

      public class LocatorImpl
      extends java.lang.Object
      implements Locator

  **Provide an optional convenience implementation of Locator.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class is available mainly for application writers, who can use it to make a persistent snapshot of a locator at any point during a document parse:**

       Locator locator;
       Locator startloc;

       public void setLocator (Locator locator)
       {
               // note the locator
         this.locator = locator;
       }

       public void startDocument ()
       {
               // save the location of the start of the document
               // for future use.
         Locator startloc = new LocatorImpl(locator);
       }

  **Normally, parser writers will not use this class, since it is more efficient to provide location information only when requested, rather than constantly updating a Locator object.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`Locator`](../Locator.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                |
    |----------------------------------------------------------------------------|
    | `LocatorImpl``()`<br>Zero-argument constructor.                            |
    | `LocatorImpl``(`[`Locator`](../Locator.md)` locator)`<br>Copy constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                     |
    |--------------------|--------------------------------------------------------------------------------------------|
    | `int`              | `getColumnNumber``()`<br>Return the saved column number (1-based).                         |
    | `int`              | `getLineNumber``()`<br>Return the saved line number (1-based).                             |
    | `java.lang.String` | `getPublicId``()`<br>Return the saved public identifier.                                   |
    | `java.lang.String` | `getSystemId``()`<br>Return the saved system identifier.                                   |
    | `void`             | `setColumnNumber``(int columnNumber)`<br>Set the column number for this locator (1-based). |
    | `void`             | `setLineNumber``(int lineNumber)`<br>Set the line number for this locator (1-based).       |
    | `void`             | `setPublicId``(java.lang.String publicId)`<br>Set the public identifier for this locator.  |
    | `void`             | `setSystemId``(java.lang.String systemId)`<br>Set the system identifier for this locator.  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LocatorImpl

          public LocatorImpl()

      Zero-argument constructor.
      This will not normally be useful, since the main purpose of this class is to make a snapshot of an existing Locator.

    <!-- -->

    - #### LocatorImpl

          public LocatorImpl(Locator locator)

      Copy constructor.
      Create a persistent copy of the current state of a locator. When the original locator changes, this copy will still keep the original values (and it can be used outside the scope of DocumentHandler methods).

      Parameters:
      `locator` - The locator to copy.

  <!-- -->

  - ### Method Detail

    - #### getPublicId

          public java.lang.String getPublicId()

      Return the saved public identifier.
      Specified by:
      [`getPublicId`](../Locator.md) in interface [`Locator`](../Locator.md)

      Returns:
      The public identifier as a string, or null if none is available.

      See Also:
      [`Locator.getPublicId()`](../Locator.md), `setPublicId(java.lang.String)`

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Return the saved system identifier.
      Specified by:
      [`getSystemId`](../Locator.md) in interface [`Locator`](../Locator.md)

      Returns:
      The system identifier as a string, or null if none is available.

      See Also:
      [`Locator.getSystemId()`](../Locator.md), `setSystemId(java.lang.String)`

    <!-- -->

    - #### getLineNumber

          public int getLineNumber()

      Return the saved line number (1-based).
      Specified by:
      [`getLineNumber`](../Locator.md) in interface [`Locator`](../Locator.md)

      Returns:
      The line number as an integer, or -1 if none is available.

      See Also:
      [`Locator.getLineNumber()`](../Locator.md), `setLineNumber(int)`

    <!-- -->

    - #### getColumnNumber

          public int getColumnNumber()

      Return the saved column number (1-based).
      Specified by:
      [`getColumnNumber`](../Locator.md) in interface [`Locator`](../Locator.md)

      Returns:
      The column number as an integer, or -1 if none is available.

      See Also:
      [`Locator.getColumnNumber()`](../Locator.md), `setColumnNumber(int)`

    <!-- -->

    - #### setPublicId

          public void setPublicId(java.lang.String publicId)

      Set the public identifier for this locator.
      Parameters:
      `publicId` - The new public identifier, or null if none is available.

      See Also:
      `getPublicId()`

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String systemId)

      Set the system identifier for this locator.
      Parameters:
      `systemId` - The new system identifier, or null if none is available.

      See Also:
      `getSystemId()`

    <!-- -->

    - #### setLineNumber

          public void setLineNumber(int lineNumber)

      Set the line number for this locator (1-based).
      Parameters:
      `lineNumber` - The line number, or -1 if none is available.

      See Also:
      `getLineNumber()`

    <!-- -->

    - #### setColumnNumber

          public void setColumnNumber(int columnNumber)

      Set the column number for this locator (1-based).
      Parameters:
      `columnNumber` - The column number, or -1 if none is available.

      See Also:
      `getColumnNumber()`

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

- **[Prev Class](DefaultHandler.md)**
- **[Next Class](NamespaceSupport.md)**

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
