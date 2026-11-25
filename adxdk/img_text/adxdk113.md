XML documents can either be input to XML Parser or generate Java or C++ classes by Java Architecture for XML Binding (JAXB) or C++ Class Generator. The Java application can output XML.

XML Schema Validator can be optionally applied to the XML Parser output.

XML Schema can also be input to XML Schema Validator. The output classes as well as the XML Schema Validator output are input to SAX, or DOM, or XML Compressor. The DOM tree output is input to XSLT processor, which also receives input from an XSL style sheet.

The XSLT processor outputs a transformed XML document.

The compressed XML is another output, coming from the XML Compressor.
