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

- **Prev Class**
- **[Next Class](XMLCompressBeanInfo.md)**

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

**oracle.xml.xmlcomp**

## **Class XMLCompress**

- **java.lang.Object**

- - **oracle.xml.xmlcomp.XMLCompress**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XMLCompress
      extends java.lang.Object
      implements java.io.Serializable

  **This bean class is a simple encapsulation of the XML Compression functionality. The functionalities that are supported in this class are essentially Compression of the internal DOM tree obtained via a DOMParser, Compression of the SAX events thrown by the SAX Parser, Uncompression of the serialized XML data, returning an XMLDocument object. The input for compression can be from an InputStream, a java String, a database CLOB object, an XMLType object. In all cases the outputStream has to be set before hand so that the compressed data is written to it. The case where input data is unparsed the parsing for it is done with no validation.To use different parsing options parse the document before inputting and then pass the XMLDocument object to the compressor bean. The compression factor is a rough value based on the file size of the input XML file and the compressed file. The limitation of the compression factor method is it can only be used when the compression is done using the "java.io.File" objects as parameters.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                  |
    |------------------------------------------------------------------------------|
    | `XMLCompress``()`<br>Constructs this object by setting the various parameter |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                                                   |
    |----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                       | `DOMCompress``()`<br>Compress the XML Data set in the Text InputStream of this object and writes the compressed data into the binary outputstream                                                        |
    | `void`                                       | `DOMCompress``(oracle.sql.CLOB clob)`<br>Compress the xml data contained in the CLOB object and writes the compressed data into the binary outputstream of this object                                   |
    | `void`                                       | `DOMCompress``(java.io.File inpTxtfile, java.io.File outpBinfile)`<br>Compress the xml data contained in the inpTxtfile and writes the compressed ouput to outpBinfile                                   |
    | `void`                                       | `DOMCompress``(java.io.InputStream is)`<br>Compress the XML Data set in the Text InputStream and writes the compressed data into the binary outputstream                                                 |
    | `void`                                       | `DOMCompress``(java.lang.String xmldoc)`<br>Compress the xml data contained in the java String and writes the compressed data into the binary outputstream of this object                                |
    | `void`                                       | `DOMCompress``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` xmldoc)`<br>Compress the XMLDocument object and writes the compressed data into the binary outputstream of this object                     |
    | `void`                                       | `DOMCompress``(`[`XMLType`](../../xdb/XMLType.md)` xmldoc)`<br>Compress the xml data contained in the database XMLType object and writes the compressed data into the binary outputstream of this object |
    | `void`                                       | `DOMExpand``()`<br>Uncompresses the binary inputstream and populates the XMLDocument of this object.                                                                                                     |
    | `void`                                       | `DOMExpand``(oracle.sql.BLOB blob)`<br>Uncompresses the BLOB parameter and populates the XMLDocument of this object.                                                                                     |
    | `void`                                       | `DOMExpand``(java.io.File inpBinfile, java.io.File outpTxtfile)`<br>UnCompress the data contained in the inpBinfile and writes the compressed ouput to outpTxtfile                                       |
    | `void`                                       | `DOMExpand``(java.io.InputStream inpstr)`<br>Uncompresses the binary inputstream parameter and populates the XMLDocument of this object.                                                                 |
    | `float`                                      | `getCompPercent``()`<br>Return the compression factor.                                                                                                                                                   |
    | [`XMLDocument`](../parser/v2/XMLDocument.md) | `getXMLDocument``()`<br>Returns the XMLDocument object obtained from compressed data                                                                                                                     |
    | `void`                                       | `SAXCompress``(java.io.File inpTxtfile, java.io.File outpBinfile)`<br>Compress the xml data contained in the inpTxtfile and writes the compressed ouput to outpBinfile                                   |
    | `void`                                       | `SAXCompress``(java.io.InputStream xmltext)`<br>Compress the XML data in the Inputstream to a binary stream which contains the SAX events                                                                |
    | `void`                                       | `SAXCompress``(java.lang.String xmltext)`<br>Compress the XML data in the String to a binary stream which contains the SAX events                                                                        |
    | `void`                                       | `setBinInputStream``(java.io.InputStream binstr)`<br>Sets the Binary inputstream to write the compressed data                                                                                            |
    | `void`                                       | `setBinOutputStream``(java.io.OutputStream binstr)`<br>Sets the Binary outputstream to write the compressed data                                                                                         |
    | `void`                                       | `setXMLDocument``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` setDoc)`<br>Sets the XMLDocument object that needs to be Compressed                                                                     |
    | `void`                                       | `setXmlTextInputStream``(java.io.InputStream txtstr)`<br>Sets the Text Inputstream to compress the data                                                                                                  |
    | `void`                                       | `setXmlTextOutputStream``(java.io.OutputStream txtstr)`<br>Sets the Text outputstream to write the XML data                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLCompress

          public XMLCompress()

      Constructs this object by setting the various parameter

  <!-- -->

  - ### Method Detail

    - #### setBinOutputStream

          public void setBinOutputStream(java.io.OutputStream binstr)

      Sets the Binary outputstream to write the compressed data
      Parameters:
      `binstr` - - Java OutputStream

    <!-- -->

    - #### setBinInputStream

          public void setBinInputStream(java.io.InputStream binstr)

      Sets the Binary inputstream to write the compressed data
      Parameters:
      `binstr` - - Java InpputStream

    <!-- -->

    - #### setXmlTextOutputStream

          public void setXmlTextOutputStream(java.io.OutputStream txtstr)

      Sets the Text outputstream to write the XML data
      Parameters:
      `txtstr` - - Java outputStream

    <!-- -->

    - #### setXmlTextInputStream

          public void setXmlTextInputStream(java.io.InputStream txtstr)

      Sets the Text Inputstream to compress the data
      Parameters:
      `txtstr` - - Java InputStream

    <!-- -->

    - #### getXMLDocument

          public XMLDocument getXMLDocument()

      Returns the XMLDocument object obtained from compressed data
      Returns:
      XMLDocument object

    <!-- -->

    - #### setXMLDocument

          public void setXMLDocument(XMLDocument setDoc)

      Sets the XMLDocument object that needs to be Compressed
      Parameters:
      `setDoc` - - XMLDocument object

    <!-- -->

    - #### DOMCompress

          public void DOMCompress()
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Compress the XML Data set in the Text InputStream of this object and writes the compressed data into the binary outputstream
      Throws:
      `XMLParseException,` - SAXException, IOException

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

    <!-- -->

    - #### DOMCompress

          public void DOMCompress(java.io.InputStream is)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Compress the XML Data set in the Text InputStream and writes the compressed data into the binary outputstream
      Parameters:
      `is` - - Java InputStream containing the XML Data

      Throws:
      `XMLParseException,` - SAXException, IOException

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

    <!-- -->

    - #### DOMCompress

          public void DOMCompress(XMLDocument xmldoc)
                           throws java.io.IOException

      Compress the XMLDocument object and writes the compressed data into the binary outputstream of this object
      Parameters:
      `xmldoc` - - XMLDocument object

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### DOMCompress

          public void DOMCompress(java.lang.String xmldoc)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Compress the xml data contained in the java String and writes the compressed data into the binary outputstream of this object
      Parameters:
      `xmldoc` - - Java string

      Throws:
      `java.io.IOException`

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### DOMCompress

          public void DOMCompress(oracle.sql.CLOB clob)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException,
                                  java.sql.SQLException

      Compress the xml data contained in the CLOB object and writes the compressed data into the binary outputstream of this object
      Parameters:
      `clob` - - Java stringoracle.sql.CLOB

      Throws:
      `java.io.IOException`

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### DOMCompress

          public void DOMCompress(XMLType xmldoc)
                           throws java.io.IOException,
                                  XMLParseException,
                                  SAXException,
                                  java.sql.SQLException

      Compress the xml data contained in the database XMLType object and writes the compressed data into the binary outputstream of this object
      Parameters:
      `xmldoc` - - oracle.xdb.XMLType

      Throws:
      `IOException,XMLParseException,SAXException,SQLException`

      `java.io.IOException`

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### DOMCompress

          public void DOMCompress(java.io.File inpTxtfile,
                                  java.io.File outpBinfile)
                           throws java.io.IOException,
                                  XMLParseException,
                                  SAXException,
                                  java.sql.SQLException

      Compress the xml data contained in the inpTxtfile and writes the compressed ouput to outpBinfile
      Parameters:
      `inpTxtfile` - - java file inpTxtfile

      `outpBinfile` - - java file outpBinfile

      Throws:
      `IOException,XMLParseException,SAXException,SQLException`

      `java.io.IOException`

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### DOMExpand

          public void DOMExpand()
                         throws java.io.IOException,
                                java.io.EOFException,
                                java.lang.ClassNotFoundException

      Uncompresses the binary inputstream and populates the XMLDocument of this object.
      Throws:
      `IOException,EOFException,ClassNotFoundException`

      `java.io.IOException`

      `java.io.EOFException`

      `java.lang.ClassNotFoundException`

    <!-- -->

    - #### DOMExpand

          public void DOMExpand(java.io.InputStream inpstr)
                         throws java.io.IOException,
                                java.io.EOFException,
                                java.lang.ClassNotFoundException

      Uncompresses the binary inputstream parameter and populates the XMLDocument of this object.
      Parameters:
      `inpstr` - - java InputStream

      Throws:
      `IOException,EOFException,ClassNotFoundException`

      `java.io.IOException`

      `java.io.EOFException`

      `java.lang.ClassNotFoundException`

    <!-- -->

    - #### DOMExpand

          public void DOMExpand(oracle.sql.BLOB blob)
                         throws java.sql.SQLException,
                                java.io.IOException,
                                java.io.EOFException,
                                java.lang.ClassNotFoundException

      Uncompresses the BLOB parameter and populates the XMLDocument of this object.
      Parameters:
      `blob` - - oracle.sql.BLOB

      Throws:
      `SQLException,IOException,EOFException,ClassNotFoundException`

      `java.sql.SQLException`

      `java.io.IOException`

      `java.io.EOFException`

      `java.lang.ClassNotFoundException`

    <!-- -->

    - #### DOMExpand

          public void DOMExpand(java.io.File inpBinfile,
                                java.io.File outpTxtfile)
                         throws java.io.IOException,
                                XMLParseException,
                                java.sql.SQLException,
                                java.lang.ClassNotFoundException

      UnCompress the data contained in the inpBinfile and writes the compressed ouput to outpTxtfile
      Parameters:
      `inpBinfile` - - java file inpBinfile

      `outpTxtfile` - - java file outpTxtfile

      Throws:
      `IOException,XMLParseException,SAXException,SQLException`

      `java.io.IOException`

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      `java.sql.SQLException`

      `java.lang.ClassNotFoundException`

    <!-- -->

    - #### SAXCompress

          public void SAXCompress(java.io.InputStream xmltext)
                           throws SAXException,
                                  XMLParseException,
                                  java.io.IOException

      Compress the XML data in the Inputstream to a binary stream which contains the SAX events
      Parameters:
      `xmltext` - - java InputStream

      Throws:
      `SAXException,XMLParseException,IOException`

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      `java.io.IOException`

    <!-- -->

    - #### SAXCompress

          public void SAXCompress(java.io.File inpTxtfile,
                                  java.io.File outpBinfile)
                           throws java.io.IOException,
                                  XMLParseException,
                                  SAXException

      Compress the xml data contained in the inpTxtfile and writes the compressed ouput to outpBinfile
      Parameters:
      `inpTxtfile` - - java file inpTxtfile

      `outpBinfile` - - java file outpBinfile

      Throws:
      `IOException,XMLParseException,SAXException,SQLException`

      `java.io.IOException`

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### SAXCompress

          public void SAXCompress(java.lang.String xmltext)
                           throws SAXException,
                                  XMLParseException,
                                  java.io.IOException

      Compress the XML data in the String to a binary stream which contains the SAX events
      Parameters:
      `xmltext` - - java InputStream

      Throws:
      `SAXException,XMLParseException,IOException`

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      [`XMLParseException`](../parser/v2/XMLParseException.md)

      `java.io.IOException`

    <!-- -->

    - #### getCompPercent

          public float getCompPercent()

      Return the compression factor. This can be used only when the compression is done using Java File objects as Inputs
      Returns:
      float , compression factor

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

- **Prev Class**
- **[Next Class](XMLCompressBeanInfo.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
