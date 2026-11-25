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

- **[Prev Class](XMLReaderAdapter.md)**
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

**org.xml.sax.helpers**

## **Class XMLReaderFactory**

- **java.lang.Object**

- - **org.xml.sax.helpers.XMLReaderFactory**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class XMLReaderFactory
      extends java.lang.Object

  **Factory for creating an XML reader.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **This class contains static methods for creating an XML reader from an explicit class name, or for creating an XML reader based on the value of the `org.xml.sax.driver` system property:**

       try {
         XMLReader myReader = XMLReaderFactory.createXMLReader();
       } catch (SAXException e) {
         System.err.println(e.getMessage());
       }


  **Note that these methods will not be usable in environments where system properties are not accessible or where the application or applet is not permitted to load classes dynamically.**

  ****Note to implementors:** SAX implementations in specialized environments may replace this class with a different one optimized for the environment, as long as its method signatures remain the same.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`XMLReader`](../XMLReader.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------|
    | `static `[`XMLReader`](../XMLReader.md) | `createXMLReader``()`<br>Attempt to create an XML reader from a system property.                      |
    | `static `[`XMLReader`](../XMLReader.md) | `createXMLReader``(java.lang.String className)`<br>Attempt to create an XML reader from a class name. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### createXMLReader

          public static XMLReader createXMLReader()
                                           throws SAXException

      Attempt to create an XML reader from a system property.
      This method uses the value of the system property "org.xml.sax.driver" as the full name of a Java class and tries to instantiate that class as a SAX2 XMLReader.

      Note that many Java interpreters allow system properties to be specified on the command line.

      Returns:
      A new XMLReader.

      Throws:
      [`SAXException`](../SAXException.md) - If the value of the "org.xml.sax.driver" system property is null, or if the class cannot be loaded and instantiated.

      See Also:
      `createXMLReader(java.lang.String)`

    <!-- -->

    - #### createXMLReader

          public static XMLReader createXMLReader(java.lang.String className)
                                           throws SAXException

      Attempt to create an XML reader from a class name.
      Given a class name, this method attempts to load and instantiate the class as an XML reader.

      Returns:
      A new XML reader.

      Throws:
      [`SAXException`](../SAXException.md) - If the class cannot be loaded, instantiated, and cast to XMLReader.

      See Also:
      `createXMLReader()`

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

- **[Prev Class](XMLReaderAdapter.md)**
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
