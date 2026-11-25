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

- **[Prev Class](XMLException.md)**
- **Next Class**

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

**oracle.xml.util**

## **Class XMLUtil**

- **java.lang.Object**

- - **oracle.xml.util.XMLUtil**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XMLUtil
      extends java.lang.Object

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XMLUtil``()`               |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type         | Method and Description                                                                                                                                      |
    |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `appendRelativeURI``(java.lang.String baseUri, java.lang.String relUri)`                                                                                    |
    | `static java.lang.String` | `encodeURL``(java.lang.String s)`<br>Translates a string into `x-www-form-urlencoded` format.                                                               |
    | `static java.lang.String` | `getJavaEncoding``(java.lang.String enc)`<br>Get Java encoding from IANA encoding                                                                           |
    | `static java.lang.String` | `getLocalName``(java.lang.String qname)`<br>extracts localName part from a qualified name                                                                   |
    | `static java.lang.String` | `getPrefix``(java.lang.String qname)`<br>extracts prefix part from a qualified name                                                                         |
    | `static java.lang.String` | `getRawLocalName``(java.lang.String qname)`<br>extracts localName part from a qualified name without intern()                                               |
    | `static java.lang.String` | `getRawPrefix``(java.lang.String qname)`<br>extracts prefix part from a qualified name without intern()                                                     |
    | `static boolean`          | `isAbsoluteURI``(java.lang.String uri)`                                                                                                                     |
    | `static boolean`          | `isFirstNameChar``(char c)`<br>Deprecated. <br>Use isNameStartChar(int)                                                                                     |
    | `static boolean`          | `isLegalXML10Char``(int cp)`<br>return true if the character is a legal character under XML 1.0                                                             |
    | `static boolean`          | `isNameChar``(char c)`<br>Deprecated. <br>Use isNameChar(int)                                                                                               |
    | `static boolean`          | `isNmtokenChar``(char c)`<br>return true if character can be part of a NMTOKEN, according to ???.                                                           |
    | `static boolean`          | `isWhiteSpace``(char[] ch, int start, int len)`<br>return true if character array is whitespace chars, according to Java.                                   |
    | `static boolean`          | `isWhiteSpaceChar``(char c)`<br>return true if character is whitespace, according to Java.                                                                  |
    | `static char[]`           | `mappingChars``(char one, java.util.HashMap maps)`                                                                                                          |
    | `static java.lang.String` | `nodeTypeToString``(int type)`                                                                                                                              |
    | `static byte[]`           | `parseBase64Binary``(java.lang.String value)`                                                                                                               |
    | `static java.lang.String` | `printBase64Binary``(byte[] val)`                                                                                                                           |
    | `static void`             | `validateName``(java.lang.String name)`<br>Validates an XML Name, with or without a colon                                                                   |
    | `static void`             | `validatePrefix``(java.lang.String prefix)`<br>Validates a prefix in a qualified name.                                                                      |
    | `static void`             | `validateQualifiedName``(java.lang.String qname)`<br>validates qualified name                                                                               |
    | `static void`             | `validateQualifiedName``(java.lang.String uri, java.lang.String qname)`<br>validates qualified name                                                         |
    | `static void`             | `validateQualifiedNameOld``(java.lang.String uri, java.lang.String qname)`<br>validates qualified name using old behavior of setAttributeNS() in XMLElement |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLUtil

          public XMLUtil()

  <!-- -->

  - ### Method Detail

    - #### getJavaEncoding

          public static java.lang.String getJavaEncoding(java.lang.String enc)

      Get Java encoding from IANA encoding
      Parameters:
      `enc` - - string IANA encoding

    <!-- -->

    - #### encodeURL

          public static java.lang.String encodeURL(java.lang.String s)

      Translates a string into `x-www-form-urlencoded` format.
      Parameters:
      `s` - `String` to be translated.

      Returns:
      the translated `String`.

    <!-- -->

    - #### isLegalXML10Char

          public static boolean isLegalXML10Char(int cp)

      return true if the character is a legal character under XML 1.0
      Parameters:
      `cp` - - Unicode code point of the character to check

      Returns:
      true/false

    <!-- -->

    - #### isWhiteSpace

          public static boolean isWhiteSpace(char[] ch,
                                             int start,
                                             int len)

      return true if character array is whitespace chars, according to Java. Warning: This method does not handle supplementary characters (surrogate pairs).
      Parameters:
      `ch` - - char array

      `start` - - start index in the array

      `len` - - number of chars to be checked

      Returns:
      true/false

    <!-- -->

    - #### isWhiteSpaceChar

          public static boolean isWhiteSpaceChar(char c)

      return true if character is whitespace, according to Java. Warning: This method does not handle supplementary characters (surrogate pairs).
      Parameters:
      `c` - - char to be checked

      Returns:
      true/false

    <!-- -->

    - #### isNameChar

          @Deprecated
          public static boolean isNameChar(char c)

      Deprecated. Use isNameChar(int)
      return true if character can be part of a name, according to ???. Warning: This method does not handle supplementary characters (surrogate pairs).
      Parameters:
      `c` - - char to be checked

      Returns:
      true/false

    <!-- -->

    - #### isNmtokenChar

          public static boolean isNmtokenChar(char c)

      return true if character can be part of a NMTOKEN, according to ???. Warning: This method does not handle supplementary characters (surrogate pairs).
      Parameters:
      `c` - - char to be checked

      Returns:
      true/false

    <!-- -->

    - #### isFirstNameChar

          @Deprecated
          public static boolean isFirstNameChar(char c)

      Deprecated. Use isNameStartChar(int)
      return true if character can be part of a name, according to ???. Warning: This method does not handle supplementary characters (surrogate pairs).
      Parameters:
      `c` - - char to be checked

      Returns:
      true/false

    <!-- -->

    - #### validateName

          public static void validateName(java.lang.String name)
                                   throws DOMException

      Validates an XML Name, with or without a colon
      Parameters:
      `name` - - XML name to be checked

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the XML name contains an illegal character.

    <!-- -->

    - #### validateQualifiedName

          public static void validateQualifiedName(java.lang.String uri,
                                                   java.lang.String qname)
                                            throws DOMException

      validates qualified name
      Parameters:
      `uri` - namespace URI against which it is validated

      `qname` - qualified name against which it is validated

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NAMESPACE_ERR: Raised if qname is malformed; or if namespaceURI is null; or if qname has a prefix "xml" and namespaceURI is not http://www.w3c.org/1998/namespace; or if qname or prefix is "xmlns" and namespaceURI is not "http://www.w3c.org/2000/xmlns/"; or if namespaceURI is "http://www.w3c.org/2000/xmlns/" and neither qname, nor its prefix, is "xmlns". INVALID_CHARACTER_ERR: Raised if qname is empty; or if qname contains an illegal character (for an XML name).

    <!-- -->

    - #### validateQualifiedNameOld

          public static void validateQualifiedNameOld(java.lang.String uri,
                                                      java.lang.String qname)
                                               throws DOMException

      validates qualified name using old behavior of setAttributeNS() in XMLElement
      Parameters:
      `uri` - namespace URI against which it is validated

      `qname` - qualified name against which it is validated

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NAMESPACE_ERR: Raised if qname is malformed; NVALID_CHARACTER_ERR: Raised if qname is empty;

    <!-- -->

    - #### validateQualifiedName

          public static void validateQualifiedName(java.lang.String qname)
                                            throws DOMException

      validates qualified name
      Parameters:
      `qname` - qualified name against which it is validated

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NAMESPACE_ERR: Raised if qname is malformed INVALID_CHARACTER_ERR: Raised if qname is empty, or if qname contains an illegal character (for an XML name).

    <!-- -->

    - #### validatePrefix

          public static void validatePrefix(java.lang.String prefix)
                                     throws DOMException

      Validates a prefix in a qualified name.
      Parameters:
      `prefix` - - String value of the prefix in the qualified name

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getPrefix

          public static java.lang.String getPrefix(java.lang.String qname)

      extracts prefix part from a qualified name
      Parameters:
      `qname` - qualified name against which it is validated

      Returns:
      the prefix part extracted from the qualifiedname

    <!-- -->

    - #### getLocalName

          public static java.lang.String getLocalName(java.lang.String qname)

      extracts localName part from a qualified name
      Parameters:
      `qname` - - qualifiedname whose localName part is needed

      Returns:
      the localName part extracted from the qualifiedname

    <!-- -->

    - #### getRawPrefix

          public static java.lang.String getRawPrefix(java.lang.String qname)

      extracts prefix part from a qualified name without intern()
      Parameters:
      `qname` - qualified name against which it is validated

      Returns:
      the prefix part extracted from the qualifiedname

    <!-- -->

    - #### getRawLocalName

          public static java.lang.String getRawLocalName(java.lang.String qname)

      extracts localName part from a qualified name without intern()
      Parameters:
      `qname` - - qualifiedname whose localName part is needed

      Returns:
      the localName part extracted from the qualifiedname

    <!-- -->

    - #### nodeTypeToString

          public static java.lang.String nodeTypeToString(int type)

    <!-- -->

    - #### mappingChars

          public static char[] mappingChars(char one,
                                            java.util.HashMap maps)

    <!-- -->

    - #### isAbsoluteURI

          public static boolean isAbsoluteURI(java.lang.String uri)

    <!-- -->

    - #### appendRelativeURI

          public static java.lang.String appendRelativeURI(java.lang.String baseUri,
                                                           java.lang.String relUri)

    <!-- -->

    - #### parseBase64Binary

          public static byte[] parseBase64Binary(java.lang.String value)

    <!-- -->

    - #### printBase64Binary

          public static java.lang.String printBase64Binary(byte[] val)

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

- **[Prev Class](XMLException.md)**
- **Next Class**

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
