The figure illustrates the XSLT Processor for XMLType (DBMS_XSLPROCESSOR) calling sequence:

- An XSLT Processor can be constructed using the method newProcessor().

- To build an XSL stylesheet from a DOM document, use method newStylesheet().

- Optionally, you can set parameters to the XSL stylesheet using the call setParams.

- XSLT processing can then be carried out with the call processXSL using the processor and stylesheet.

- Pass the XML document to be transformed to the call processXSL.

- The resulting DOMDocumentFragment interface can be operated on using the PL/SQL DOM API for XMLType.
