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
- **[Next Class](XMLDiffBeanInfo.md)**

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

**oracle.xml.differ**

## **Class XMLDiff**

- **java.lang.Object**

- - **oracle.xml.differ.XMLDiff**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, java.util.EventListener, [DOMBuilderErrorListener](../async/DOMBuilderErrorListener.md), [DOMBuilderListener](../async/DOMBuilderListener.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLDiff
      extends java.lang.Object
      implements DOMBuilderListener, DOMBuilderErrorListener, java.io.Serializable

  **Defines an interface for comparing two XML files. It enables two XML files to be compared to check for their equivalence. It provides the objects to display the differences, if any, in a graphical format. The differences can also be represented as XSL. The corresponding XSL stylesheet with the differences can be generated as a file or an `XMLDocument` object. The first XML file can be transformed into the second XML file by using the XSL stylesheet generated.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `XMLDiff``()`<br>Constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                          |
    |----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                    | `diff``()`<br>Finds the differences between the two XML files or the two XMLDocument objects                                                                                    |
    | `void`                                       | `generateXSL``(java.io.Writer out)`<br>Generates an XSL file of input filename which represents the differences between the 2 XML files which were set initially.               |
    | [`XMLDocument`](../parser/v2/XMLDocument.md) | `generateXSLDoc``()`<br>Generates an XSL stylesheet as an `XMLDocument` which represents the differences between the 2 XML documents set initially.                             |
    | `void`                                       | `generateXSLFile``(java.lang.String filename)`<br>Generates an XSL file of input filename which represents the differences between the 2 XML files which were set initially.    |
    | `javax.swing.JTextPane`                      | `getDiffPane1``()`<br>Gets the text panel as `JTextPane` object which visually shows the diffs in the first XML file.                                                           |
    | `javax.swing.JTextPane`                      | `getDiffPane2``()`<br>Gets the text panel as `JTextPane` object which visually shows the diffs in the second XML file or document                                               |
    | [`XMLDocument`](../parser/v2/XMLDocument.md) | `getDocument1``()`<br>Gets the document root as an `XMLDocument` object of the first XML tree                                                                                   |
    | [`XMLDocument`](../parser/v2/XMLDocument.md) | `getDocument2``()`<br>Gets the document root as an `XMLDocument` object of the second XML tree                                                                                  |
    | `void`                                       | `printDiffTree``(int tree, java.io.BufferedWriter out)`<br>Prints the diff tree which contains the node names and values which have been identified as diffs by the algorithm.  |
    | `void`                                       | `setDelWSBeforeDeletes``(boolean val)`<br>Set option to remove whitespaces-only before a deleted node.                                                                          |
    | `void`                                       | `setDocuments``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` doc1, `[`XMLDocument`](../parser/v2/XMLDocument.md)` doc2)`<br>Sets the XML documents which need to be compared. |
    | `void`                                       | `setFiles``(java.io.File file1, java.io.File file2)`<br>Sets the XML files which need to be compared.                                                                           |
    | `void`                                       | `setIndentIncr``(int spaces)`<br>Sets the indentation for the XSL generation.                                                                                                   |
    | `void`                                       | `setInput1``(java.io.File file1)`<br>Sets the first XML file which need to be compared.                                                                                         |
    | `void`                                       | `setInput1``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` inp1)`<br>Sets the first XML data source which need to be compared.                                         |
    | `void`                                       | `setInput1``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` doc1)`<br>Sets the first XML document which need to be compared.                                                    |
    | `void`                                       | `setInput2``(java.io.File file2)`<br>Sets the second XML file which need to be compared.                                                                                        |
    | `void`                                       | `setInput2``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` inp2)`<br>Sets the second XML data source which need to be compared.                                        |
    | `void`                                       | `setInput2``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` doc2)`<br>Sets the second XML document which need to be compared.                                                   |
    | `void`                                       | `setNewNodeIndentIncr``(int spaces)`<br>Sets the indentation for the XSL generation.                                                                                            |
    | `void`                                       | `setNoMoves``()`<br>Assume that there are no moves to be detected by the diff algorithm.                                                                                        |
    | `void`                                       | `setUrl1``(java.lang.String url1)`<br>Sets the first XML url which need to be compared.                                                                                         |
    | `void`                                       | `setUrl2``(java.lang.String url2)`<br>Sets the second XML url which need to be compared.                                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.xml.async.[DOMBuilderListener](../async/DOMBuilderListener.md)

      [`domBuilderError`](../async/DOMBuilderListener.md)`, `[`domBuilderOver`](../async/DOMBuilderListener.md)`, `[`domBuilderStarted`](../async/DOMBuilderListener.md)

    <!-- -->

    - ### Methods inherited from interface oracle.xml.async.[DOMBuilderErrorListener](../async/DOMBuilderErrorListener.md)

      [`domBuilderErrorCalled`](../async/DOMBuilderErrorListener.md)

<!-- -->

- - ### Constructor Detail

    - #### XMLDiff

          public XMLDiff()

      Constructor

  <!-- -->

  - ### Method Detail

    - #### setFiles

          public void setFiles(java.io.File file1,
                               java.io.File file2)
                        throws java.io.IOException,
                               XMLParseException,
                               SAXException,
                               java.lang.InterruptedException

      Sets the XML files which need to be compared. Both files are parsed into DOM trees for comparision. This is faster than calling setInput1() and setInput2()
      Parameters:
      `file1` - first XML file

      `file2` - second XML file

      Throws:
      `java.io.IOException` - thrown when an I/O error occurs

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

      `java.lang.InterruptedException` - if a sleeping thread is interrupted

    <!-- -->

    - #### setDocuments

          public void setDocuments(XMLDocument doc1,
                                   XMLDocument doc2)

      Sets the XML documents which need to be compared.
      Parameters:
      `doc1` - first XML document

      `doc2` - second XML document

    <!-- -->

    - #### setInput1

          public void setInput1(java.io.File file1)
                         throws java.io.IOException,
                                XMLParseException,
                                SAXException,
                                java.lang.InterruptedException

      Sets the first XML file which need to be compared. The input file is parsed into a DOM tree for comparision.
      Parameters:
      `file1` - first XML file

      Throws:
      `java.io.IOException` - thrown when an I/O error occurs

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

      `java.lang.InterruptedException` - if a sleeping thread is interrupted

    <!-- -->

    - #### setInput2

          public void setInput2(java.io.File file2)
                         throws java.io.IOException,
                                XMLParseException,
                                SAXException,
                                java.lang.InterruptedException

      Sets the second XML file which need to be compared. The input file is parsed into a DOM tree for comparision.
      Parameters:
      `file2` - second XML file

      Throws:
      `java.io.IOException` - thrown when an I/O error occurs

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

      `java.lang.InterruptedException` - if a sleeping thread is interrupted

    <!-- -->

    - #### setInput1

          public void setInput1(XMLDocument doc1)

      Sets the first XML document which need to be compared.
      Parameters:
      `doc1` - first XML document

    <!-- -->

    - #### setInput2

          public void setInput2(XMLDocument doc2)

      Sets the second XML document which need to be compared.
      Parameters:
      `doc2` - second XML document

    <!-- -->

    - #### setInput1

          public void setInput1(InputSource inp1)
                         throws java.io.IOException,
                                XMLParseException,
                                SAXException

      Sets the first XML data source which need to be compared.
      Parameters:
      `inp1` - XML data source as `org.xml.sax.InputSouce`

      Throws:
      `java.io.IOException` - thrown when an I/O error occurs

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

    <!-- -->

    - #### setInput2

          public void setInput2(InputSource inp2)
                         throws java.io.IOException,
                                XMLParseException,
                                SAXException

      Sets the second XML data source which need to be compared.
      Parameters:
      `inp2` - XML data source as `org.xml.sax.InputSouce`

      Throws:
      `java.io.IOException` - thrown when an I/O error occurs

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

    <!-- -->

    - #### setUrl1

          public void setUrl1(java.lang.String url1)
                       throws java.io.IOException,
                              XMLParseException,
                              SAXException,
                              java.lang.InterruptedException

      Sets the first XML url which need to be compared. The input xml url is parsed into a DOM tree for comparision.
      Parameters:
      `url1` - first XML url

      Throws:
      `java.io.IOException` - thrown when an I/O error occurs

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

      `java.lang.InterruptedException` - if a sleeping thread is interrupted

    <!-- -->

    - #### setUrl2

          public void setUrl2(java.lang.String url2)
                       throws java.io.IOException,
                              XMLParseException,
                              SAXException,
                              java.lang.InterruptedException

      Sets the second XML url which need to be compared. The input xml url is parsed into a DOM tree for comparision.
      Parameters:
      `url2` - second XML url

      Throws:
      `java.io.IOException` - thrown when an I/O error occurs

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

      `java.lang.InterruptedException` - if a sleeping thread is interrupted

    <!-- -->

    - #### getDocument1

          public XMLDocument getDocument1()

      Gets the document root as an `XMLDocument` object of the first XML tree
      Returns:
      the document root of the first XML file

    <!-- -->

    - #### getDocument2

          public XMLDocument getDocument2()

      Gets the document root as an `XMLDocument` object of the second XML tree
      Returns:
      the document root of the second XML file

    <!-- -->

    - #### diff

          public boolean diff()
                       throws java.lang.NullPointerException

      Finds the differences between the two XML files or the two XMLDocument objects
      Returns:
      false if the XML files or docs are same, true if they are different

      Throws:
      `java.lang.NullPointerException` - occurs when xml files were not parsed successfully and this function was called. Or if xml documents have not been set.

    <!-- -->

    - #### getDiffPane1

          public javax.swing.JTextPane getDiffPane1()

      Gets the text panel as `JTextPane` object which visually shows the diffs in the first XML file.
      Returns:
      visual text panel showing diffs in first XML file

    <!-- -->

    - #### getDiffPane2

          public javax.swing.JTextPane getDiffPane2()

      Gets the text panel as `JTextPane` object which visually shows the diffs in the second XML file or document
      Returns:
      visual text panel showing diffs in second XML file

    <!-- -->

    - #### setIndentIncr

          public void setIndentIncr(int spaces)

      Sets the indentation for the XSL generation. This should be called before the generateXSLFile() or generateXSLDoc(). The indentation will be applied to all attributes only. For indenting newly inserted nodes besides attributes see setNewNodeIndentIncr()
      Parameters:
      `spaces` - indentation increment in number of spaces for attributes

    <!-- -->

    - #### setNewNodeIndentIncr

          public void setNewNodeIndentIncr(int spaces)

      Sets the indentation for the XSL generation. This should be called before the generateXSLFile() or generateXSLDoc(). The indentation will be applied to all newly inserted nodes only (except attributes). For attributes indentation support see setIndentIncr()
      Parameters:
      `spaces` - indentation increment in number of spaces for new nodes

    <!-- -->

    - #### setDelWSBeforeDeletes

          public void setDelWSBeforeDeletes(boolean val)

      Set option to remove whitespaces-only before a deleted node. This should be called before calling generateXSLFile() or generateXSLDoc(). By default whitespaces before seleted nodes are \*not\* deleted.
      Parameters:
      `val` - true (deleted whitespace before deletes), false(do not delete whitespace before deletes).

    <!-- -->

    - #### generateXSLFile

          public void generateXSLFile(java.lang.String filename)
                               throws java.io.IOException

      Generates an XSL file of input filename which represents the differences between the 2 XML files which were set initially. If the input filename is null this function will do nothing. The first XML file can be transformed into the second XML file using the XSL stylesheet generated. If the XML files were the same then the XSL generated will transform the first XML file into the second XML file, where the first and second files will equivalent.
      Parameters:
      `filename` - output XSL file name

      Throws:
      `java.io.IOException` - could occur if the xsl file was not created successfully

    <!-- -->

    - #### generateXSLDoc

          public XMLDocument generateXSLDoc()
                                     throws java.io.FileNotFoundException,
                                            SAXException,
                                            XMLParseException,
                                            java.io.IOException

      Generates an XSL stylesheet as an `XMLDocument` which represents the differences between the 2 XML documents set initially. The first XML file can be transformed into the second XML file using the XSL stylesheet generated. If the XML files were the same then the XSL generated will transform the first XML file into the second XML file, where the first and second files will equivalent.
      Returns:
      XSL stylesheet as an XML document

      Throws:
      `java.io.IOException` - could occur if the xsl file was not created successfully

      `java.io.FileNotFoundException` - if xsl file generated could not be found

      [`SAXException`](../../../org/xml/sax/SAXException.md) - caused when parsing xml document

      [`XMLParseException`](../parser/v2/XMLParseException.md) - caused when parsing xml document

    <!-- -->

    - #### generateXSL

          public void generateXSL(java.io.Writer out)
                           throws java.io.IOException,
                                  java.lang.NullPointerException

      Generates an XSL file of input filename which represents the differences between the 2 XML files which were set initially. The first XML file can be transformed into the second XML file using the XSL stylesheet generated. If the XML files were the same then the XSL generated will transform the first XML file into the second XML file, where the first and second files will equivalent.
      Parameters:
      `out` - Generated XSLT will be written to 'out'.

      Throws:
      `java.io.IOException` - could occur if the xsl file was not created successfully

      `java.lang.NullPointerException` - could occur if input file name is null

    <!-- -->

    - #### printDiffTree

          public void printDiffTree(int tree,
                                    java.io.BufferedWriter out)
                             throws java.io.IOException

      Prints the diff tree which contains the node names and values which have been identified as diffs by the algorithm. Useful for debugging.
      Parameters:
      `tree` - tree to print, i.e. one or two

      `out` - containing the printed diff tree

      Throws:
      `java.io.IOException` - could occur if the xsl file was not created successfully

    <!-- -->

    - #### setNoMoves

          public void setNoMoves()

      Assume that there are no moves to be detected by the diff algorithm. This function should be called before the diff() function. It will result in a performance gain.

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
- **[Next Class](XMLDiffBeanInfo.md)**

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
