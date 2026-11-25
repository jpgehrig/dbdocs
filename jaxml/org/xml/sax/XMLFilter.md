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

- **[Prev Class](SAXParseException.md)**
- **[Next Class](XMLReader.md)**

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

**org.xml.sax**

## **Interface XMLFilter**

- **All Superinterfaces:**
  **[XMLReader](XMLReader.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XMLFilterImpl](helpers/XMLFilterImpl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XMLFilter
      extends XMLReader

  **Interface for an XML filter.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **An XML filter is like an XML reader, except that it obtains its events from another XML reader rather than a primary source like an XML document or database. Filters can modify a stream of events as they pass on to the final application.**

  **The XMLFilterImpl helper class provides a convenient base for creating SAX2 filters, by passing on all [`EntityResolver`](EntityResolver.md), [`DTDHandler`](DTDHandler.md), [`ContentHandler`](ContentHandler.md) and [`ErrorHandler`](ErrorHandler.md) events automatically.**

  **Since:**
  **SAX 2.0**

  **See Also:**
  **[`XMLFilterImpl`](helpers/XMLFilterImpl.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                        |
    |-----------------------------|-------------------------------------------------------------------------------|
    | [`XMLReader`](XMLReader.md) | `getParent``()`<br>Get the parent reader.                                     |
    | `void`                      | `setParent``(`[`XMLReader`](XMLReader.md)` parent)`<br>Set the parent reader. |

    - ### Methods inherited from interface org.xml.sax.[XMLReader](XMLReader.md)

      [`getContentHandler`](XMLReader.md)`, `[`getDTDHandler`](XMLReader.md)`, `[`getEntityResolver`](XMLReader.md)`, `[`getErrorHandler`](XMLReader.md)`, `[`getFeature`](XMLReader.md)`, `[`getProperty`](XMLReader.md)`, `[`parse`](XMLReader.md)`, `[`parse`](XMLReader.md)`, `[`setContentHandler`](XMLReader.md)`, `[`setDTDHandler`](XMLReader.md)`, `[`setEntityResolver`](XMLReader.md)`, `[`setErrorHandler`](XMLReader.md)`, `[`setFeature`](XMLReader.md)`, `[`setProperty`](XMLReader.md)

<!-- -->

- - ### Method Detail

    - #### setParent

          void setParent(XMLReader parent)

      Set the parent reader.
      This method allows the application to link the filter to a parent reader (which may be another filter). The argument may not be null.

      Parameters:
      `parent` - The parent reader.

    <!-- -->

    - #### getParent

          XMLReader getParent()

      Get the parent reader.
      This method allows the application to query the parent reader (which may be another filter). It is generally a bad idea to perform any operations on the parent reader directly: they should all pass through this filter.

      Returns:
      The parent filter, or null if none has been set.

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

- **[Prev Class](SAXParseException.md)**
- **[Next Class](XMLReader.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
