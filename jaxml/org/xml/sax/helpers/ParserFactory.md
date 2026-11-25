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

- **[Prev Class](ParserAdapter.md)**
- **[Next Class](XMLFilterImpl.md)**

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

## **Class ParserFactory**

- **java.lang.Object**

- - **org.xml.sax.helpers.ParserFactory**

<!-- -->

-

  ------------------------------------------------------------------------

  **Deprecated. **
  **This class works with the deprecated [`Parser`](../Parser.md) interface.**
  **
  **

      public class ParserFactory
      extends java.lang.Object

  **Java-specific class for dynamically loading SAX parsers.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  ****Note:** This class is designed to work with the now-deprecated SAX1 [`Parser`](../Parser.md) class. SAX2 applications should use [`XMLReaderFactory`](XMLReaderFactory.md) instead.**

  **ParserFactory is not part of the platform-independent definition of SAX; it is an additional convenience class designed specifically for Java XML application writers. SAX applications can use the static methods in this class to allocate a SAX parser dynamically at run-time based either on the value of the \`org.xml.sax.parser' system property or on a string containing the class name.**

  **Note that the application still requires an XML parser that implements SAX1.**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`Parser`](../Parser.md), `Class`**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                 | Method and Description                                                                                                      |
    |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | `static `[`Parser`](../Parser.md) | `makeParser``()`<br>Deprecated. <br>Create a new SAX parser using the \`org.xml.sax.parser' system property.                |
    | `static `[`Parser`](../Parser.md) | `makeParser``(java.lang.String className)`<br>Deprecated. <br>Create a new SAX parser object using the class name provided. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### makeParser

          public static Parser makeParser()
                                   throws java.lang.ClassNotFoundException,
                                          java.lang.IllegalAccessException,
                                          java.lang.InstantiationException,
                                          java.lang.NullPointerException,
                                          java.lang.ClassCastException

      Deprecated. 
      Create a new SAX parser using the \`org.xml.sax.parser' system property.
      The named class must exist and must implement the [`Parser`](../Parser.md) interface.

      Throws:
      `java.lang.NullPointerException` - There is no value for the \`org.xml.sax.parser' system property.

      `java.lang.ClassNotFoundException` - The SAX parser class was not found (check your CLASSPATH).

      `java.lang.IllegalAccessException` - The SAX parser class was found, but you do not have permission to load it.

      `java.lang.InstantiationException` - The SAX parser class was found but could not be instantiated.

      `java.lang.ClassCastException` - The SAX parser class was found and instantiated, but does not implement org.xml.sax.Parser.

      See Also:
      `makeParser(java.lang.String)`, [`Parser`](../Parser.md)

    <!-- -->

    - #### makeParser

          public static Parser makeParser(java.lang.String className)
                                   throws java.lang.ClassNotFoundException,
                                          java.lang.IllegalAccessException,
                                          java.lang.InstantiationException,
                                          java.lang.ClassCastException

      Deprecated. 
      Create a new SAX parser object using the class name provided.
      The named class must exist and must implement the [`Parser`](../Parser.md) interface.

      Parameters:
      `className` - A string containing the name of the SAX parser class.

      Throws:
      `java.lang.ClassNotFoundException` - The SAX parser class was not found (check your CLASSPATH).

      `java.lang.IllegalAccessException` - The SAX parser class was found, but you do not have permission to load it.

      `java.lang.InstantiationException` - The SAX parser class was found but could not be instantiated.

      `java.lang.ClassCastException` - The SAX parser class was found and instantiated, but does not implement org.xml.sax.Parser.

      See Also:
      `makeParser()`, [`Parser`](../Parser.md)

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

- **[Prev Class](ParserAdapter.md)**
- **[Next Class](XMLFilterImpl.md)**

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
