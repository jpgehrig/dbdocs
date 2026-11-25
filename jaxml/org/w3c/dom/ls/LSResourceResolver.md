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

- **[Prev Class](LSProgressEvent.md)**
- **[Next Class](LSSerializer.md)**

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

**org.w3c.dom.ls**

## **Interface LSResourceResolver**

-

  ------------------------------------------------------------------------

  **
  **

      public interface LSResourceResolver

  **`LSResourceResolver` provides a way for applications to redirect references to external resources.**
  **Applications needing to implement custom handling for external resources can implement this interface and register their implementation by setting the `resourceResolver` attribute of the `LSParser`.**

  **The `LSParser` will then allow the application to intercept any external entities (including the external DTD subset and external parameter entities) before including them.**

  **Many DOM applications will not need to implement this interface, but it will be especially useful for applications that build XML documents from databases or other specialized input sources, or for applications that use URN's.**

  **Note: `LSResourceResolver` is based on the SAX2 \[[SAX](http://www.saxproject.org/)\] `EntityResolver` interface.**

  See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                                                                                                                            |
    |-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LSInput`](LSInput.md) | `resolveResource``(java.lang.String type, java.lang.String namespaceURI, java.lang.String publicId, java.lang.String systemId, java.lang.String baseURI)`<br>Allow the application to resolve external resources. |

<!-- -->

- - ### Method Detail

    - #### resolveResource

          LSInput resolveResource(java.lang.String type,
                                  java.lang.String namespaceURI,
                                  java.lang.String publicId,
                                  java.lang.String systemId,
                                  java.lang.String baseURI)

      Allow the application to resolve external resources.
      The `LSParser` will call this method before opening any external resource except the top-level document entity (including the external DTD subset, external entities referenced within the DTD, and external entities referenced within the document element); the application may request that the `LSParser` resolve the resource itself, that it use an alternative URI, or that it use an entirely different input source.
      Application writers can use this method to redirect external system identifiers to secure and/or local URI's, to look up public identifiers in a catalogue, or to read an entity from a database or other input source (including, for example, a dialog box).
      If the system identifier is a URI, the `LSParser` must resolve it fully before calling this method.
      Parameters:
      `type` - The type of the resource being resolved. For XML \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\] resources (i.e. entities), applications must use the value `"http://www.w3.org/TR/REC-xml"`, for XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , applications must use the value `"http://www.w3.org/2001/XMLSchema"`. Other types of resources are outside the scope of this specification and therefore should recommend an absolute URI in order to use this method.

      `namespaceURI` - The namespace of the resource being resolved, i.e. the namespace of the XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] when resolving XML Schema resources.

      `publicId` - The public identifier of the external entity being referenced, or `null` if no public identifier was supplied or if the resource is not an entity.

      `systemId` - The system identifier, a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\], of the external resource being referenced.

      `baseURI` - The absolute base URI of the resource being parsed, or `null` if there is no base URI.

      Returns:
      A `LSInput` object describing the new input source, or `null` to request that the parser open a regular URI connection to the system identifier.

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

- **[Prev Class](LSProgressEvent.md)**
- **[Next Class](LSSerializer.md)**

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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at <http://www.w3.org/TR/DOM-Level-3-LS>.**
